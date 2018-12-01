---
layout: post
title:  "sidekiq & restclient"
date:   2016-07-13 14:50:39  
categories: outer
---

```ruby

class MyWorker
  include Sidekiq::Worker
  sidekiq_options :retry => 1

  sidekiq_retries_exhausted do |perform_msg|
    Sidekiq.logger.warn "Failed #{perform_msg['class']} with #{perform_msg['args']}: #{perform_msg['error_message']}"
    MyWorker.new.deal_result('bad', perform_msg['args'].last)
  end

  def perform(url, ps, opts = {})    
    raise "manually error" if text == 'showerror'
    RestClient::Request.execute(:method => :post, :url => url, :payload => ps.to_json, :headers => {"Content-Type" => "application/json"}, :timeout => 1, :max_redirects => 1) do |resp, request, result, &block|
      if [301, 302, 307].include?(resp.code)
        resp.follow_redirection(request, result, &block)
      end            
    end

    deal_result('good', opts)
  end

  def deal_result(flag, opts)
    #do_good if flag == 'good'
    #do_bad  if flag == 'bad'
  end
end

```
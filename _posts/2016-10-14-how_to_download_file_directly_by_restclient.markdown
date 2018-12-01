---
layout: post
title:  "不把文件流载到内存，怎样直接通过RestClient下载一个大文件"
date:   2016-10-14 18:14:39  

categories: rails
---

不把文件流载到内存，怎样通过RestClient直接下载并保持一个大文件

```ruby
require 'rest-client'
File.open('/tmp/README.md', 'w') {|f|
  block = proc { |response|
    response.read_body do |chunk|
      #puts "Working on response"
      f.write chunk
    end
  }

  RestClient::Request.new(method: :get, url: 'https://raw.githubusercontent.com/rails/rails/master/README.md', block_response: block).execute  
}

```

不过这个办法，　还有编码问题
original from [here](https://github.com/rest-client/rest-client/issues/534)

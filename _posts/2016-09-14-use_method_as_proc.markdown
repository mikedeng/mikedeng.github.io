---
layout: post
title:  "use method as proc"
date:   2016-09-14 22:00:39  

categories: ruby
---

如何把 Ruby 方法当作 Block 使用

```ruby

	# sample 01
	plus_one = 1.method(:+)
	plus_one.call(1)             # => 2


	# sample 02
	printer = method(:puts)
	[1, 2, 3].each(&printer)     # => puts 1, 2, 3 one by one


	# sample 03
	def some_method(logger_strategy = method(:puts))
	  # do something
	  logger_strategy.call  "xxx info"
	end


	# sample 04
	def do_some_with_rescue(err_strategy = method(:raise))
	  # raise something	  
	rescue
	  err_strategy.call
	end

	# 1. directly by raise error
	do_some_with_rescue

	# 2. rescue by yourself
	error_handler = Proc.new { puts 'Yahoo, I rescued it!' }
	do_some_with_rescue(error_handler)

```
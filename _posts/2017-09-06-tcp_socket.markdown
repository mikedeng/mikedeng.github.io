---
layout: post
title:  "TCP socket实现NOSQL"
date:   2017-09-04 22:30:39

categories: db
---


## 问题： 如何使用TCP server实现NoSQL

+ server side：

	```ruby
		require 'socket'
		module CloudHash
			class Server
				def initialize(port)
					@server = TCPServer.new(port)
					puts "Listening on port #{@server.local_address.ip_port}"
					@storage = {}
				end

				def start
					Socket.accept_loop(@server) do |connection|
						handle(connection)
						connection.close
					end
				end

				def handle(connection)
					request = connection.read
					connection.write process(request)
				end

				def process(request)
					command, key, value = request.split
					case command.upcase
					when 'GET'
						@storage[key]
					when 'SET'
						@storage[key] = value
					end
				end
			end
		end

		server = CloudHash::Server.new(4481)
		server.start
	```

+ client side：
	```ruby

		require 'socket'
		module CloudHash
			class Client
				class << self
					attr_accessor :host, :port
				end

				def self.get(key)
					request "GET #{key}"
				end

				def self.set(key, value)
					request "SET #{key} #{value}"
				end

				def self.request(string)
					@client = TCPSocket.new(host, port)
					@client.write(string)
					@client.close_write
					@client.read
				end
			end
		end

		CloudHash::Client.host = "localhost"
		CloudHash::Client.port = 4481
		CloudHash::Client.set "president", "xijingping"
		puts CloudHash::Client.get "president"
	```
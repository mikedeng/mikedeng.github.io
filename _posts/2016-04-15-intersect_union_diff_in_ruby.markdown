---
layout: post
title:  "intersect & union & diff  in ruby"
date:   2016-04-15 17:08:39  
categories: rails
---

```ruby
x = [1, 1, 2, 4]
y = [1, 2, 2, 2]

# intersection
x & y            # => [1, 2]

# union
x | y            # => [1, 2, 4]

# difference
x - y            # => [4]

```

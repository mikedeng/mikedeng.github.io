---
layout: post
title:  "插入排序"
date:   2016-04-15 17:08:39  
categories: rails
---

```ruby
def insertion(arr)
  arr = arr.dup
  n = arr.length

  (1...n).each do |i|
    i.downto(1) do |j|
      arr[j], arr[j-1] = arr[j-1], arr[j] if arr[j] < arr[j-1]
    end
  end
  arr
end

arr = [1, 47, 4, 43, 52, 36, 35, 51, 412, 33, 45, 66, 564]
arr2 = insertion(arr)
puts arr2.join(', ')

```

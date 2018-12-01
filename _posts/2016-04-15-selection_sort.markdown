---
layout: post
title:  "选择排序"
date:   2016-04-15 17:08:39  
categories: rails
---

```ruby

def selection(arr)
    arr = arr.dup
    n = arr.length
    (0...n).each do |i|
        min = i

        ((i + 1)...n).each do |j|
            min = j if arr[j] < arr[min]
        end
        arr[i], arr[min] = arr[min], arr[i]
    end
    arr
end

arr  = [1, 4, 3, 2, 5, 2]
arr2 = selection(arr)
puts arr2.join(',')

```

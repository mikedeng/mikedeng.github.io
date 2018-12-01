---
layout: post
title:  "希尔排序"
date:   2016-04-15 17:08:39  
categories: args
---

```ruby

def shell(arr)
    arr = arr.dup
    n   = arr.length
    h   = 1

    while h < (n / 3)
        h = 3 * h + 1
    end

    while h >= 1
        (h...n).each do |i|
            i.step(h, -h) do |j|
                m = j - h
                if arr[j] < arr[m]
                    arr[j], arr[m] = arr[m], arr[j]
                    break
                end
                puts ''
            end
            puts ''
        end
        h = h / 3
    end
    arr
end

```

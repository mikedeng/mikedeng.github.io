---
layout: post
title:  "dedupe model"
date:   2016-04-15 17:08:39  
categories: rails
---

```ruby
def self.dedupe
  grouped = all.group_by{|model| [model.customer_id, model.agent_id] }
  grouped.values.each do |duplicates|
    first_one = duplicates.shift
    duplicates.each{|double| double.destroy}
  end
end
```

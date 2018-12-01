---
layout: post
title:  "enum field 怎样保存nil 值"
date:   2016-10-12 18:14:39  

categories: rails
---

我只是想在 `enum` 字段保存一个 `nil` 值,  居然报错 **enum is not valid industry**

Env:

  > Rails version = 4.0.13


migration

```ruby
  create_table :model_table do |t|
     t.industry :integer
  end

```

model

```ruby
  class ModelName < ActiveRecord::Base
    INDUSTRY = {"online_travel" => 100 ,"entertainment" => 110 ,"other" => 120}
    enum industry: INDUSTRY
  end

```


执行的 action

```ruby
　def create
    model = ModelName.new
    model.industry = nil
  end

```
**居然报错 enum is not valid industry**

查了文档 `enum` 方法, 居然没有 allow_blank: true 之类的设置.

官方给的best practice 是加一个 default: 0, [here](http://edgeapi.rubyonrails.org/classes/ActiveRecord/Enum.html).
可是之前同事发布时, mysql执行default时间太长的引发了故障，不敢用这个。


 意淫了一把，把 model 弄成这样：

**solution:**

model

```ruby
  class ModelName < ActiveRecord::Base
    INDUSTRY = {"online_travel" => 100 ,"entertainment" => 110 ,"other" => 120,  '' => nil}
    enum industry: INDUSTRY
  end

```

设置 `model.industry = nil`，竟然可以!!

action

```ruby
  model = ModelName.new
  model.industry = ''   # good
  model.industry = nil  # good
```

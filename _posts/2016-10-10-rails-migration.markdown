---
layout: post
title:  "rails migration"
date:   2016-10-10 18:14:39  

categories: ruby
---

```bash

	 #退回两次 migration
	rake db:rollback STEP=2

	# 退回特定的 migration
	rake db:migrate:down VERSION=20161010095310

```

---
layout: post
title:  "bash复制文件"
date:   2016-04-15 17:08:39  
categories: linux
---

```bash
#!/bin/bash
DEST="../other_folder"

files="app/file1.rb
app/file2.rb"

for file in $files; do
  echo "cp -f $file $DEST/$file"
  cp -f $file $DEST/$file
done

```

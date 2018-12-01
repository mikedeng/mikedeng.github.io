---
layout: post
title:  "building automation"
date:   2018-02-19 18:01:39

categories: frontend
---

## features
    + compile and watch sass
    + live-server
    + npm-run-all
    + compile with node-sass
    + concat style file
    + prefix with autoprefixer
    + compress with node-sass

```json
{
    "scripts": {
    "watch:sass": "node-sass scss/main.scss css/style.css -w",
    "devserver": "live-server",
    "start": "npm-run-all --parallel devserver watch:sass",
    "compile:sass": "node-sass scss/main.scss css/style.comp.css",
    "concat:sass": "concat -o css/style.concat.css css/icon-font.css css/style.comp.css",
    "prefix:css": "postcss --use autoprefixer -b 'last 10 versions' css/style.concat.css -o css/style.prefix.css",
    "compress:css": "node-sass css/style.prefix.css css/style.css --output-style compressed",
    "build:css": "npm-run-all compile:sass concat:sass prefix:css compress:css"
    },
    "devDependencies": {
      "autoprefixer": "^8.0.0",
      "concat": "^1.0.3",
      "live-server": "^1.2.0",
      "node-sass": "^4.7.2",
      "npm-run-all": "^4.1.2",
      "postcss-cli": "^5.0.0"
    }
}
```
---
layout: post
title:  "Advanced linear-gradient"
date:   2018-02-17 23:30:39

categories: frontend
---


## Advanced linear-gradient
```html
    <div class="book">
        <div class="book__form">
        </div>
    </div>
```

## Advanced linear-gradient

```scss
    .book {
        background-image: linear-gradient(105deg,
                            rgba($color-white, .9) 0%,
                            rgba($color-white, .9) 50%,
                            transparent 50%
                            ),
                          url(../img/nat-10.jpg);
        background-size: cover;
        height         : 50rem;

        &__form {
            width  : 50%;
            padding: 6rem;
        }
    }
```
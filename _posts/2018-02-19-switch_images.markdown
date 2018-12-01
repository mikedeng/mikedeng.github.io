---
layout: post
title:  "Switching images in different ways"
date:   2018-02-19 14:01:39

categories: frontend
---

```html
<!-- resolution direction -->
<img srcset="img/nat-1.jpg 300w, img/nat-1-large.jpg 100w"
    sizes="(max-width: 56.25em) 20vw, (max-width: 37.5em) 30vw, 300px"
    alt="Photo 1"
    class="composition__photo composition__photo--p1">
```


```html
<!-- Art direction:  -->
<picture class="footer__logo">
    <source srcset="img/logo-green-small-1x.png 1x, img/logo-green-small-2x.png 2x" media="(max-width: 37.5em)">
    <img srcset="img/logo-green-1x.png 1x,img/logo-green-2x.png 2x">
</picture>
```

```scss
    /* Media query */
    @media (min-resolution: 192dpi) and (min-width: 37.5em),  /* apple device */
        (-webkit-min-device-pixel-ratio: 2) and (min-width: 37.5em), /* safari apple device */
        (min-width: 125em),
        only screen and (hover: none) /* touch pad */
    {
        /* show the large background-image */
    }
```
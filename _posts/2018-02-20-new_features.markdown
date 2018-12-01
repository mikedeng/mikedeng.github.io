---
layout: post
title:  "fill & currentColor & input placeholder"
date:   2018-02-20 14:01:39

categories: frontend
---
## make element move left
```css
    {
        margin-right: -3rem;
    }
```

## fill color
```css
    {
        width: 2.5rem;
        height: 2.5rem;
        fill: var(--color-grey-dark-3);
    }
```

## -webkit-input-placeholder
```css
    &::-webkit-input-placeholder {
        font-weight: 100;
        color: var(--color-grey-light-3);
    }
```

## currentColor, change along the parent color.
```css
    .a {
        color: orangered;
        .side-nav__icon {
            fill: currentColor;
        }
    }
```

## scale element from zero to full `height` from the `bottom`
```css
    .side-nav__item::before {
        transform: scaleY(0);
        /* transform from the bottom */
        transform-origin: bottom;
        transition: transform 1s;
    }

    .side-nav__item:hover::before {
        transform: scaleY(1);
    }
```

## z-index only works if we have specified position.
```css
{
    position: relative;
    z-index : 10;
}
```
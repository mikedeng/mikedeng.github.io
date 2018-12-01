---
layout: post
title:  "Media query with sass"
date:   2018-02-18 14:01:39

categories: frontend
---


## root
```scss

    *,
    *::after,
    *::before {
        margin: 0;
        padding: 0;
        box-sizing: inherit;
    }

    html {
        // This defines what 1rem is.
        font-size: 62.5%;

         // This large query should put in the first
        @include respond(tab-land) {
            // 1rem = 9px; 9 / 16 = 56.25%;
            font-size: 56.25%;
        }

        @include respond(tab-port) {
            // 1rem = 8px; 8 / 16 = 50%;
            font-size: 50%;
        }

        @include respond(phone) {
            // 1rem = 4.8px;  4.8 / 16 = 30%;
            font-size: 30%;
        }

        @include respond(big-desktop) {
            // 1rem = 12px; 12 / 16 = 75%;
            font-size: 75%;
        }
    }

    body {
        box-sizing: border-box;
    }
```


##  mixin definition
```scss
    // MEDIA QUERY MANAGER
    /*
        0      ~ 600px : PHONE
        600px  ~ 900px : TABLET PORTRAIT
        900px  ~ 1200px: TABLET LANDSCAPE
        1200px ~ 1800px: Is where our normal styles apply
        1800px +       : BIG DESKTOP

        $breakpoint argument choices:
        - phone
        - tab-port
        - tab-land
        - big-desktop
    */

    @mixin respond($breakpoint) {
        @if $breakpoint == phone {
             // 600 px
            @media (max-width: 37.5em) { @content; }
        }

        @if $breakpoint == tab-port {
             // 900 px
            @media (max-width: 56.25em) { @content; }
        }

        @if $breakpoint == tab-land {
            // 1200 px
            @media (max-width: 75em) { @content; }
        }

        @if $breakpoint == big-desktop {
             // 1800 px
            @media (min-width: 112.5em) { @content; }
        }
    }
```
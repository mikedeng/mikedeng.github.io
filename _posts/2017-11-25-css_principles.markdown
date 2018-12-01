---
layout: post
title:  "CSS一些原则"
date:   2017-11-25 22:30:39

categories: frontend
---

### 怎样清浮动

```css
  .clearfix:after {
    content: "";
    display: table;
    clear: both;
  }
```

### Typography 排版原则

  + 15 ~ 25px is perfect.
  + big font 60 ~ 90px for titles.
  + use line spacing between 120 and 150%.
  + 46 - 90 characters per line is good-looking.
  + use good fonts [ good web fonts ]
  + Decrease font weight when you use a big font-size

### Color 颜色选择原则

  + use only one base color 只使用一种基颜色
  + use a tool if you wanna use more colors 当使用多种颜色时， 用工具来决定
  + use color to draw attention 使用颜色吸引注意
  + Never use black in your design 不是使用黑色，因为黑色在现实中从来出现，如果用它会让人感觉不成熟。
  + 选择正确的颜色【红色 - 暖色（力量、激动）】
  + Red is a great color to use when power, passion, strength and excitement want to be transmitted. Brighter tones are more energetic and darker shades are more powerful and elegant.

- Orange draws attention without being as overpowering as red. It means cheerfulness and creativity. Orange can be associated with friendliness, confidence, and courage.


- Yellow is energetic and gives the feeling of happiness and liveliness. Also, it associates with curiosity, intelligence, brightness, etc.


- Green is the color of harmony, nature, life and health. Also, it is often associated with money. In design, green can have a balancing and harmonizing effect.


- Blue means patience, peace, trustworthiness, and stability. It is one of the most beloved colors, especially by men. It is associated with professionalism, trust and honor. That's actually why the biggest social networks use blue.


- Purple is traditionally associated with power, nobility and wealth. In your design, purple can give a sense of wisdom, royalty, nobility, luxury, and mystery.


- Pink expresses romance, passivity, care, peace, affection, etc.


- Brown is the color of relaxation and confidence. Brown means earthiness, nature, durability, comfort, and reliability.



图片与文字

+ put font directly on the image 把文本直接放在图片上。它只适用当图片与文字颜色有一定对时。
+ Overlay the image 先用一层带色透明的颜色覆盖图片，然后再在颜色图层上面写文字
+ use color gradients to achive stunning effects 使用颜色渐变来覆盖图片做出好效果
+ put you text in a box  把文字放在框里，框的背景是有些透明，这样可以看到它后面的图
+ Blur the image
+ The floor fade 让图片底边褪色

图标

+ use icons to list features/steps 用图标来展示特性、步骤
+ use icons to actions and links 用图标显示操作与链接
+ icons should not take a center stage 图标不应放在最重要显眼的位置，它应只起辅助作用
+ use icon fonts instead of static images 使用图标字体而不是静态图片

使用空白

+ Put whitespace between your elements
+ Put whitespace between your groups of elements
+ Put whitespace between your website's sections
+ But don't exaggerate

视觉层级

+ define where you wanna your audience to look first.
+ Establish a flow that corresponds to your content's message
+ Use white space to build that flow.

ideas

+ collect designs that you like
+ try to understand everything about them
+ why do they good looking
+ what do these sites have in common
+ how were they built in html & css
+ steal like an artist



Process of build a website

+ Define the goal of you project

  > Define your audience

  > Design your goal and audience in mind

+ Plan out everything

  > Plan you content: text, images, videos, icons, etc.

  > Start thinking about visual heirarchy.

  > Define the navigation.

  > Define the site structure if it's a bigger project.

+ Sketch your ideas before you design

  > Get inspired and think about your design

  > Get the idea out of your head: sketch your ideas before you start designing

  > Make as many sketches as you want, but don't make it perfect.

  > Never start designing without having an idea of what you want to build

+ Design and develop your website

  > use the provided guildelines

  > do that using html and css: designing in the browser

  > ​





Design guidelines

```
Beautiful Typography

1. Use a font-size between 15 and 25 pixels for body text

2. Use (really) big font sizes for headlines

3. Use a line spacing between 120 and 150% of the font size

4. 45 to 90 characters per line

5. Use good fonts

6. Chose a font which reflects the look and feel you want for your website

7. Use only one font



Using Colors Like a Pro

1. Use only one base color

2. Use a tool if you want to use more colors

3. Use color to draw attention

4. Never use black in your design

5. Choose colors wisely



Working with Images

1. Put text directly on the image

2. Overlay the image

3. Put your text in a box

4. Blur the image

5. The floor fade



Working with icons

1. Use icons to list features/steps

2. Use icons for actions and links

3. Icons should be recognizable

4. Label your icons

5. Icons should not take a center stage

6. Use icon fonts whenever possible



Spacing and layout

1. Put whitespace between your elements

2. Put whitespace between your groups of elements

3. Put whitespace between you website's sections

4. Define where you want your audience to look first

5. Establish a flow that corresponds to your content's message

6. Use whitespace to build that flow
```


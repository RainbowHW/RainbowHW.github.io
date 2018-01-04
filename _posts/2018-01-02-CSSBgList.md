---
layout: post
title: CSS3背景和列表
description: CSS3背景和列表
tag: CSS3
---

CSS背景和列表

#### 背景样式   背景样式包括内容、内边距padding和边框、不包括外边距margin

1. background-color  颜色 | transparent 

   transparent 是全透明黑色 RGBa（0，0，0，0）

2. background-image 设置背景图片

   一般情况下，同时设定背景和背景图片，**背景位于背景图片的下方，被背景图片覆盖**，防止图片加载错误时产生背景空白

3. background-position：长度值（x y）| 百分比(x% y%) | top | right | left | bottom | center  设置背景图像的起始位置

4. background-attachment : scroll(默认值) | fixed 设置背景图像是否固定或者随着页面其余部分滚动

5. background-repeat 

6. background 复合属性 **多个属性值用空格分隔开，不分先后顺序**

#### 列表样式

1. list-style-type: 关键字 | none 列表项标志的类型

   > 关键字：decimal（从1开始的整数） lower-roman 小写罗马数字 upper-roman 大写罗马数字   lower-alpha 小写英文字母 upper-alpha 大写英文字母
   >
   > 有序列表 ：

2. list-style-image 将列表项目的标志设置为自定义图片

3. list-style-position: inside | outside(默认值) 设置列表标志的位置

   > inside: 项目标记放在文本以内，是以标志对齐
   >
   > outside：项目标记放置在文本以外，是以文本对齐

   inside：

   ![CSS2](E:\a前端\github\younguei.github.io\images\article\CSS2.PNG)

   outside：

   ![outside](E:\a前端\github\younguei.github.io\images\article\CSS1.PNG)

4. list-style 复合属性 **多个属性值用空格分隔开，不分先后顺序**
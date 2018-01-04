

layout: post
title: CSS3字体样式
description： CSS3的字体样式
tag: CSS3
---

设置网页字体样式：

1. **文字**（单个文字） : 颜色、字体大小，字体，加粗等效果
2. **文本** （大段的文字）: 行高、对齐方式、文本修饰

#### 文字样式

font-family 含有空格字体名和中文，用引号括起来  font-family: "Times New Roman"；

font-size 

font-color

font-weight

font-style

#### 文本样式 ：属性继承的时候，是将em转换为px来继承的（继承计算值）

**text-align**设置**块级元素**的居中效果 (只对块级元素有效) `<div><img src="img/logo.png"/></div>`  设置行内元素对齐方式可以外层嵌套div

**vertical-align **只对**行内元素生效**，对**块级元素不生效** `<span>只对行内元素有效</span>`

```
vertical-align:baseline | sub | super | top | text-top | middle | bottom | text-bottom | 长度（表示偏移距离） | 百分比
```

line-height  常用em来定义行高 `font-size:20px; line-height:1.3em` 行高为26px (同样也可以使用百分数来定义行高，是相对于字体大小计算的)

word-spacing: 设置元素内**单词**之间的间距  (以空格开区分单词，当连续汉字的时候不会产生间距 当汉字之间存在空格的时候就会产生间距)

letter-spacing: 设置元素内**字母**之间的间距 （连续汉字之间没有空格的时候，也会产生间距）

text-transform: capitalize uppercase lowercase  none

text-decoration 
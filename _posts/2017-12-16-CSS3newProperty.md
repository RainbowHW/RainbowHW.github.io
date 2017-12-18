---
layout: post
title: CSS3新增属性
description: CSS3新增属性归纳
tag: CSS3
---

## CSS3新增属性

1. RGBa属性：增加透明度通道  Alpha参数是一个介于0.0和1.0之间的参数
2. border-radius属性：设置圆角效果

```
border-radius:左上 右上 右下 左下;
```

3. text-shadow属性：文字阴影

```css
text-shadow:x轴方向的阴影 y轴方向上的阴影 模糊范围 阴影颜色；/* 正方向 下 右*/
```

4. gradient属性：渐变

> `linear-gradient`: `background:linear-gradient(to left，red，blue);`
>
> `radial-gradient`: `background:radial-gradient(中心位置，尺寸，颜色);`

5. box-shadow属性

> `box-shadow:x轴方向偏移 y方向偏移 模糊范围 阴影颜色`

6. @font-face字体规则：可以引用外部字体

```
@font-face{
	font-family:myfont; /*给引用的字体指定名称 利用该名称来使用字体到网页上*/
	src: url(字体路径);
}
```


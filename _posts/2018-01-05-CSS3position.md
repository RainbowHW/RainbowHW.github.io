---
layout: post
title: CSS3定位position
description: CSS3定位
tag: CSS3
---

### 布局方式

1. 标准流  2. 浮动流  3. 定位

#### 定位position属性  配合left top right bottom属性来实现元素位置的改变

position: static | relative | absolute | fixed | inherit 

关于设置定位属性后元素：后写元素的层级大于先写的元素

#### 1. relative

```
position:relative;
right: 50px;   向左侧移动50px
bottom: 50px;  向上侧移动50px
```

当设置left top 的属性的时候，**坐标原点为网页的左上角**，**以向右 和向下为x、y正方向**

当设置right bottom 的属性的时候，**坐标原点为网页的左上角**，**以向左和向上为x、y正方向**

#### 2. absolute 配合 left bottom right top位置属性 **元素将会脱离正常的文档流** 

```css
position:absolute; 
<!--当只有定位属性，不存在位置属性时，元素还存在普通文档流中，未脱离文档流 -->
left:10px;
top:10px;
```



**位置属性是相对与窗口定位的，也许页面很长，但是absolute是只针对于窗口**

当设置left top 的属性的时候，坐标原点为网页的**左上角**，**以向右 和 向下为x、y正方向**

当设置right bottom 的属性的时候，坐标原点为网页的**右下角**，**以向左和向上为x、y正方向**

#### relative 和 absolute 归纳

relative是相对于本身位置进行的定位  

absolute是相对于窗口定位的

#### 3.fixed  配合left bottom right top 位置属性 使用，脱离文档流，根据窗口四个角点进行定位

根据窗口来定位，即使父元素存在定位属性，也不受父元素影响

#### 4.inherit 在子元素中使用该属性值的时候，定位是继承父元素定位方式

### z-index 

可以设置元素的叠加顺序，但**依赖定位属性**

所有带有定位属性的元素都是带有层级的，先写的带有定位属性的元素将会被后写的带有定位属性的元素覆盖

> z-index
>
> 1. 依赖定位属性
> 2. z-index大的元素会覆盖z-index小的元素
> 3. z-index为auto的元素不参与层级比较
> 4. **z-index为负值，元素被普通流中的元素覆盖**

#### 操作实例：实现侧边栏导航
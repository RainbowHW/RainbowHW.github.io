---
layout: post
title: HTML5新增元素
description: HTML5新增元素归纳
tag: HTML
---

## HTML5新增元素与属性

1. 格式标签(**?表示存在疑问 *表示重要**)

> ？`<bdi>` (Bi-directional Isolation)：设置一段文本，使其脱离其父元素的文本方向  **支持的浏览器比较少**
>
> ​    `<mark>`定义带有标记的文本 自动给文本添加黄色的背景
>
> ​    `<meter>` 定义衡量大小的尺度，该标签的效果就像 硬盘图标
>
> ​    `<progress>` 进度条
>
> ​    `<rp>` 定义不支持ruby元素的浏览器所显示的内容 
>
> ​    `<ruby>` 定义注释，比如文字上方的拼音 与`<rt>`元素一同使用
>
> ​    `<rt>` 定义字符的解释和发音  `<ruby>胡<rt>hu</rt></ruby>` 效果就是文字上方添加拼音
>
> ​    `<time>`定义一个 日期/时间
>
> \*  `<wbr>` 单标记 在浏览器窗口或父级窗口宽度足够的情况下，不换行；在宽度不足的情况下，在加了<wbr>处主动换行。

2. 窗体标签

> ​    `<datalist>` 规定了input元素可能的选项列表，该元素用于给input标签提供一个下拉列表，用于数据输入;例子 `<input id="myCar" list="cars"/><datalist id="cars"><option value="BMW"><option value="Ford"</datalist>` 注意：input的list属性和datalist的id属性配合
>
> ?  `<keygen>` 生成密钥 没有具体使用过
>
> ​    `<output>` 用于输出计算结果 比如加减运算输出结果

3. 图像

> ​    `<cancas>`
>
> ​    `<figure>` 用于定义图像和名称 配合`<figcaption>`使用
>
> ​    `<figcaption>` 为`<figure>`元素定义标题  **注意：这个元素应该位于<figure>元素的首或尾位置**

4. 音频和视频

> ​    `<audio>`
>
> ​    `<video>`
>
> ​    `<source>`
>
> ​    `<track>`

5. 链接

> ​    `<nav>`

6. 区段元素

> ​    `<header>`
>
> ​    `<footer>`
>
> ​    `<article>`
>
> ​    `<aside>`
>
> ?  `<dialog>` 定义一个对话框或窗口
>
> ​    `<details>` 定义了一个用户可以点击展开或关闭的补充细节
>
> ​    `<summary>`  配合`<details>`使用

```
<details>
	<summary>this is the title<summary>
	content......
</details>
```

7. 嵌入内容

> ​    `<embed>`定义一个容器，嵌入外部插件
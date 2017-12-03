---
layout: post
title: 锋利的jQuery代码案例
description: jQuery Code
tag: jQuery代码练习
---

## 第二章 案例

函数`filter()` `is()`

### `filter()` 

定义和语法：将匹配元素集合缩减为匹配指定选择器的元素。

`.filter(selector)` 参数selector为字符串，包含匹配当前元素集合的**选择器表达式**

`$("ul li").filter(:even).css("background-color","red");`

### is()

定义和语法：根据选择器、元素来检测匹配元素集合，**如果这些元素中至少有一个元素匹配，则返回true**

`.is(selector)` 参数selector为字符串值，包含匹配元素的**选择器表达式**

`if($target.is(":visible"))` 检测是否可见，返回布尔值 
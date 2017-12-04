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

## 第三章 案例

`var tooltip = "<div id='tooltip'>"+ this.title +"</div>"` 

```javascript
$(document).ready(function(){
  var x = 15;
  var y = 15;
  $("p a.tooltip").mouseover(function(e){
      this.myTitle = $(this).attr("title");  //this.myTitle
      console.log(this.myTitle);
      this.title = "";
      var tooltip = "<div id='tooltip'>" + this.myTitle + "</div>";
      $("body").append(tooltip);
      $("#tooltip").css({
        left : e.pageX + x  + "px",
        top : e.pageY + y  + "px"
      }).show("slow");
  }).mouseout(function(){
      this.title = this.myTitle;   			//this.myTitle
      $("#tooltip").remove();
  }).mousemove(function(e){
      $("#tooltip").css({
        left : e.pageX + x  + "px",
        top : e.pageY + y  + "px"
      })
  });
})
```

> jQuery中的`clientY` `pageY` `screenY` **都是获取鼠标位置的属性**
>
> `screenX screenY` 是距离**电脑屏幕**边缘的距离
>
> `clientX clientY`是距离当前可视窗口的距离，**除去浏览器顶部菜单栏**
>
> `pageX pageY`是相对于当前页面中除去菜单栏的距离，**在`clientX clientY`的基础上加上滚动条滚动的距离**

## 第四章 案例
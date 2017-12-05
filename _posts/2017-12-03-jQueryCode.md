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

jQuery中的`clientY` `pageY` `screenY` **都是获取鼠标位置的属性**

`screenX screenY` 是距离**电脑屏幕**边缘的距离

`clientX clientY`是距离当前可视窗口的距离，**除去浏览器顶部菜单栏**

`pageX pageY`是相对于当前页面中除去菜单栏的距离，**在`clientX clientY`的基础上加上滚动条滚动的距离**

## 第四章 案例

疑问：什么使背景图片居中

`parents()` 取得一个包含所有匹配元素的祖先元素和集合元素

> 几个函数：
>
> 1. `parents(可选参数)` 返回祖先元素**多个祖先元素** 距离近的祖先元素先返回 `$("b").parents()`
>
>
> 2. `parent(可选参数)`返回父元素 **父元素只有一个**
> 3. `find(参数必须要有)`获得元素的后代元素  `$("ul").find("li")`
> 4. `width()` 获取或设置元素的宽度
> 5. `animate({css样式},time)`
> 6. `eq()` 将匹配元素缩减指定index上的一个元素**从0开始** `$("li").eq(2).css()` **为第三个li添加css样式**
> 7. `siblings()`选取某个元素的所有兄弟元素
> 8. `if(!$(".contentList").is(":animated"))` 确保处于动画时不能再添加动画效果 `:animated`
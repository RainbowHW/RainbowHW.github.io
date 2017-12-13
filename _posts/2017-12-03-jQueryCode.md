---
layout: post
title: 锋利的jQuery代码案例
description: jQuery Code
tag: jQuery
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

## 第五章 案例

1. 放大缩小网页字体  (巧妙地是用**一个点击函数给两个按钮添加事件 **缺点是利用bootstrap给span按钮添加class后 无法使用)

```javascript
$("span").click(function(){
  var fontSize = parseFloat($("#para").css("fontSize"));
  var fontUnit = $("#para").css("fontSize").slice(-2);
  var ele = $(this).attr("class");  //这里this要注意  错误写法var ele = $("span").attr("class"); 
  if(ele == "bigger"){
    fontSize += 5;
  }else if(ele == "smaller"){
    fontSize -= 5;
  }
  $("#para").css("fontSize",fontSize+fontUnit);
})
```

2. 网页选项卡，通过显示或隐藏来切换内容

   `index(this)` 获取当前元素的索引值

```javascript
$(".tab_menu ul li").click(function(){
  var index = $(".tab_menu ul li").index(this);  //返回当前元素的索引值
  $(this).addClass("selected").siblings().removeClass("selected");
  $(".tab_box div").eq(index).show().siblings().hide();
})
```

3. 网页换肤

   网页换肤的原理就是通过调用不同的样式表来实现不同皮肤的切换，并且将设置好的皮肤放入cookie中，这样下次打开页面的时候会自动显示自定义皮肤。

> (1).引用不同的css样式：**jQuery 可以选取link标签中的herf属性值并修改**
>
> `$("#filecss").attr("href","css/"+this.id+".css");`

当单击不同的li时，根据li的id属性，切换样式表的herf属性值

```javascript
var $li = $("#skin li");
$li.click(function(){
  $(this).addClass("selected").siblings().removeClass("selected"); //给点击的li添加样式
  //link标签一定要与id属性cssfile
  $("#cssfile").attr("href","css/"+this.id+".css");  //this.id css样式表链接地址由点击的li的id确定
})
```

>  (2).设置cookie
>
>  `$.cookie("MyCssSkin",this.id,{path:'/',expires:10})；`将当前皮肤保存到cookie中(**也就是this.id值**)
>
>  网页加载后获取cookie存入的皮肤值
>
>  ```
>  var cookie_skin = $.cookie("MyCssSkin");
>  $("#"+cookie_skin).addClass("selected").siblings().removeClass("selected");
>  $("#cssfile").attr("href","css/"+cookie_skin+".css");
>  $.cookie("MyCssSkin",cookie_skin,{path:'/',expires:10});
>  ```

4. `cookie`使用教程 [JavaScript设置Cookie](http://www.runoob.com/js/js-cookies.html)

   cookie以名/值对形式存储：`username = John Doe`

   > * 使用JavaScript创建Cookie：使用document.cookie属性来创建、修改及删除cookie
   >
   >   创建：`document.cookie = "username = John Doe"`
   >
   >   ​	   `document.cookie = "username = John Doe;expires=Thu,18 Dec 2018` 使用expires指定一个过期时间
   >
   >   ​	   `document.cookie = "username = John Doe;expires=Thu,18 Dec 2018 path=/` 使用path指定路径，默认为当前页面
   >
   > * 使用JavaScript读取Cookie：`var x = document.cookie`;

5. cookie使用教程 (jQuery设置Cookie)

   > * 写入Cookie `$.cookie('the_cookie','the_value')`;
   >
   > * 读取Cookie `$.cookie('the_cookie');`
   >
   > * 删除Cookie `$.cookie('the_cookie',null);
   >
   > * 其它参数:
   >
   >   ```javascript
   >   $.cookie('the_cookie','the_value',{
   >     expires: 7,  //到期  expires:(number|Date)
   >     path: '/',  //文件路径，默认为当前目录
   >     domain: 'jquery.com',//cookie的域名，默认为当前页面创建
   >     secure: true   //设置为true 传输按HTTPS安全协议
   >   });
   >   ```


## 第六章 案例


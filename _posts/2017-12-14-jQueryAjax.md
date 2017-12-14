---
layout: post
title: Ajax
description: jQuery与Ajax的应用
tag: jQuery
---

## Ajax

工作原理相当于在用户和服务器之间加一个中间层，实现了用户操作和服务器响应的异步操作

#### JavaScript操作Ajax

#### jQuery中的Ajax

##### `load()方法`

1.  `load(url[,data][,callback])` 载入远程的HTML代码并插入选中的DOM中  **插入的是整个HTML文件**

```javascript
<script type="text/javascript">
	$(function(){
      $("#send").click(function(){
        $("#resText").load("test.html");
      })
	})
</script>
```

2. `load(url+选择器[,data][,callback])` **筛选**载入的远程HTML代码并插入DOM中

```javascript
<script type="text/javascript">
	$(function(){
      $("#send").click(function(){
        $("#resText").load("test.html .comment"); //只载入test.html中class为comment的元素
      })
	})
</script>
```

3. `load(url[,data][,callback]) `[,data]表示向服务器传递的键值对，没有参数则默认为GET传递，反之则为POST传递

```
$("#resText").load("test.php",{name:"rain",age:"22"}),function(){  //POST传递
  //..
}}
```

4. `load(url[,data][,callback])`回调函数无论请求成功失败，都会执行，回调函数有3个参数，`responseText `表示返回的内容`textStatus` 表示请求状态  `XMLHttpRequest` 表示这个`XMLHttpRequest`对象

```javascript
$(function(){
			$("#send").click(function(){
				$("#resText").load("test.html .comment",function(responseText,textStatus,XMLHttpRequest){
					alert(responseText);
					alert(textStatus);
					alert(XMLHttpRequest);
				});
			})
		})
```

##### `$.get()方法`

1. `$.get(url[,data][,callback][,type])` [,type]表示服务器返回内容的格式，包括xml、 html、script、json、text、和_default

   **注意：**

   [,callback]只有在**数据执行成功的时候才会调用**

```
$(function(){
  $("#send").click(function(){
    $.get("get.php",{
      username : $("#username").val(),  //数据传递给php文件
      content : $("#content").val(),
    },function(data,textStatus){    //php中数据传递给html
      $("#resText").html(data);
    })
  })
})
```

#####`$.post()方法`

1. 使用方法类似`$.get()` 区别是提交的方式，一个是post一个是get

##### `$.getScript()`

有时候，页面加载的时候不需要加载全部的js文件，可以利用该函数动态的添加js文件

`$.getScript(url,callback)` 支持回调函数

`$(document.createElement("script")).attr("src","test.js").appendTo("head");`

##### `$.getJson()`

动态加载json文件，同样支持回调函数

##### `$.ajax()` jQuery最底层的Ajax方法

`$.ajax(option)` 只有一个参数

```javascript
$(function(){
  $("#send").click(function(){  //实现了$.getScript()方法
    $.ajax({
      type: "GET",
      url: "test.js",
      dataType: "script"
    });
  });
})
```
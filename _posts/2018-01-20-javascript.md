---
layout: post
title: JavaScript基础语法DOM及BOM
description: 慕课网前端入门JavaScript
tag: JavaScript
---

### JavaScript的组成：

完整的JavaScript是由ECMAScript(语法)、DOM、BOM组成的。

### JavaScript的语法：

ECMAScript中的一切（变量、函数名和操作符）都区分大小写

### JavaScript的数据类型：

ECMAScript中有5中简单的数据类型：**undefined string boolean number null**  （注意：undefined是派生自null值的）

一种复杂数据类型：**object**

typeof：检测变量类型 返回值为6种类型

### JavaScript的流程控制：

> 1.prompt(): 弹出输入框

### JavaScript中的内置对象

> 1. Array
>
>    数组方法：
>
>    arrayObject.join([separator]) 输出字符串 separator可选，指定要使用的分隔符，如果省略，则**使用逗号**，
>
> 2. String
>
> 3. Math
>
> 4. Date

### JavaScript的DOM

> 给元素设置样式： 
>
> ele.style.styleName = styleValue  (**注意：styleName不能使用 中划线- 要使用驼峰命名**)
>
> getAttribute(attribute) :  p.getAttribute(class) 等价于 p.className
>
> `<p id="text" class="text" align="center" data-type="title">` 
>
> **p标签自带id等属性 所以可以利用点符号来获取 但假若不是自带的属性的话，必须使用getAttribute()函数获取** document.getElementById("text").id  获取id   `p.getAttribute("data-type")`

### JavaScript的事件

> HTML事件：在HTML元素上绑定事件  `<tag 事件="执行脚本"></tag>`
>
> DOM0级事件：  **事件没有写在元素上**
>
> 1. 通过DOM获取HTML元素
> 2. （获取的HTML元素）.事件 = 执行脚本  执行脚本可以是一个匿名函数，也可以是一个函数的调用

#### 鼠标事件

> 1. onload : 页面加载完成后触发  `window.onload = function(){....}`
>
> 2. unload：页面卸载后触发
>
>    表单控件事件
>
> 3. onfocus：控件处于焦点状态的时候触发事件
>
> 4. onblur：控件失去焦点状态的时候触发事件
>
> 5. onchange: 常用于select元素，当内容改变的时候触发
>
> 6. onsubmit: 表单中提交按钮点击的时候发生  **绑定在form表单标签上，不是绑定在提交按钮上**
>
> 7. onresize：调整浏览器窗口时触发  **绑定到window对象上**
>
> 8. onscroll：拖动滚动条时触发  **可以绑定到window 或者 在某个对象上滚动时候也可以绑定到这个元素上**

#### 键盘事件

> 1. onkeydown :按下一个键盘按键时发生
> 2. onkeypress：按下一个按键并释放后发生
> 3. onkeyup： 键盘松开时触发
>
> **keyCode**属性： 返回按键的代码值  event.keyCode

### JavaScript的BOM

#### window对象: 

​	**是ECMAScript中的GLOBAL对象，又是通过JavaScript访问浏览器窗口的一个接口**

> 所有的全局变量和方法都被归在window上
>
> 全局函数：
>
> 全局变量：

#### window对象方法：

> window.alert("content");
>
> window.confirm("message");  存在返回值  点击确定返回true 点击取消返回false
>
> window.prompt("text,defaultText"); 存在返回值 点击取消返回null 点击确认返回**输入字段当前显示的**文本
>
> 1. window.open(pageURL,name,parameters)
>
>    name: **为新窗口取一个名称** name声明了新窗口的名称，方便后期通过name对子窗口的引用
>
>    parameters：一组参数 用逗号分隔开 表示窗口的参数 比如width height left等等
>
>    `"width=400,height=200,left=0,top=0,toolbar=no,toolbars=no,status=no"`
>
>    parameters 参数列表：
>
>    |   width    |          窗口宽度           |
>    | :--------: | :---------------------: |
>    |   height   |          窗口高度           |
>    |    left    |         窗口x轴坐标          |
>    |    top     |         窗口y轴坐标          |
>    |  toolbar   | 是否显示浏览器的工具栏  toolbar=no |
>    |  menubar   |         是否显示菜单栏         |
>    | scrollbars |         是否显示滚动条         |
>    |  location  |        是否显示地址字段         |
>    |   status   |         是否添加状态栏         |
>
> 2. window.close() 关闭当前窗口
>
> **JavaScript是单线程语言，单线程就是执行的代码必须按照顺序执行  但是也可以通过设置超时值或间歇值来使代码在特定的时间执行**
>
> 3. setTimeout(code,millisec)   等价于window.setTimeout() 习惯上省略window   **最好code为匿名函数**    **返回值为一个ID值，通过它取消超时调用**
>
>    clearTimeout(timeID)
>
> 4.  setInterval(code,millisec) 
>
>    clearInterval(timeID)

#### location对象：

​	**该对象提供了与当前窗口中加载的文档有关的信息，它既是window对象的属性，又是document对象的属性**

#### location对象属性：

> 1. location.href : 返回当前加载页面的完整的URL  location.href === window.location.href
>
> 2. location.hash  (hash: #后跟零或多个字符)   返回URL中的hash，如果不包含则返回空字符串
>
>    `file:///c:/code/index.html#top`  hash返回#top
>
> 3. **location.search: 返回URL的查询字符串，这个字符串以？开头**
>
> 4. location.host : 返回服务器名称及端口号
>
> 5. location.hostname: 返回服务器名称
>
> 6. location.path: 返回目录及文件名
>
> 7. location.port : 返回端口号

#### location对象的方法：

> 1. 改变浏览器位置的方法： location.href 属性   **该方法会在历史记录生成新纪录**
>
>
> 2. location.replace(页面地址)；  重新定向URL，但是**该方法不会再历史记录中生成新纪录**
>
> 3. location.reload(): 重新加载当前显示的页面
>
>    location.reload() 可能从缓存中加载
>
>    location.reload(true) 强制从服务器端重新加载

#### history对象：

​	保存着用户在浏览器中访问页面的历史记录

#### history对象的方法：

> 1. history.back() 回到历史上一步  === history.go(-1)
> 2. history.forward() 回到历史下一步   === history.go(1)
> 3. history.go(参数)  参数为负数表示后退，参数为正数表示前进

#### screen对象

​	screen对象包含有关客户端显示屏幕的信息

#### screen对象属性

> 1. screen.availWidth: 获取**屏幕的**宽度
> 2. screen.availHeight:
> 3. window.innerWidth:  获取**窗口显示区的**宽度
> 4. window.innerHeight: 

#### navigation对象

​	提供浏览器及操作系统的信息,**判断设备的终端是移动还是PC**

#### navigation的属性：

> 1. navigation.userAgent: 返回浏览器类型

   
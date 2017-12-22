---
layout: post
title: Bootstrap3
description: 详解bootstrap导航条
tag: Bootstrap
---

Bootstrap中导航条设计的知识比较综合，下面拆分开来研究一下

#### 整体概览

```html
<nav class="navbar navbar-default">   
  	<!--   1   -->
	<div class="navbar-header">
      	<!--必须要存在.navbar-brand的a标签-->
		<a href="#" class="navbar-brand">网页logo</a>  
	</div>
  
  	<!--   2 被折叠区域  -->
	<div>
        <!--表示导航条中的导航 -->
      	<!--   3   -->
		<ul class="nav navbar-nav">
			<li><a>...</a></li>
			<li><a>...</a></li>
		</ul>
        <!-- 表示导航条中的form表单-->
      	<!--   4   -->
		<form class="navbar-form navbar-left">
			<div class="form-group">
				<input type="text" class="form-control">
			</div>
			<button type="submit" class="btn btn-default">submit</button>
		</form>
	</div>
</nav>
```

1.

```html
<div class="navbar-header">
   <!--这个按钮在屏幕一定小的时候 会出现  点击可以显示隐藏导航栏  data-target链接到导航的主体部分-->
  <button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-target="#navbarlinks">
     <!--该类表示 障碍人士使用-->
    <span class="sr-only">Toggle navigation</span>
     <!--表示面包图标-->
    <span class="icon-bar"></span>
    <span class="icon-bar"></span>
    <span class="icon-bar"></span>
  </button>
  <!--必须要存在.navbar-brand的a标签-->
  <a href="#" class="navbar-brand">网页logo</a>  
</div>
```

2.

```html
<!--表示导航栏的主体 -->
<div class="collapse navbar-collapse" id="navbarlinks">
   <!--导航-->
 	<ul class="nav navbar-nav">
      <li></li>
      <li></li>
      <!--导航中的下拉菜单-->
      <li class="dropdown">
        <a href="#" class="dropdown-toggle" ...>MORE</a>
        <ul class="dropdown-menu">
          ...
        </ul>
      </li>
  	</ul>
   <!--表单-->
  	<form class="navbar-form">
      
  	</form>
</div>
```

3.该部分就是一个导航样式

4.该部分就是一个添加`navbar-form`的表单

将复杂的导航栏划分区块，逐个分析，还是简单的。




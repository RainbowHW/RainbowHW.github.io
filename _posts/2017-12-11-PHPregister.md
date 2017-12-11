---
layout: post
title: PHP用户登录
description: PHP文本数据库模拟用户登录
tag: PHP
---

## 前言

实现用户注册、用户登录功能

> * 注册功能：信息填写完毕后，点击提交，用户数据自动追加到**users.txt**中，然后**跳转到登陆页面**
> * 登陆功能：登陆时，将输入的用户名和密码与users.txt中对应的用户比较，信息一致则登陆成功

## 开始吧

1. `$_SERVER['REQUEST_METHOD']`存储的是表单的提交方式，若表单method为POST则该变量值为POST;

2. `include_once "文件路径"` 引入文件

   > `require`:使用方法`require "index1.php;"`  这个**语句**通常放在php程序的最前面，php程序执行前，就会先读取require指定的文件，使它变为php程序网页程序的一部分
   >
   > `include`：使用方法`include "index1.php";` 这个**语句**放在程序控制的处理部分中，php程序读到include的文件时，才将它读进来
   >
   > **两者的最主要区别**
   >
   > 1. `require` 读取一个文件存在错误的话，显示致命错误，程序**中断执行**
   > 2. `include` 读取一个文件存在错误的话，显示警告错误，程序**继续执行**
   > 3. `require_once include_once` 都表示相同的文件只引用一次，避免多次引入相同的文件造成变量、函数重复定义

3. 相对路径：

   > `./` 表示在当前目录开始寻找文件 **`./index1.php `等价于`index1.php`**
   >
   > `/`**？？？？ 表示在下一级目录开始寻找文件/表示根目录来写绝对路径？？ 哪个正确**
   >
   > `../`在上一级目录开始寻找文件

4. 区分登陆还是注册

   > ```php
   > $a = $_GET['a']; //从url中获取一个变量
   > if($a == "register"){
   > 	//注册操作
   > }else if($a == "login"){
   >   	//登陆操作
   > }else{
   >    echo "网站建设中";
   > }
   > ```

5. php和html代码混合

   ```php+HTML
   <?php
   	if($a > 0){
         ....
   	}
   ?>
   <form>
   //...      //中间html代码将php分隔开来
   </form>
   <?php
   	else{  //接上面的php代码if
         ... 
   	}
   ?>
   ```

6. 当输入成功的时候不显示表单

   ```php+HTML
   <?php
   if($_SERVER['REQUEST_METHOD'] == 'POST'){
   		//php代码	
   }else{
     ?>  
     <form method="post" action="">
   	<!-- form表单 -->
     </form>
     <?php 
   }
   ```

   ​

7. 登陆操作

   判断输入的邮箱密码是否和数据库中符合

8. 密码多了一个换行符

   `substr($line,0,strlen($len)-2);` 截取字符串函数  去除最后两个符号`\r\n`

   `substr(string,start,length);` 返回字符串的一部分

   > 如何解决最后输入的一个用户密码不会被删除最后两个字符 因为没有换行符所以`fgets()` 不会获取回车换行符，在利用`substr()`的时候会多删除两个字符

9. 当用户**注册成功**后自动**跳转登录**页面 (三种方式)

   > 1. JS跳转：`<script>window.location.href = "?a=login";</script>`
   > 2. html跳转  `<head><meta `
   > 3. php跳转

10. `<?php `

11. 将密码文件放在上级目录中，这样就不会被访问到

    > 方法1：`useraccount.txt` 放在上级目录中   引用方法`../密码文件位置`
    >
    > 方法2：`<?php exit;?>` 将文件改为php文件，并在文件第一行写入该diamagnetic即可
    >
    > ​		`<?php exit;?>`  exit;表示后面的不执行

    ​




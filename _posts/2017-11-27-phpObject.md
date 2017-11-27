---
layout: post
title: PHP面向对象
description: PHP-Object
tag: PHP
---

## 1、面向对象内容 

* 类：定义了一件事物的抽象特点，具有抽象性
* 对象：类的实例
* 多态：相同的函数或方法可作用于多种类型的对象上获得不同的结果
* 重载：方法具有相同的名称，但是参数列表不同，不同的参数的函数或方法之间，互称为重载函数或方法
* 构造函数：不同于JS，PHP中构造函数位于类中，在配合new操作符的同时，将对象成员变量初始化 

```php
<?php
  class Site{
  var $url;
  var $title;
  
  function __construct($par1,$par2){
    $this->url = $par1;
    $this->title = $par2;
  }
  function getUrl(){
    echo $this->url ;
  }
  function getTitle(){
    echo $this->title;
  }
}
$taobao = new Site('www.taobao.com','淘宝');		//这里自动调用了构造函数 传入了url、title两个参数，将对象中变量初始化
$taobao->getTitle();		//淘宝
echo '</br>';
$taobao->getUrl();			//www.taobao.com
?>
```



* 析构函数：在对象结束生命周期后，系统自动调用析构函数，释放内存


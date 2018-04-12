---
layout: post
title: localStorage相关知识
description: Vue学习中遇到的问题
tag: Vue
---

### web本地存储 (localStorage sessionStorage)

> 1. localStorage: 长期存储 ,浏览器刷新、关闭后数据仍然存在
> 2. sessionStorage: 临时存储，数据在浏览器打开期间存在，浏览器关闭数据消失

#### 保存数据到本地

会将数据转换为字符串，所以要解析为JSON字符串格式

```
const info = {
  name: 'Lee',
  age: 20,
  id: '001'
};
sessionStorage.setItem("key",JSON.stringify(info));
localStorage.setItem("key",JSON.stringify(info));
```

#### 从本地存储获取数据

存储的为字符串格式，要解析为JSON数据

```
var data1 = JSON.parse(sessionStorage.getItem("key"));
var data2 = JSON.parse(localStorage.getItem("key"));
```

#### 本地存储中删除某个保存的数据

```
sessionStorage.removeItem("key");
localStorage.removeItem("key");
```

#### 删除本地保存的所有数据

```
sessionStorage.clear();
localStorage.clear();
```


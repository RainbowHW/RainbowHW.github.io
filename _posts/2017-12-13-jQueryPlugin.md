---
layout: post
title: jQuery Plugin
description: jQuery插件
tag: jQuery
---

插件(Plugin)也称为扩展(Extension),是利用jQuery编写的程序(工具)

## [jQuery Validate](http://www.runoob.com/jquery/jquery-plugin-validate.html)

该插件为表单提供了验证功能

#### 起步 导入js库 (jQuery validate 中文信息提示包 ) 

```
<script src="https://cdn.bootcss.com/jquery/3.2.1/jquery.min.js"></script>
<script src="https://cdn.bootcss.com/jquery-validate/1.17.0/jquery.validate.min.js"></script>
<script src="https://cdn.bootcss.com/jquery-validate/1.17.0/localization/messages_tr.min.js"></script>
```

#### 默认校验规则

| 序号   | 规则                                       | 描述   |
| ---- | ---------------------------------------- | ---- |
| 1    | required:true/required:"#aa:checked"/required:function(){} | 必须字段 |
| 2    | ..                                       | ..   |
| 3    | ..                                       | ..   |

#### 使用方式

```html
<form action="" method="POST" id="myform2">
			<label>Username: <input type="text" name="username" value="" placeholder="enter your username"></label><br/>
			<label>Age: <input type="text" name="age" value="" placeholder="enter your age"></label><br/>
			<label>Birthday: <input type="text" name="birthday" value="" placeholder="enter your birthday"></label><br/>
			<label>Password: <input type="password" name="password" id="password2" value="" placeholder="enter your password"></label><br/>
			<label>Confirm Password: <input type="password" name="confirmPassword" value="" placeholder="confirm your password"></label><br/>
			<input type="submit" name="submitBtn" value="Sign In">
	</form>
```

1. 将校验规则写入html控件代码中

   ```javascript
   $().ready(function(){
     $("表单选择器").validate();// 表单验证开启生效
   })
   ```

   ​

2. 将校验规则写到js代码中

   ```javascript
   //点击提交后，会自动验证表单控件
   $(document).ready(function(){
     $("表单选择器").validate({
       reles: {
         //...
       },
       messages: {
         //...
       }
     });
     $("#myform2").validate({
       rules: {
         username: {
           required: true,
           minlength: 2,
         },
       },
       messages: {
         username: {
           required: "请输入用户名",
           minlength: "用户名长度不得小于2字符",
         },
       }
     })
   })
   ```

#### 常用方法：

1. 用其它方式代替默认的SUBMIT

   ```javascript
   $().ready(function(){
     $("表单控件选择器").validate({
       submitHandler:funcion(form){
         alert("提交事件");
         form.submit();//提交表单，表单内容重置
       },
       rules: {
         //...
   	},
      messages: {
   	 //...
      },
     })
   })
   ```

2. 更改错误信息显示位置 `errorPlacement:function(error,element){......}`


## [管理Cookie的插件-Cookie](http://www.jq22.com/jquery-info254)

Cookie需要上传到服务器上才能查看结果

#### 起步 导入js库

```
<script src="https://cdn.bootcss.com/jquery/3.2.1/jquery.min.js"></script>
<script src="https://cdn.bootcss.com/jquery-cookie/1.4.1/jquery.cookie.min.js"></script>
```

#### 使用方式

1. 创建一个Cookie并设置过期时间 `$.cookie('the_cookie','the_value'，{expires: 7});`
2. 读取一个Cookie `$.cookie('the_cookie');`
3. 删除一个Cookie `$.cookie('the_cookie',null);`
4. 可选参数

```
$.cookie("the_cookie","the_value",{
	expires: 7, //这个cookie的有效期
	path: '/', //该页面cookie的路径
	domain: '' ,//页面域名
	secure: true// 安全协议 false为http协议 true为https协议
})
```


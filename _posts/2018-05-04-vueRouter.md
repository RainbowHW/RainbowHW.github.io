---
layout: post
title: Vue-router笔记
description: JSpang系列教程
tag: Vue
---

### 1.Vue-router入门

当我们写一个单页面应用的使用需要使用到路由。

路由：是SPA单页应用的路径管理器，单页应用只有一个index.html页面，所以不能使用a标签来跳转页面

**在`router/index.js`文件中添加新路由** :

添加路由三部曲:

> 1. 声明路由页面组件
> 2. 在`index.js`中引入组件
> 3. 添加路由配置

标签: 

`<router-view></router-view` router的内容在标签内显示

`<router-link></router-link>` 路由页面的跳转 相当于a标签

**思考：**

路由是注册到全局上的，所以页面执行顺序：

> 当项目打包后，router的内容会展示到`router-view`标签内，router是全局注册的，所以点击`router-link`会切换`router-view`展示的内容，从而实现在一个`index.html`页面中切换内容

### 2.`vue-router`中配置子路由

子路由：在一个页面下有多个页面，例如：主栏目下有两个子页面

子路由的写法是在原来的路由的配置下添加children字段即可

```
  routes: [
    {
      path: '/',
      name: 'HelloWorld',
      component: HelloWorld
    },
    {
      path:'/hi',
      name: 'hiPage',
      component:Hi,
      children:[
        {path:'hi1',name:'hi1',component:Hi1},
        {path:'hi2',name:'hi2',component:Hi2},
      ]
    },
  ]
  // <router-link to="/hi/hi1"></router-link>
  // <router-link to="/hi/hi2"></router-link>
  
```

在`Hi.vue`组件中添加`<router-view><router-view>`用于显示子路由内容

### 3.`vue-router`传递参数

方法1路由配置中给给组件使用name属性，通过`$route.name`引用

> `{{$route.name}}`

方法2在`<router-link></router-link>`为to属性添加自定义键值，用`$route.params.xxx`引用

> `<router-link :to="{name:'Hipage',params:{'username':'younguei'}}"></router-link>` 
>
> **注意**：这里的标签没有路径，是***通过name来跳转组件***的，name对应了我们在路由配置中给文件起的name值
>
> `$route.params.username`  获取自定义参数username的值

`$route.params.key`

### 4.`vue-router`利用url传递参数  相对于方法3该方法url传递参数更常用

`{path:'/params/:newsId/:newsTitle'，component:Params}`

`<router-link to="/hi/8888/i love you>Hi</router-link>"`

使用参数: `{{$route.params.newsId}}` `{{$route.params.newsTitle}}`

### 5.单页面多路由区域操作

在一个页面内有多个`<router-view></router-view> `  相当于一个页面内有多个需要路由操作的模块

页面分成了多个路由区域，

在路由的components属性内进行配置

```
components:{
  default: Hello,  //默认区域 即第一个rouer-view区域显示Hello组件
  left: H11,      //left区域显示Hi1组件
  right:Hi2       // right区域显示Hi组件 
}
```

```
<router-view></router-view>
<router-view name="left"></router-view>  //该路由显示区域名称为left
<router-view name="right"></router-view>  //该路由显示区域名称为right
```

完整的写法：

```
export default new Router({
  routes:[
    {
      path:'/home',   //home页面上有三个路由
      name: 'home',
      components:{
        default: Hello,  //三个区块分别渲染 三个组件
        left: H11,     
        right:Hi2 
      }
    }
  ]
})
```

### 6.`vue-router`重定向`redirect`

```
{
  path: '*', //当url输入其它未定的地址的时候，页面跳转到home页面
  redirect: '/home'
}
```

### 7.alias别名的使用 

alias与redirect有相同的重定向效果，具体的还是有些区别

区别: **注意alias是路径的别名，不是组件的别名  `alias:'/other'`**

> alias是给配置文件里的***路径***起一个别名
>
> alias重定向可以改变url中的显示地址，而redirect重定向会跳转到某个页面，地址栏不会改变

小坑：

vue不支持给path为`/`（根目录）起别名，不会跳转到根目录

### 8.路由的过渡动画 `<transition></transition>`

fade-enter 进入过渡的开始状态 瞬间行为

fade-enter-active  进入过渡的结束状态，

fade-leave  离开过渡开始的状态 瞬间行为

fade-leave-active 离开过渡

```
.fade-enter{
  opacity:0;
}
.fade-enter-active{
  transition: opacity 1s;
}
.fade-leave{
  opacity:1;
}
.fade-leave-active{
  opacity:0;
  transition:opacity 1s;
}
```

### 9.路由的mode模式

在路由配置文件添加mode选项`mode:history|hash(默认)`

`history`会将url变为正常的url形式没有多余的 `/#`

`hash`url中会多一个` /#`

```
export default new Router({
  mode:'history',
  routes:[
    ....
  ]
})
```

### 10.路由的钩子函数

**某个路由独享的钩子**： 定义在某个路径内部或某个组件内部

方法1： 在路由文件中配置 (**只能在路由文件中写enter不能写leave**)

> ```
> beforeEnter: (to,from,next)=>{
>   //to 是一个对象，包含要跳转的路径信息
>   //from 是一个对象，包含跳转前页面的路径信息
>   //next() 当少这个函数的时候 不允许跳转 路由的控制参数，常用的有next(true) next(false)
>   // next({path:'/'})，跳转到根目录中
> }
> ```

方法2： 在vue模板文件中配置

```
beforeRouteEnter: (to,from,next)=>{
  console.log("进入");
  next();
},
beforeRouteLeave: (to,from,next)=>{
  console.log("离开");
  next();
}
```

**全局钩子**： 对所有组件都有效果，定义在全局

```
const router = new VueRouter({.....})
router.beforeEach((to,from,next)=>{
  ....
})
```

### 11.编程式导航

`this.$router.go(-1)`

`this.$router.push('/xxx')` 编程式跳转
---
layout: post
title: Vue实战练习1
description: JSpang系列教程
tag: Vue
---

### vue实战1 利用Vue做一个食品订单页面

[参考教程](http://jspang.com/2017/05/22/vuedemo/#9-1)

技术栈：webpack+vue-cli+vue.js+element+axios

### 开始做一个订单demo吧 fighting

#### 1. vue-cli环境搭建

> [搭建教程](https://younguei.github.io/2018/05/vueCli/)

#### 2. 基本布局 

![1](/images/article/vueExercise1-1.PNG)

![成品图](/images/article/vueExercise1-2.PNG)

`lef-nav`用于构建导航栏，特意写了一个组件，用于导航。

`right-div`用于`<router-view>`路由的展示，原本想把该区域分为若干组件，但是做到后期，组件之间的通信又是一个难题，所以目前若有代码都集成在一个组件中。

> (1) 关于组件导出标签名的写法：是驼峰还是中划线？
>
> 使用驼峰：`<leftNav></leftNav>` 因为在局部注册的时候`components:{leftNav}` 不支持中划线写法
>
> `import leftNav from '@/components/common/leftNav'`
>
> (2) 关于样式名称的写法：是驼峰还是中划线？
>
> 使用中划线：`.left-nav`  `.left-nav ul{....}`

#### 3. 页面构建

>  (1)利用axios从`jspang`的网站获取后台数据，在渲染数据的时候犯了一个错误

```
<ul>
	<li v-for="(item,index) in data">{{item.goodsName}}</li>
	//注意这里v-for放在哪里，哪里就会进行渲染，不能放在ul内，这样会渲染出多个ul，
</ul>
```

> (2)`<el-tabs>`卡死问题，项目显示成功运行在8080端口，但是页面无法加载出来，多次尝试后，发现之前代码中存在`v-for`错写在`ul`中的现象，修改后正常运行，但不知道是不是`el-tabs`无法加载的根源，还需多次尝试。
>
> (3)关于axios的使用：
>
> 使用npm安装axios完毕后，只需要在使用到axios的地方引入即可，不需要全局注册
>
> (4)关于`element-ui`使用：
>
> 使用npm安装完毕后，需要全局引入(main.js中引入)，并use

```
import ElementUI from 'element-ui'
import 'element-ui/lib/theme-default/index.css'
Vue.use(ElementUI)
```

####4. 页面功能

> (1) 向购物车内添加商品，若商品不存在，则添加，存在则该商品数量加1，不能重复添加条目

利用了filter方法，filter方法将满足条件的数据以集合的方式返回。

```
//如果存在，则数据加1
let arr = this.orderListTable.filter(item=>item.goodsId === goods.goodsId)//goods为传入的参数
arr[0].count++;// 返回arr是一个对象
```

> (2)删除购物车内的某一条商品

也是利用filter方法，传入待删除的数据，遍历整个数据，将与之不同的数据(不想删除的数据)留下即可

```
this.orderListTable = this.orderListTable.filter(item=>item.goodsId !== goods.goodsId)
```

**遇到的问题**:

> 1. 如何设置div的高度为页面高度，即`height:100%;`
>
>    首先设置`html,body,#app{height:100%;}`
>
> 2. 在element中，代码不明确意思：以下代码`scope="scope"`是什么意思
>
>    ```
>    <el-table-column prop="action" label="操作" fixed="right" align="center">
>      <template scope="scope">
>        <el-button type="text" size="mini" @click="deleteItem(scope.row)">删除</el-button>
>        <el-button type="text" size="mini" @click="getTableList(scope.row)">添加</el-button>
>      </template>
>    </el-table-column>
>    ```
>
>    解决：这是vue作用域插槽的典型，允许使用者如何自定义渲染列表的每一项，但是**scope.row是什么？ 求大神解答** 自我是代表一个一行的数据对象
>
>    在vue2.5后用slot-scope代替了scope
>
>    [参考文档](https://cn.vuejs.org/v2/guide/components-slots.html#%E4%BD%9C%E7%94%A8%E5%9F%9F%E6%8F%92%E6%A7%BD)
>
> 3. `@click="addOrderList(scope.row)"` 还是相同的问题，该怎么解释`scope.row`




---
layout: post
title: Vuex笔记
description: JSpang系列教程
tag: Vue
---

vuex为了大型项目而生，主要是状态管理（状态指的是数据），解决了平级组件之间的数据公用。

### 1.vuex安装

1. 引入vuex
2. 创建vuex文件夹，在其下创建`store.js`用于保存公共数据，文件中引入vue和vuex
3. 在使用vuex `Vue.use(Vuex)`

详细代码:

> store.js文件

```javascript
import Vue from 'vue';
import Vuex from 'vuex';
Vue.use(Vuex);
const state = {
  count:1,
},
const mutations  = {
  add(state){  //第一个参数为默认参数 自动传入
    state.count++;
  },
  reduce(state){
    state.count--;
  }
}
//导出一个vuex对象
export default new Vuex.Store({
  state,
  mutations,
}) 
```

> 组件使用数据

```javascript
<template>
	<div>
		{{$store.state.count}}<br>
		<button @click="add">add</button>
		<button @click="reduce">reduce</button>
	</div>
</template>
<script>
	import store from '../vuex/store.js';
	export default {
	  //注册
      store,
      methods:{
        add(){
          this.$store.commit('add');
        },
        reduce(){
          this.$store.commit('reduce');
        },
      }
	}
</script>
```

### 2. state状态对象

count为共享值，将共享值封装到一个对象中，这个对象称为访问状态对象

```
const state = {
  count = 1,
}
```

**获取共享值的方法**

> 1.利用计算属性: 将`$store.state.count`重新命名  

```
  computed:{
    count(){
      return this.$store.state.count;
    },
  }
```

首先引入mapState对象

> 2.通过mapState的对象来赋值  `computed:mapState({count:state=>state.count})`
>
> 3.通过mapState的数组来赋值  `computed:mapState(["count"])` 将state对象中count属性的值赋值给count变量

### 3. mutations修改状态

在store.js文件中添加mutations属性

```
const mutations = {
  add(state){//state必须要有表示公共参数组成的对象
    state.count++;
  },
};
export default new Vuex.Store({
  state,
  mutations,
})
```

在模板中使用：

```
methods: mapMutations(['add','reduce'])
```

```
<button @click="$store.commit('add')">+</button>//在DOM上触发
```

### 4.getters计算过滤操作

对数据进行一种过滤与加工，可以看作是**在获取数据前对数据进行一种再编辑**

**getters基本用法**：

> 1.在`store.js`中声明getters属性，

```
const getters = {
  count: function(state){
    reutrn state.count += 100;//在每次输出count前加100后再输出
  }
}
```

> 2.在Vuex.Store()中引入getters属性

**在模板中使用**：

> 1.计算属性
>
> 2.利用`import {mapGetters} from 'vuex'`   `...mapGetters(["count"])`　

### 5.actions异步修改状态

actions与mutations功能基本一样，actions是异步操作的，mutations是同步操作的，可以异步执行mutations中的方法

**actions基本用法**:

> 1.在`store.js`中声明actions属性，actions中调用mutation中的方法，实现异步

```
const actions = {
  addAction(context){//context为上下文对象，可以理解为store本身
    context.commit('add',10);//触发add方法
    setTimeout(()=>{context.commit(reduce)},3000);
  }
}
```

**在模板中使用**:

> 1.在methods中使用

```
methods:{
  ...mapActions(['addAction','reduceAction'])
}
```

### 6.module模块组

把我们状态的各种操作进行一个分组，分组后再进行按组编写。

```
consot moduleA ={
  state,mutations,getters,actions
}
export default new Vuex.Store({
  modules:{a:moduleA}
})
```

### 总结

vuex中几个属性：

> 1. state对象：保存公用变量
>
>
> 2. mutations对象：保存操作state中变量的方法
> 3. getters对象：对state中变量进行筛选计算过滤，并输出给使用的组件
> 4. actions对象：对mutations中的方法实现异步操作

导出vuex创建的对象:

```
export default Vuex.Store({
  state,mutations,getters,actions
})
```

在组件中使用:

```
import store from '../vuex/store.js'; //导入自己写的js文件
import {mapState,mapMutations,mapGetters,mapActions} from 'vuex'
export default {
  store,//注册
  computed:{
    ...mapState(['count']),//导出count变量
    ...mapGetters(['count']),//导出计算过滤后的count变量
  },
  methods:{
    ...mapMutations(['add','reduce']),
    ...mapActions(['addAction','reduceAction'])
  }
}
```


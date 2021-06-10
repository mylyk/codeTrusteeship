# Vuex笔记

[TOC]

### 一 简介

Vuex是一个专门为VueJS应用程序开发的**状态管理模式**。它采用**集中式存储方式**管理应用所有组件的状态，并以相应的规则保证状态以一种可以预测方式发生改变。

1. 什么是**状态自管理**，包含一下几个部分，也是最基本的**单向数据流**
   * state 驱动应用程序数据源
   * view 以声明的方式将 state 映射到试图上
   * actions 响应 view 上用户输入导致状态变化
2. 我们可以将组件的共享状态抽离出来，以一个全局单例模式管理，在这种模式下我们组件树构成一个巨大的 “视图” ，不管在树的任何位置，任何组件都可以获取状态或者触发行为；==通过定义和隔离状态管理中的各种概念，并通过强制规则维持视图和状态的独立性，使代码变得**更结构化且易维护**==，这就是 Vuex 背后的基本思想。
3. 什么时候使用Vuex
   * 如果你打算开发单页应用，使用Vuex可能是复杂冗余，但也应用一个简单的**store模式（单向数据流）** 就足够了；
   * 如果是构建一个中大型项目应用，需要考虑如何在组件外部，来更好的管理状态，Vuex就是自然的选择。

![vuex](https://vuex.vuejs.org/vuex.png)

### 二 安装

#### 1. 引入js文件方法

```js
<script src="/path/to/vue.js"></script>
<script src="/path/to/vuex.js"></script>
```

#### 2. NPM 安装方法

```shell
npm install vuex --save
```



### 三 基本使用

> 每一个**Vuex**的核心就是store仓库。**“store”**基本上是一个容器，它包含着你的应用中大部分的 **状态（state）**。

#### Vuex 和 单纯的全局对象有以下两点不同：

1. Vuex 的状态存储是响应式的。当Vuex从 **store** 中读取状态的时候，若 **store** 中的状态发生改变，那么相应的组件也会相应的更新。
2. 你不能直接修改 **store** 中的状态，改变 **store** 中读取状态的唯一途径就是 **提交（commit）mutations** 。这样才能方便我们追踪每一个状态的变化。 



#### 在代码中使用

创建 store 文件夹用来存放 Vuex相关代码，并新建一个 **index.js** 

```js
import Vue from 'vue';
import Vuex from 'vuex';

//组测vuex
Vue.use(Vuex);

//申明store 对象
const store = new Vuex.Store({
  state:{
    count:0
  },
  mutations:{
    increment(state){
      state.count++;
    }
  }
});

//抛出store 对象
export defalut store;
```

然后在  **main.js** 中引入 **store** 

```js
new Vue({
  el:"#app",
  store:store   //也可以使用es6中对象的简写，某个属性名和key名一样时简称成： store
})
```

使用方法是通过  ==$store.state.count== 访问 **状态（state）** 对象，以及通过 ==store.commit== 方法触发状态变更。

```js
 methods: {
  increment() {
    this.$store.commit('increment')
    console.log(this.$store.state.count)
  }
}
```



### 四 Vuex的核心概念

#### state （单一状态树）

> Vuex使用的是单一状态树，用一个对象包裹全部应用层级状态，至此他便成为一个 **“唯一数据源”** ，这也意味着，每个应用仅仅包含一个 **store实例** 。
>
> Vuex中的数据和Vue实例中的 **data** 遵循相同的规则

1. 在Vue组件中获取Vuex状态

   * 由于Vuex存储的是响应式，从 **store** 实例中读取的状态最简单方法就是在 **计算属性（computed）** 中返回某个状态。

2. **mapState** 辅助函数

   * 当一个组件需要获取多个状态的时候，将这些状态都声明为计算属性会有些重复和冗余。为了解决这个问题，我们可以使用 `mapState` 辅助函数帮助我们生成计算属性，让你少按几次键：

   * ```js
     // 在单独构建的版本中辅助函数为 Vuex.mapState
     import { mapState } from 'vuex'
     
     export default {
       // ...
       computed: mapState({
         // 箭头函数可使代码更简练
         count: state => state.count,
     
         // 传字符串参数 'count' 等同于 `state => state.count`
         countAlias: 'count',
     
         // 为了能够使用 `this` 获取局部状态，必须使用常规函数
         countPlusLocalState (state) {
           return state.count + this.localCount
         }
       })
     }
     ```

   * 当映射的计算属性的名称与 state 的子节点名称相同时，我们也可以给 `mapState` 传一个字符串数组。

   * ```js
     computed: mapState([
       // 映射 this.count 为 store.state.count
       'count'
     ])
     ```

     


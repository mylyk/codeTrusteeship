### 一. 计算属性的本质

#### 1.1 计算属性的本质

*   fullName(){ set()  ,  get() }

#### 1.2 计算属性和methods的对比

* 计算属性在多次使用时，只会调用一次
* 它是有缓存的

#### 1.3 监听属性

* watch

### 1.4 过滤器

* filter





### 二 . 事件监听

#### 2.1 事件监听的基本使用

#### 2.2参数问题

* btnClick     省略括号
* btnClick(event)     不省略括号
* btnClick（参数，event）      如果需要事件的event对象，可以在括号里面将event传过去

#### 2.3 修饰符号

* `stop`
* `prevent`
* `.enter` 
* `.once`
* `.navtive`
*  `.exact` 



### 三 . 条件判断

#### 3.1 v-if/v-else   和   v-else-if  

#### 3.2 登陆和邮箱切换的小案例

#### 3.3 v-show

* v-show 和 v-if 的区别

 

### 四. 循环遍历

#### 4.1 遍历数组

#### 4.2 遍历对象

* ```js
  <button v-for='value of Array'></button>
  ```

* ```js
  <button v-for='(value,key) of Array'></button>
  ```

* ```js
  <button v-for='(value,key,index) of Array'></button>
  ```



### 五. 购物车小案例

应用到了`v-for=‘’`  `v-if=''` `v-on:click=''` `methods 方法属性`  `computod  计算属性`    `filters 过滤器`



### 六 . v-model的使用

#### 6.1 v-model的基本使用

* v-model  ==>   v-bind:value   v-on:input

#### 6.2 v-model和 radio / checkbox / select

#### 6.3 修饰符

* `.lazy` 
* `.number` 
* `.trim` 



### 七.  组件化开发

#### 7.1 认识组件化

#### 7.2 组件的基本使用

#### 7.3 全局组件和局部组件

#### 7.4 父组件和子组件

#### 7.5 组件注册的语法糖

#### 7.6 模板的分类写法

* script
* template

#### 7.7 数据的存放

* 子组件不能直接访问父组件
* 子组件中有自己的 data（），而且必须是一个函数
* 为什么必须是一个函数

#### 7.8 父子组件通信

* 父传子：**props**
* 子传父：**this.$emit（'方法名称'，可以放子组件对应参数）** <br>调用的时候直接在父组件中使用  **@[子组件定义方法名] = “设置父组件方法”**   

#### 7.9 gitHub上下载的项目如何跑起来

* `npm install` 
* `npm run server`  

#### 7.10 双向绑定小案例

* 通过 `v-bind:value=''` 和 `v-on:input=‘’` 来实现双向绑定小案例
* 通过 `watch` 监听属性；*watch* 是监听的数据发生改变就会出发 *watch* 事件

#### 7.11 父子之间方法的互相调用

1. **$children** 和 **$refs**  的区别

   *  `this.$children`  返回值是一个数组，获取当前父组件中所有的子组件。

   * `this.$refs`  返回值是一个空对象，获取子组件中定义了 **ref=‘属性名’**的组件，如下：<br>

     ```js
     <comoponentName ref='cpn-name'></comoponentName>
     ```

   * 实际开发中主要以 `$refs` 为主

2. **$parent**  和 **$root**

   * `this.$parent` 返回当前组件的父组件，由于组件复用性非常高，因此包含该方法的组件，在不同的模块中他的父组件并不一定都是上一级，还可能是 **Vue** 实例对象。
   * `this.$root` 直接返回 **Vue** 实例对象

#### 7.11  组件的插槽 slot

1. 简介

   * 组件的插槽是为了让我们组件的封装更具扩展性
   * 可以控制组件的内部内容的展示，也就是抽取组件的共性，保留其中的不同

2. 基本使用

   * 在组件中定义一个 `<slot></slot>` 标签

   * 使用的时候只要在组件掉用的位置编辑组件内不同的内容即可，例如：<br>

     ```html
     <cpn> 这里是插槽接收的内容 </cpn>
     ```

   * 插槽里面也可以放默认值



### 八 . 前端模块化

#### 8.1 模块化基础

* 模块化雏形就是，在匿名函数内部定义对象，将你需要的方法或者属性绑定到这个对象，然后通拓 **return** 将他返回赋值给一个变量，例如<br>

  ```js
  var moduleTest = (function(){
    var obj={};
    var name='lyk';
    function sum(a,b){
      return a+b;
    }
    obj.name=name;
    obj.sum=sum;
    return obj;
  })();
  ```

* 常见的模块化规范有：

  * CommonJS
  * AMD
  * CMD
  * Es6中Module
  
* Es6中的模块化开发（详细请查看Es6学习文档）<br>**注意：** 在Es6中使用模块化开发需要在 `script` 标签中增加 `type='module'` 属性，并且模块化引用需要在http上。

### 九 . webPack

####  经验

*  配置  **node** 的项目需要重新跑一下
* --save 会把依赖包名称添加到 package.json 的 dependencies （依赖性）键下，而 --save-dev 会添加到 devDependencies（开发环境依赖） 键下。
* `--save-dev` 表示开发时依赖

#### 9.1 认识webpack

==webpack 为了正常运行，必须依赖Node环境。== 

* 从本质上来说 **webpack** 是一个现代的 **javaScript** 应用的静态 **模块打包** 工具，简单理解就是 **打包** 和 **模块**
* webpack 和 gulp 的对比
  * **gulp **主要是定义 **task(任务)** 处理，之后让**gulp**来依次执行这些任务，而且让整个流程自动化，所以 **glup** 也被称之为**前端自动任务管理工具**
  * **gulp**强调的是前端流程的自动化，模块化不是它的核心
  * **webpack**更加强调模块化开发管理，而文件压缩合并、预处理等功能，实他的附带功能。

#### 9.2 webpack安装

* 查看你node版本命令 `node -v` 
* 全局安装 ***webpack*** （这里先指定版本号为3.6.0，因为 ***vue CLI*** 依赖该版本）<br>
* `npm install webpack -g` 全局安装

#### 9.3 webpack的起步

* 需要配置 ***webpack.config.js*** 文件，示例如下：<br>

  ```js
  const path=require('path');
  module.exports={
  	entry:'[入口文件路径]',
  	output：{
  		//出口文件
    	path:path.resolve(__dirname,'[出口文件存放文件夹名称]'),
      filename:'[出口文件名称]'
  	}
  };
  ```

* 

#### 9.4 webpack的配置

* 全局安装命令 `npm install webpack@3.6.0 -g`    其中 **-g** ；表示全局安装
* 局部安装 `--save-dev` 是开发时依赖，项目打包后不需要继续使用的
* 初始化 **Node** 仓库：`npm init` ，生成 ***package.js*** 文件
* 查看版本 `webpack -version`  或者 `webpack -v`  

* ***注意：*** 只要是在终端里面输入的 `webpack` 命令他就是全局；只有你用 **package.json** 文件里面的 scripts 定义了其他方法太才会优先调用本地的。

#### 9.5 loder的使用 

* 什么是loader? 
  
  * loader 是webpack中非常核心的概念，用来处理CSS文件
  
* 安装使用步骤（负责解析css）：

  * 官方文档：[loader使用方法](https://www.webpackjs.com/loaders/css-loader/)

  * 安装loader：`npm install --save-dev css-loader`  

  * 在==webpack.config.js== 文件中配置

  * 注意：在安装是会出现应位webpack版本太低或者太高，导致当前的 ***css-loader*** 无法正常编译成功报错可以尝试更换高版本或者低版本试试，报错提示：<Br>

    ```js
    UnhandledPromiseRejectionWarning: TypeError: this.getResolve is not a function
    ```

* 卸载当前版本 `npm uninstall css-loader` 

* 引用Css文件到项目中： `require('../src/normal.css')`

*  负责将css样式应用到Dom节点上：

  * 安装 ***style-loader*** 来配合 ***css-loader*** 一起使用
  
* ==**项目中引入less文件**==

* 处理less文件，安装对应的less编译包<br>`npm install --save-dev less-loader less` 

* 卸载less包：`npm uninstall less-loader less` 

* ==**项目中引入图片**== 

* 安装 ***url-loader*** :  `npm install --save-dev url-loader` 

* 如果图片大小超过默认设置的大小还需要安装 ***file-loader*** <br>`npm install --save-dev file-loader`   并在 ***package.config.js*** 文件中 **output** 属性里面增加公共路径。

#### 9.6 Es6转Es5的配置

* Es6语法处理需要用到 ***babel*** ，在webpack中直接使用对应的 **loader** 就可以了
* 安装（这里的命令是根据当前需求配置，具体更具需求查询文档或者百度）：<br>`npm install --save-dev babel-loader@7 babel-core babel-preset-es2015` 

#### 9.7 webpack中配置Vue

* 安装：`npm install vue` 
* 详细步骤转到 **webpack学习复习章节**

####  9.8 plugin的使用



####   搭建本地服务器







### 十 . Vue CLl(脚手架)



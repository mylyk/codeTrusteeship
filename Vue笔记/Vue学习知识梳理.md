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

> **plugin** : 对某个现有框架的扩展——对现有的webpack打包内容进行扩展，让webpack更好使用。

1. plugin 和 loader 的区别：**loader**  主要用于转换某种类型的模块，它是一个转换器；**plugin** 是插件，他是针对webpack本身的扩充，是一个扩展器。

2. plugin的基本使用：

   * 通过npm安装某需要需要使用的插件（某些*webpack*内置的插件不需要安装）
   * 在*webpack*中的 **webpack.config.js** 文件中配置 *plugin* 插件。

3. 使用内置的**plugin** ，添加版权信息，在 **webpack.config.js** 配置<br>

   ```js
   module.exports={
     plugins:[
       new webpack.BannerPlugin("最终所有版本贵lyk所有")
     ]
   }
   ```

   

4. 打包 html 的 plugin

   * 安装：`npm install html-webpack-plugin --save-dev` 

   * 在 **webpack.config.js** 中配置<br>

     ```js
     const HtmlWebpackPlugin = require("html-webpack-plugin");
     module.exports={
       plugins:[
         new webpack.BannerPlugin("最终所有版本贵lyk所有"),
         new HtmlWebpackPlugin();
       ]
     }
     ```

     配置过*htmlWebpackPlugin* 就可以删除 *output* 属性中的*publicPath*了。

   * 为 *htmlWebpackPlugin* 指定模板，语法：<br>

     ```js
     new HtmlWebpackPlugin({
     	template:'index.html'     //指定一个模板，让他从这模板中加载我们的div
     });
     ```

5. JS 压缩的 *plugin* 

   * 安装：<br>`npm install uglifyjs-webpack-plugin@1.1.1 --save-dev`  

   * 配置<Br>

     ```js
     const UgligyjsWebpack = require('uglifyjs-webpack-plugin');
     
     plugins:[
         new webpack.BannerPlugin("最终所有版本贵lyk所有"),
         new HtmlWebpackPlugin({
           template:'index.html'     //指定一个模板，让他从这模板中加载我们的div
         }),
         new UgligyjsWebpack()
       ]
     ```

   


####   9.9 搭建本地服务器

1. webpack-dev-server 搭建本地服务器

   * 安装：<br>`npm install webpack-dev-server@2.9.1 --save-dev` 

   * 配置：

     ```js
     devServer:{
         contentBase:'./dist',
         inline:true
       }
     ```

     contentBase：为哪一个文件夹提供本地服务，默认是根文件夹

     port：端口号

     inline：页面实时刷新

     historyApiFallback：在SPA页面中，依赖HTML5的history模式。

   * 在 **package.json** 中配置运行命令<br>

     ```js
     "scripts": {
         "test": "echo \"Error: no test specified\" && exit 1",
         "bulid": "webpack",
         "dev":"webpack-dev-server"
       }
     ```

     细节：还可以在 *dev* 里面增加 **- -open** 让它直接在浏览器中打开

     ```js
     "scripts": {
         "test": "echo \"Error: no test specified\" && exit 1",
         "bulid": "webpack",
         "dev":"webpack-dev-server --open"
       }
     ```

     

   * 在命令提示服里面运行服务：`npm run dev` 

2. webpack 配置文件分离，区分哪些配置是开发时依赖，哪些是运行时依赖

   > --save-dev 表示开发依赖（辅助） 
   > 开发时的依赖比如安装 js的压缩包gulp-uglify 因为我们在发布后用不到它，而只是在我们开发才用到它。
   >
   > --save   表示运行依赖（发布）
   > 发布后还需要依赖的模块，譬如像jQuery库或者Angular框架类似的，我们在开发完后后肯定还要依赖它们，否则就运行不了。

   * 安装：`npm install webpack-merge --save-dev` 

   * 用法：

     ```js
     const webpackMerge = require('webpack-merge');    //引入webpack-merge 用来合并配置文件
     const baseConfig = require('./base.config');
     
     module.exports = webpackMerge.merage(baseConfig,{
       devServer:{
         contentBase:'./dist',
         inline:true,
         port:9090
       }
     });
     ```

     ==注意：新的*webpack-merage*返回的是一个对象，也就是**webpackMerge**是一个对象需要调用里面 **merge** 方法来完成打包。== 

     ​			通过 *webpack-marge* 设置完成后，可以删除掉 *webpack.config.js* 默认配置文件；然后再 **package.json** 文件中配置运行时指向的配置文件；语法如下

     ```json
     "scripts": {
         "test": "echo \"Error: no test specified\" && exit 1",
         "bulid": "webpack --config ./bulid/prod.config.js",
         "dev": "webpack-dev-server --open --config ./bulid/dev.config.js"
       }
     ```



### 十 . Vue CLl(脚手架)

#### 10.1  简介

* 使用vue开发大型项目应用时，我们需要考虑代码目录结构、项目结构和部署、热加载、代码单元测试等事情。
* 如果每个项目都要手动完成这些工作，那无疑效率比较低，所以通常我们会使用一些脚手架工具来帮助完成这些事情。
* CLI是什么
  * command-Line Interface , 翻译为命令界面，但是俗称脚手架。
  * Vue CLI 是一个官方发布 Vue.JS 项目脚手架。
  * 使用 Vue-Cli 可以快速搭建 Vue 开发环境以及对应的 webpack 配置。
* 什么是NPM 
  * 全称：Node Package Manage
  * 是一个Node包管理和分发工具



#### 10.2 基本使用

1. 安装Vue 脚手架
   * `npm install -g @vue/cli` 或者 `npm install -g vue-cli` 
   * 查看版本：`vue --version`<br>
   * 上面安装的是Vue CLI3的版本，如果需要按照Vue CLI2的方式初始化项目是不可以的；因此你需要安装 Cli2的模板。
2. 拉取 Cli 2.x 模板
   * 命令：`npm install @vue/cli-init -g` 
   * Cli 2.x 初始化项目：`vue init webpack [my-project项目名称]` 
3. Cli 3.x 
   * 初始化项目：`vue create [myproject项目名称]`



#### 10.3 CLI2 初始化项目过程

1. 安装 **vue2.x** 的模板：`npm install @vue/cli-init -g` 

2. 命令：`vue init webpack [项目的名称]` ；注意项目的名称不能使用中文
   * project name :  [项目名称，不能包含大写]
   * project description：[作者信息，默认会从本地git中读取]
   * vue bulid：[选择vue的模式是runtime compiler或者runtime-only]
   * install vue-router：是否安装vue-router  路由功能
   * use EsLint to lint your code?：是否使用代码格式限制
   * set up unit tests：是否单元测试
   * setup e2e tests with nightwatch？：是否进行 E to E 测试
   * 最后一步选择是用npm开发；还是yarn开发
   
3. VueCli2 目录结构
   * **Build**：项目构建（webpack）相关代码;
   * **config**：配置目录，包括端口号等。
   * **node_modules**：npm加载的项目依赖模块
   * **src**：这个目录当中的内容包含了我们基本上要做的事情，这里包含了几个文件：
     * **assets**：存放图片
     * **components**：存放组件文件
     * **App.vue**：项目入口文件，组件也可以直接写在这里不适用components
     * **main.js**：核心文件
   * **static**：静态资源目录
   * **test**：初始测试目录
   * **.xxxx**：配置文件，包括git配置和语法配置等
   *  **index.html**：首页
   * **package.json**：项目配置文件
   * **README.md**：说明文档
   
4. **runtime-compile ** 和 **runtime-only** 的区别

   * vue compile 程序运行过程：<br>template  —解析—> ast（抽象的语法树abstract syntax tree）—编译—> render渲染（functions）——>vitual dom（虚拟DOM）——>UI（界面上的真实dom）

   * vue only程序运行过程：<br>template  —解析—> render渲染（functions）——> vitual dom（虚拟DOM）——> UI（界面上的真实dom）

   * ```js
     import Vue from 'vue'
     import App from './App'
     
     Vue.config.productionTip = false
     new Vue({
       el: '#app',
       // components: { App },
       // template: '<App/>'
       render(createElement) {
         //普通用法：creatElement("标签"，{标签的属性}，["标签内容"])
         //return createElement('h2',{class:'box'},['hello Vue',createElement('button',['按钮'])]);
         
         //传入一个组件对象
         return createElement(App);
       },
     })
     ```

#### 10.4 Vue CLI3

1. Vue Cli2 和 Vue Cli3 的区别
   1. vue-cli3是基于webpack4打造的，vue-cli3是基于webpack3打造的
   2. vue-cli3的设计原则是 "0配置" ，移除的配置文件根目录下，build 和 config 等目录。
   3. vue-cli3提供了 vue ui 命令，提供了可视化配置，更加人性化。
   4. 移除了 static 文件夹，新增了public 文件夹，并且 index.html 移动到 public 中
2. 创建项目命令：`vue create [项目名称]` 
   * please pick a preset： 选择配置方式
   * check the features needed for project：选择自己需要的配置（空格选中或取消，回车确定）
   * where do you prefer placing config for babel,postcss,eslint,etc：对应的配置单独生成文件还是放在*package.json*文件中，一遍选择生成单独的文件
   * save this as a preset for future projects ：要不要将刚才自己选择配置保存下来。
   * save preset as：设置保存的名称
3. Vue UI（vue配置的图形界面）
   * 启动的命令：vue UI



### 十一. Vue-Router

#### 11.1 认识路由

1. 什么是路由：从一个源数据，将数据分发到指定终端，实现端到端的传输过程。

2. 前端路由和后端路由
   * **后端路由：**一个网页有自己对应的地址，也就是url；url会向服务发送请求，并交个控制器（controller）进行处理，controller 进行各种处理，最后生成 *HTML* 和数据，返回给前端，浏览器（Browser）解析并展示出来。
   * **前端路由：** 涉及到前后端分离，也就是后端只负责提供数据，不负责内容的展示；前端路由主要负责处理我们url和页面资源的映射关系。
   
3. URL的hash

   * URL的hash（哈希）也就是锚点，本质上是改变**windows.location**的**href**属性

   * 我们可以通过直接赋值 **location.hash** 来改变 href，但是页面不会刷新。

   * ```js
     location.hash='lyk'  //lyk
     //结果为：http://localhost:8080/#/lyk
     
     ```

     

4. html5中的 **history** 模式

   * pushstate语法：`history.pushState({},'',url)` <br>

     ```js
     history.pushState({},"","home")  
     //浏览器地址：http://localhost:8080/home
     ```

     该方法类似栈结构（先进后出）可以返回上次路由；也是使用`history.back（）` 方法返回

   * replaceState 语法：`history.replaceState({},"",url )` <br>

     ```js
     history.replaceState({},"",'homes')
     //浏览器地址：http://localhost:8080/homes
     ```

     注意：该方法url是替换，无法点击返回到上次路由

   * go语法：`history,go(-1)`  等同意 `history.back()`    

   * > 补充说明：
     >
     > 1. history.back() 等价于history.go(-1);
     > 2. history.forward()等价于history.go(1)
     > 3. 这仨个方法等同于浏览器界面的前进后退

#### 11.2 vue-router 基本使用

> 目前前端的三大框架都有自己的路由
>
> 1. Angular 的 ngRouter
> 2. React 的 ReactRouter
> 3. Vue 的 Vue-router

1. 认识Vue-router

   * Vue-router 是Vue.js 官方的路由插件，他和Vue是深度集成，适合构建单页面应用。<br>官网地址：https://router.vuejs.org/zh/
   * 路由用于设定访问路径，将路径和组件映射起来。
   * 在Vue-router的单页面应用中，页面的路径改变就是组件的切换。

2. 安装和使用Vue-router

   * 安装命令：`npm install vue-router --save` 
   * 使用步骤：
     * 导入路由对象，并且调用Vue.use(VueRouter)
     * 创建路由实例，并传入路由映射配置
     * 在Vue实例中挂载创建的路由实例
   * 通过 Vue.use(插件)，安装插件：`Vue.use(VueRouter)` 

3. 配置使用

   * 找到router文件夹下面的index.js

   * 如果手动配置，代码如下：<br>

     ```js
     //0.引入相关依赖
     import VueRouter from 'vue-router'
     import Vue from 'vue'
     
     //1.注册Vue.use（插件），安装插件
     Vue.use(VueRouter)
     
     //2.创建VueRouter对象
     const routes=[
       {
         path:'/',
         //redirect 重定向 
         redirect:'/home'
       },{
         path:'/home',
         name:'Home',
         component: Home
       },{
         path:'/about',
      name:'About',
         component:About
       }
     ]
     const router =new VueRouter({
       //配置路由和组件之间的应用关系
       routes
     });
     
     //3.将router对象传入到Vue实例中
     export default router;
     ```
   
   * 使用路由<br>
   
     ```
     <router-link to="/home">首页</router-link>
     <router-link to="/about">首页</router-link>
     <router-view/>
     ```
   
     `<router-view/>` 是内容展示区域
   
4. 路由的默认路径<br>

   ```JS
   {
     path:'/',
     //redirect 重定向 
     redirect:'/home'
   }
   ```

5. 路由修改为 **history** 模式<br>

   ```js
   export default new Router({
     routes,
     mode:'history'
   })
   ```

   在路由的js中增加 *mode* 属性

6. **router-link** 的其他属性补充

   * tag ：指定`router-link` 之后渲染成什么组件；<br>

     ```html
     <router-link to='/home' tag='li'></router-link>
     ```

     上面例子会将 `router-link` 渲染成 li 标签

   * replace ： replace 不会留下 history 记录，所以指定了replace 后网页将无法后退以及返回

   * active-class：当`router-link` 对应的路由匹配成功时，会自动给当前元素设置一个router-link-active的class，设置active-class可以修改默认名称；

     * 在进行高亮显示的导航菜单会使用到该类；
     * 但通常不会修改该类的属性，会直接使用默认的 router-link-active 即可。
     * 统一修改可以在路由里面增加 **linkActiveClass** 属性 

7. 通过代码实现路由跳转

   * 安装了 **router** 后，会往每一个组件里面插入 **$router** 对象 ，同过 **$router** 对象中的方法来修改路由

8. 动态路由使用

   * 在路由配置里，新增的路由后面增加动态路由的参数<br>
   
     ```js
     {
         path:'/user/:userID',    //这里增加了动态路由参数
         component:User
       }
     ```
   
   * 调用时使用 `$route.params.userID[如上定义的用户参数]` 
   
9. 子路由：增加属性 `children` <br>

   ```js
   {
       path:'/home',
       name:'Home',
       component:Home,
       children:[
         {
           path:'user',
           name:'User',
           component:User
         }
       ]
     }
   ```

   

#### 11.3 路由的懒加载 

1. 懒加载，既在使用时才调用相关资源，语法如下：<Br>

   ```JS
   const Home = () => import('../components/home');
   ```

   

#### 11.4 vue-router 嵌套路由

1. 增加属性 `children` 配置新的路由<br>

   ```js
   const routes = [
     {
       path:'/',
       component:Home,
       children:[
         {
           path:'news',
           component:News
         }
       ]
     }
   ]
   ```

   

#### 11.5 vue-router 参数传递

* 传递参数主要有两种类型：**params** 和 **query**
* **params** 类型：
  * 配置路由格式：`/router/:id` 
  * 传递方式：在path后面跟上对应的值
* **query** 类型：
  * 配置路由格式：`/router` 
  * 传递方式：对象中使用 query 的 key 作为传递方式

#### 11.6  *$router* 和 *$route* 的区别

==$router对象是全局路由的实例，是route构造方法的实例，router是VueRouter的一个对象，通过Vue.use(VueRouter)和VueRouter构造函数得到一个router的实例对象，这个对象中是一个全局的对象，他包含了所有的路由包含了许多关键的对象和属性。==

* 所有的组件都集成Vue的原型<Br>参考地址：https://www.jianshu.com/p/758bde4d9c2e

* `$route`对象：.route是一个跳转的路由对象，每一个路由都会有一个route对象，是一个局部的对象，可以获取对应的name,path,params,query等

  * `$route`对象表示当前路由信息，包含了当前URL解析的信息。包含当前路径，参数，query对象。
  *  **$route.path** 字符串，对应当前路由的路径，总是解析为绝对路径
  * **$route.params** 一个 key/value 对象，包含了 动态片段 和 全匹配片段，   如果没有路由参数，就是一个空对象
  * **$route.query**   一个 key/value 对象，表示 URL 查询参数。
  * **$route.hash**   当前路由的hash值 (不带#) ，如果没有 hash 值，则为空字符串。
  * **$route.fullPath**   完成解析后的 URL，包含查询参数和hash的完整路径
  * **$route.matched**   数组，包含当前匹配的路径中所包含的所有片段所对应的配置参数对象。
  * **$route.name**  当前路径名字
  * **$route.meta** 路由元信息

* `$router` 对象   **$router对象是全局路由的实例，是router构造方法的实例。**

  * **路由实例方法：**

    * #### **push** <br>

      ```
      1.字符串this.$router.push('home')
      2. 对象this.$router.push({path:'home'})
      
      3. 命名的路由this.$router.push({name:'user',params:{userId:123}})
      
      4.带查询参数，变成 /register?plan=123this.$router.push({path:'register',query:{plan:'123'}})push方法其实和<router-link :to="...">是等同的。
      ```

    * **go** 页面路由跳转；前进或者后退

    * **replace**  push方法会向 history 栈添加一个新的记录，而replace方法是替换当前的页面，不会向 history 栈添加一个新的记录




#### 11.6 vue-router 导航守卫

* 生命周期函数<br>

  ```js
  //当组件被创建出来时触发
   created() {
     
   },
   //当模板挂载到DOM节点上时触发。
   mounted() {
     
   },
   //当界面上数据更新时触发
   updated() {
     
   },
   activated(){
     
   }
  ```

* ![生命周期函数](https://img2018.cnblogs.com/blog/1449477/201812/1449477-20181205223637098-2100656304.png) 

* Title 显示对应的标题

  * ```js
    router.beforeEach((to,from,next)=>{
      //to:即将进入的目标路由对象
      //from：单签导航即将要离开的路由对象
      //next：调用该方法后，才能进入下一钩子
      //从from跳转到to
      document.title = to.matched[0].meta.title;
    	next();  //必须要调用next方法
    });
    
    const routes = [{
        path:'/about',
        name:'About',
        meta:{
          title:'关于'
        },
        component:About
      }]
    ```

    使用 router.beforeEach 来实现导航守卫；在路由配置里面也需要增加eta 来添加元数据

#### 11.7 keep-alive

1. `router-view` 也是一个组件，如果被包在 `keep-alive` 里面，所有路径匹配的试图组件都会被缓存
2. `keep-alive` 是Vue内置的组件，可以使包含的组件保留状态，或避免重新渲染；他有两个重要的属性
   * include：字符串或正则表达式，只有匹配的组件才会被创建
   * exclude：字符串或正则表达式，任何匹配的组件都不会被缓存

#### 11.8  路径起别名

* 为了方便代码的书写和阅读，我们可以给文件路径起别名

* 在 *webpack.base.conf.js* 文件中修改配置如下：<br>

  ```js
  resolve: {
      extensions: ['.js', '.vue', '.json'],
      alias: {
        '@': resolve('src'),
        'assets': resolve('src/assets'),
        'components': resolve('src/components'),
        'views': resolve('src/views')
      }
    }
  ```

  ==注意：==在html路径中使用别面需要使用 "~" 符号，示例代码如下：<br>

  ```html
  <tab-bar-item path='/home'>
    <img slot='item-img' src="~assets/img/tabbar/home.svg" />
    <img slot='item-img-active' src="~assets/img/tabbar/home_active.svg" />
    <div slot='item-text'>首页</div>
  </tab-bar-item>
  ```

#### 11.9 拓展 . Promise

* Promise 是异步编程的一种解决方案。
* 异步操作一般有三种状态：
  * pending：等待状态
  * fulfill：满足状态，当我们主动调用 resolve 时，就处于满足状态，并且回调.then()
  * reject：拒绝状态

#### 11.10 Cli3中自定义配置

> 在CLI3中所有的脚手架配置都放到 `node_modules` 文件夹中的@vue中，因此你自定义的配置需要在当前项目中新建文件`vue.config.js` 文件，在其中配置

1. 端口号配置<br>

   ```js
   module.exports = {
     devServer: {
       // 项目运行时候的端口号
       port: 2020
     }
   };
   ```

   

2. 文件别名配置<br>

   ```js
   configureWebpack:{
       resolve:{
         alias:{
           'css':'@/assets/css',
           'img':'@/assets/img',
           'common':'@/common',
           'components':'@/components',
           'view':'@/view',
           'network':'@/network',
         }
       }
     }
   ```

   



### 十二 . VueX

#### 12.1 Vuex的简介

* 每一个 Vuex 应用的核心就是 store（仓库）。“store”基本上就是一个容器，它包含着你的应用中大部分的**状态 (state)**。

* VueX 是一个转为Vue.js应用程序开发的**状态管理模式**。
  * 他采用 **集中式存储管理** 应用的所有组件状态，并以相应的规则状态以一种可预测的方式发生改变。
* 什么是**状态管理** 
  * 状态管理模式，集中式存储管理简单理解为把需要多个组件的变量共享全部存储到一个对象里面。将这个对象放到Vue实例的顶层，供其他组件使用
  * **state**，驱动应用的数据源；
  * **view**，以声明方式将 **state** 映射到视图；
  * **actions**，响应在 **view** 上的用户输入导致的状态变化。
  * 以下是一个表示“单向数据流”理念的简单示意：
  * ![什么是“状态管理模式”](https://vuex.vuejs.org/flow.png)
  * ![Vuex的模式](https://vuex.vuejs.org/vuex.png) 
* Vuex 和单纯的全局对象有以下两点不同：
  * Vuex 的状态存储是响应式的。当 Vue 组件从 store 中读取状态的时候，若 store 中的状态发生变化，那么相应的组件也会相应地得到高效更新
  * 你不能直接改变 store 中的状态。改变 store 中的状态的唯一途径就是显式地**提交 (commit) mutation**。这样使得我们可以方便地跟踪每一个状态的变化，从而让我们能够实现一些工具帮助我们更好地了解我们的应用



#### 12.2 Vuex的安装

1. 安装 Vuex ：`npm install vuex --save` 

2. 引用插件：`Vue.use（插件名）` 

3. vuex组件在APP.js种引用后，vue种将会有一个全局对象`$store` 

4. Vuex基础使用<br>

   ```js
   import Vue from 'vue'
   import Vuex from 'vuex'
   
   //注册组件
   Vue.use(Vuex);
   
   //创建组件对象
   const store = new Vuex.Store({
     state:{
       //定义相关公共的属性和对象
       count:100
     },
     mutations:{
       //定义相关方法的;每个方法默认都有一个state参数
       increment(state){
         return state.count++;
       },
       decrement(state){
         return state.count--;
       }
     }
   });
   
   //对外抛出定义对象
   export default store;
   ```

   

5. Vuex里面的核心概念
   * State：单一状态树
   
   * Getters：可以认为是 **Vuex** 的计算属性。就像计算属性一样，getter的返回值会根据它的依赖被缓存起来，只有当值发生改变才会被重新计算；启动被定义的方法也会默认传入一个 **state** 形参。
   
   * Mutation：可以理解为事件和方法，且每一个方法也有一个state形参
     * mutation 中进行并记录的都是同步操作，无法记录异步操作。
     * 每个Mutation都有一个字符串**事件类型**（type）
     * **回调函数**
     * mutation需要遵守Vue的响应规则：
       1. 最好提前定义在 store 中并初始化好所有的属性。
       2. 当需要在对象上添加新属性时，你需要`Vue.set(Obj,'[key]','[value]')` 
       3. 删除对象是也要使用`Vue.delete(target,key)` 
     
   * Action：它类似于 **Mutation** ，不同在于 **Action** 中处理的都是异步操作，语法格式：<br>
   
     ```js
     this.$store.dispatch();
     ```
   
   * Module：Vuex 允许我们将 store 分割成**模块（module）** ，每个模块拥有自己的 state、mutation、action、getter、甚至是嵌套子模块——从上至下进行同样方式的分割。
   
     * 对于模块内部的 action，局部状态通过 `context.state` 暴露出来，根节点状态则为 `context.rootState` 
   
       ```js
       sumWithRootCount (state, getters, rootState) {
         		//根节点会作为第三个参数暴露出来
             return state.count + rootState.count
           }
       ```
   
6. 项目结构 （Vuex 并不限制你的代码结构。但是，它规定了一些需要遵守的规则：）

   1. 应用层级的状态应该集中到单个 store 对象中。

   2. 提交 **mutation** 是更改状态的唯一方法，并且这个过程是同步的。

   3. 异步逻辑都应该封装到 **action** 里面

   4. 示意图：<br>

      ```js
      ├── index.html
      ├── main.js
      ├── api
      │   └── ... # 抽取出API请求
      ├── components
      │   ├── App.vue
      │   └── ...
      └── store
          ├── index.js          # 我们组装模块并导出 store 的地方
          ├── actions.js        # 根级别的 action
          ├── mutations.js      # 根级别的 mutation
          └── modules
              ├── cart.js       # 购物车模块
              └── products.js   # 产品模块
      ```

      



### 十三 . 网络请求的封装（axios）

#### 13.1 官方网站（http://www.axios-js.com/zh-cn/）

* 简介：Axios 是一个基于 promise 的 HTTP 库，可以用在浏览器和 node.js 中。

#### 13 .2 基本使用

1. 安装：`npm install axios --save` 

2. 基本使用<br>

   ```js
   //直接引用
   import axios from 'axios'
   ```

   

3. axios的基本框架<br>

   ```js
   axios({
     url:'请求的地址',
     method:'get/post'   //声明网络请求的方式是get还是post
   }).then(res=>{
     console.log(res);
   })
   ```
   
   
   
4. 携带参数的请求<br>

   ```js
   axios({
     url:'请求的地址',
    	//params是专门针对get请求的参数拼接
     params:{
       //参数名：‘参数’
     },
     //data是专门针对post请求的参数传递
     data:{
       //参数名:'参数'
     }
   }).then(res=>{
     console.log(res);
   })
   ```

   其中**params**是针对**get**的参数传递；**data**是针对与post的参数传递。其中在post传递参数时使用data时需要用的qs库将data的参数转换为'字符串数据'。

   

#### 13.3 并发请求

* 发送并发请求：**axios.all()** 返回结果是一个数组，使用 **axios.spread()** 可将返回结果数组拆分开来<br>

  ```js
  //基本语法
  axios.defaults.baseURL='http://123.207.32.32:8000';
  axios.all([
    axios({
      url:'/home/multidata'
    }),
    axios({
      url:'/home/data',
      params:{
        type:'sell',
        page:5
      }
    }),
    axios({
      url:'/category'
    })
  ]).then(res1=>{
    console.log(res1);
  })
  
  
  //使用axios.spread()
  axios.all([
    axios({
      url:'http://123.207.32.32:8000/home/multidata'
    }),
    axios({
      url:'http://123.207.32.32:8000/home/data',
      params:{
        type:'sell',
        page:2
      }
    })
  ]).then(axios.spread((result1,result2)=>{
    console.log(result1);
    console.log(result2);
  }))
  ```



#### 13.4 全局配置

* 给axios中设置全局/公共的配置（或者叫默认值）<br>

  ```js
  axios.defaults.baseURL='公共的请求路径'
  ```



#### 13.5 创建实例和模块封装

1. 创建实例<br>

   ```js
   //创建实例
   const instance1=axios.create({
     baseURL:'http://123.207.32.32:8000',
     timeout:5000   //设置请求时间不超过多少毫秒
   })
   //使用实例
   instance1({
     url:'/home/data'
   }).then((result)=>{
     console.log('地址1成功结果如下：');
     console.log(result)
   }).catch((err)=>{
     console.log('请求地址有误');
   })
   
   const instance2=axios.create({
     baseURL:'http://123.207.32.32:8000',
     timeout:1000   //设置请求时间不超过多少毫秒
   })
   instance2({
     url:'/home/multidata'
   }).then((result)=>{
     console.log('地址2成功结果如下：');
     console.log(result)
   }).catch((err)=>{
     console.log('请求地址有误');
   })
   
   ```

   

2. 模块封装

   1. 新建文件夹 **network** ，新建文件 **request.js（名称可以自己定义）** 

   2. 封装 **axios** <br>

      ```js
      import axios from 'axios'
      export function request(config,success,error){
        //创建axios实例
        const instance = axios.create({
          baseURL:'公共请求路径地址'
          // 其他参数
        })
        instance(config).then(res=>{
          //结果不能再封装模块中处理要将结果反馈出去
          //方法1.传过来一个方法，通过回调函数的方法将结果返回去
          console.log(res);
          success(res)
        }).catch(err=>{
          //结果不能再封装模块中处理要将结果反馈出去
          console.log(err);
          error(err)
        })
      }
      
      //方法2.由于axios.create是基于promise 的http库，可以在外面调用时直接通过then和catch来获取结果

        //创建实例
        const instance = axios.create({
          baseURL:"http://123.207.32.32:8000"
        })
        //直接将instance 抛出，因为axios.create创建的就是一个promise
        return instance(config);
      ```
      
      

#### 13.6 拦截器

1. axios提供的拦截器，用于我们每次发送请求或者响应后，进行相应的处理。

2. 请求的拦截器<br>

   ```js
   //创建一个实例
   const instance = axios.create({
     baseURL:"http://123.207.32.32:8000"
   });
   
   // 添加请求拦截器
   instance.interceptors.request.use(function (config) {
     // 在发送请求之前做些什么
     return config;
   }, function (error) {
     // 对请求错误做些什么
     return Promise.reject(error);
   });
   // 添加响应拦截器
   axios.interceptors.response.use(function (response) {
       // 对响应数据做点什么
       return response;
     }, function (error) {
       // 对响应错误做点什么
       return Promise.reject(error);
     });
   ```

   注意：不管是响应拦截还是请求拦截，都必须拦截结果**return**出去，否则响应/请求会一直停在拦截器哪里，不进行下一步。



### 十四 .  Element-UI学习

#### 14.1  基本使用

1. VueCli3安装：`npm install element-ui -S`  或者 `npm install element-ui --save` 

2. 在 `mian.js` 文件中引入<br>

   ```js
   import ElementUI from 'element-ui'
   import 'element-ui/lib/theme-chalk/index.css'
   Vue.use(ElementUI)
   ```

   

3. 示例代码<br>

   ```vue
   <div class="block">
     <span class="demonstration">默认不区分颜色</span>
       <el-rate v-model="value1"></el-rate>
     </div>
     <div class="block">
       <span class="demonstration">区分颜色</span>
       <el-rate v-model="value2" :colors="colors"></el-rate>
     </div>
   </div>
   <script>
     data(){
       return {
         value1: null,
         value2: null,
         colors: ["#99A9BF", "#F7BA2A", "#FF9900"]
       }
     }
   </script>
   ```

   


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


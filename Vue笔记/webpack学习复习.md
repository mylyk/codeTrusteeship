### 一 . webpack学习总结回顾

==注意：== 

1. webpack 4x以上，webpack将命令相关的内容都放到了webpack-cli，所以还需要安装webpack-cli；<br>`npm install --global webpack-cli` 

#### 1.1 安装使用

1. webpack的安装 
   * 全局安装：`npm install webpack -g`   或者  `npm install webpack@3.6.0 -g` 
   * 开发时依赖项目中安装：`npm install webpack --save-dev` <br> 或者 `npm install webpack@3.6.0 --save-dev` 
   
2. 编写模化的代码，使用最基本的命令来打包文件<br>`webpack [入口文件路径] [输出文件路径]` 

3. 以上这种命令方法过于冗长，我们通过webpack配置文件来简化和易懂我们命令

   * 在当前目录下创建*webpack*配置文件，文件名必须为 **webpack.config.js** ,基础配置如下：<br>

     ```js
     //使用node的path包
     const path=require('path');
     
     module.exports={
       entry:'./src/js/main.js',   //入口文件路径
       output:{
         //出口文件路径
         path:path.resolve(__dirname,'dist/js'),       //此处必须是文件的绝对路径,此处需要用到 nodejs 中的path包
         filename:'bundle.js'
       }
     }
     ```

   * 在以上配置文件编写过程中，*output* 输入文件路径必须是绝对路径，因此需要用到 **NodeJS** z中 *path* 包；使用 *path* 包之前需要初始化当前文件夹 `npm init` 来初始化当前文件夹，初始化完成后会生成一个 *package.json* 的配置文件。

   * **配置完成后输入 `webpack` 命令将会给我们自动打包文件** 

4. 真实开发中我们一把不是使用 `webpack` 命令来打包文件，而是使用 `npm run bulid` 或者其他命令来执行的我们的打包操作；因此需要修改 ***package.json*** 文件，如下：<br>

   ```json
   {
     "name": "demowebpack",
     "version": "1.0.0",
     "description": "",
     "main": "webpack.config.js",
     "scripts": {
       "test": "echo \"Error: no test specified\" && exit 1",
       "bulid":"webpack"
     },
     "author": "",
     "license": "ISC"
   }
   
   ```

   在配置文件中 *scripts* 属性中自定义你需要命令名称，如下定义了 **bulid** ，后面跟上你要执行的命令；*scripts* 中的指令会优先执行本地的webpack。

   > ​			注意：在命令行中直接输入 **webpack** 都是全局，每个项目都有根据当前项目的需要而安装特定的版本，因此都需要用到本地webpack，就是*运行时依赖* ，命令[接上面开发时依赖命令]。



#### 1.2 打包CSS文件

1. 需要使用 *loader* 让我们 **webpack** 来打包处理我们CSS文件。

2. 安装 **css-loader** ，让 *webpack* 解析css；<br>**注意：**==使用多个loader是文件读取顺序是从右往左，因此需要先写css-loader再写style-loader==

   * 命令：`webpack install css-loader@2.0.2 --svae-dev` 

   * 在 **webpack.config.js** 文件中配置，如下：<br>

     ```js
     //使用node的path包
     const path=require('path');
     
     module.exports={
       entry:'./src/js/main.js',   //入口文件路径
       output:{
         //出口文件路径
         path:path.resolve(__dirname,'dist/js'),       //此处必须是文件的绝对路径,此处需要用到 nodejs 中的path包
         filename:'bundle.js'
       },
       module: {
         rules: [
           {
             test: /\.css$/,
             use: ['css-loader' ]
           }
         ]
       }
     }
     ```

   * webpack 编译CSS完成后需要将样式添加到 **DOM** 中，还需要安装我们的 **style-loader** ，安装步骤与 **css-loader** 一样，安装完成后也需要配置。

3. 将编译的css样式渲染到dom节点上需要安装 **style-loader** ：<br>`npm install style-loader --save-dev` 



#### 1.4 打包图片

1. 对图片类的文件打包需要使用 **url-loader** : `npm install url-loader --save-dav` 

2. 安装完后在  **webpack.config.js** 文件中配置即可<br>

   ```js
   {
     test: /\.(png|jpg|gif)$/,
     use: [
       {
         loader: 'url-loader',
         options: {
           limit: 8192    //图片小于定义大小，会将图片转成base64
         }
       }
     ]
   }
   ```

   

3. 如果图片操作默认设置的大小，还需要安装使用 **file-loader** <br>`npm install --save-dev file-loader` 并在 **package.config.js** 文件，output属性里面增加公共路径。

4. 超过图片设置大小后，会将图片转换成*Base64*来显示，转换成 *base64* 页面会提示找不到图片文件路径，这是需要配置公共路径 **publicPath**；<br>

   ```js
   entry:'./src/js/main.js',   //入口文件路径
     output:{
       //出口文件路径
       path:path.resolve(__dirname,'dist/js'),       //此处必须是文件的绝对路径,此处需要用到 nodejs 中的path包
       filename:'bundle.js',
       publicPath:'./dist/js/'
     },
   ```

   

5. 图片文件处理-修改文件名

   * 为了防止图片名称为一长串哈希值，可以通过 *url-loader* 配置 **option** 添加如下选项：<br>

     ```js
     {
       test: /\.(png|jpg|gif)$/,
       use: [
         {
           loader: 'url-loader',
           options: {
             limit: 8192,    //图片小于定义大小，会将图片转成base64
             name:"image/[name].[hash:8].[ext]"
           }
         }
       ]
     }
     ```

     > 参数：<br>1. image：文件打包到的文件夹，
     >
     > 2.name：获取图片远来的名字放在该位置
     >
     > 3.hash:8：截取哈希名称的长度
     >
     > 4.ext：原文件的扩展名



#### 1.5 将代码中用到Es6的内容打包成ES5

***注意：以下步骤基于学习教程中使用，具体打包方法更具项目选择对应版本和方法***

1. 安装：`npm install --sava-dev babel-loader@7 babel-core babel-preset-es2015` 

2. 修改配置文件<br>

   ```js
   {
     test: /\.js$/,
     //exclude  排除   include  包含
     exclude: /(node_modules|bower_components)/,
     use: {
       loader: 'babel-loader',
       options: {
         presets: ['es2015']
       }
     }
   }
   ```

   如果出现报错：*ERROR in Entry module not found: Error: Can't resolve 'babel-loader' in…*，运行：<br>`cnpm install babel-loader@7 --save-dev` 

 

#### 1.6 webpack中配置Vue

1. 安装（因为我们后续在实际项目中也会使用vue，所以此处并不是开发是伊依赖）<br>`npm install vue -save` 

2. Vue的三种使用方法
   * 下载 *vue.js* 文件引用使用
   * CDN应用使用
   * npm 安装使用：将vue当作一个模块来使用
   
3. vue初期开发时模式分为两种：
   * runtime-only  代码中，不可以有任何的*template* 
   * runtime-compiler 
   
4. 在 *webpack.config.js* 文件增加 **resolve** 属性：<br>

   ```js
   resolve:{
       //alias 别名
       alias:{
         'vue$':'vue/dist/vue.esm.js'
       }
     }
   ```

   

#### 1.7  vue中 template 和 el 

> SPA  单页面复应用，多页面跳转时通过（vue-router）前端路由实现

1. el 和 template 的区别

   * 之前我们定义的Vue实例中，我们定义了el属性，用于和index.html中的*#app* 进行绑定，让Vue实例之后可以管理它其中的内容

   * 这里，我们可以将DIV元素中的 *{{message}}* 内容删掉，只保留一个基本的有ID的div元素

   * 如果我们希望在其中显示*{{message}}* 的内容，我们可以在定义一个 **template** 属性<br>

     ```js
     new Vue({
       el:'#app',
       template:`
       <h3>{{message}}</h3>
       `,
       data:{
         message:'这是通过webpack打包的vue模块展示出阿来'
       }
     });
     ```

     **注意：**当代码中有 **el** 和 **template** 会将 **template** 中的内容替换到，HTML中的 *el* 指向的元素位置。

2. webpack 中 ***.vue*** 后缀文件的处理

   * 安装 `vue-loader` 和  `vue-template-compiler` <br>`npm install vue-loader vue-template-compiler --save-dev` 

   * 修改配置文件<br>

     ```js
     {
       test:/\.vue$/,
       use:['vue-loader']
     }
     ```

     **注意：** 这样运行后会报错：*vue-loader was used without the ….* ，在配置文件中修改 **vue-loader** 的版本后在执行 `npm install` 重新跑一下 **node** 他会自动安装我们刚才在配置文件中修改的版本。


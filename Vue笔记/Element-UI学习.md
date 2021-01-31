### 一 快速上手

#### 1.1 基本使用

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

   


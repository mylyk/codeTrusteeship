### 一 	创建Vue实例

1. 创建实例<br>

   ```js
   const vm = new Vue({
     el:"#app",
     data:{
       message:"hello VUE"
     }
   });
   ```

   Vue采用的 **MVVM** （Module View ViewModule）模型

2. 数据绑定<br>

   ```js
   data:{
   
   }
   ```

   

3. 生命周期图<br>

![Vue 实例生命周期](https://cn.vuejs.org/images/lifecycle.png)



### 二	模板语法

1. 数据绑定最常用的形式就是使用"Mustache"语法（双大括号）的文本插值；<br>

   ```html
   <span>{{message}}</span>
   ```

2. 显示原始HTML<br>

   ```html
   <span v-html="rawHtml"></span>
   ```

3. 修饰符

   * 修饰符 (modifier) 是以半角句号 `.` 指明的特殊后缀，用于指出一个指令应该以特殊方式绑定。例如，`.prevent` 修饰符告诉 `v-on` 指令对于触发的事件调用 `event.preventDefault()` 

4. 缩写

   * `v-bind` 缩写<br>

     ```html
     <!-- 完整语法 -->
     <a v-bind:href="url">...</a>
     
     <!-- 缩写 -->
     <a :href="url">...</a>
     ```

     

   * `v-on` 缩写：<br>

     ```html
     <!-- 完整语法 -->
     <a v-on:click="doSomething">...</a>
     
     <!-- 缩写 -->
     <a @click="doSomething">...</a>
     ```



### 三	计算属性——监听器——方法

1. 计算属性（computed）和方法（method）区别
   * 在处理结果上两者完成一样
   * 不同点
     * 计算属性（computed）是基于他们的相应式依赖进行缓存的，只有在相关响应式依赖发生改变的时候才会重新求值，返回处理结果，且不会执行函数。
     * 方法（method），没事触发重新渲染是，调用方法将会再次执行函数
   * 对于任何复杂的逻辑，你都可以采用计算属性；可以理解为计算属性有缓存，当值发生改变时不需要每次都调用函数。
2. 监听属性（watch）
   * Vue提供了一种通用的方法来观察和相应*Vue*实例上的变动：**监听属性**。



### 四	Class 与 style 绑定

#### 4.1 绑定 HTML  Class

* 对象语法

  * `v-bind:class` 可以穿一个对象<br>

    ```html
    demo1
    <div v-bind:class="{ active: isActive }"></div>
    
    demo2
    <div v-bind:class="classObject"></div>
    data: {
      classObject: {
        active: true,
        'text-danger': false
      }
    }
    ```
* 数组语法

  * `v-bind:class` 穿一个数组过去<br>

    ```html
    <div v-bind:class="[activeClass, errorClass]"></div>
    data: {
      activeClass: 'active',
      errorClass: 'text-danger'
    }
    ```

    其中也可以采用三元表达式：

    ```html
    <div v-bind:class="[isActive ? activeClass : '', errorClass]"></div>
    ```

#### 4.2  绑定内联样式

* 对象语法

  * `v-bind:style` 的对象语法十分直观——看着非常像 CSS，但其实是一个 JavaScript 对象。CSS property 名可以用驼峰式 (camelCase) 或短横线分隔 (kebab-case，记得用引号括起来) 来命名：<br>

    ```html
    <div v-bind:style="{ color: activeColor, fontSize: fontSize + 'px' }"></div>
    
    ```
<div v-bind:style="styleObject"></div>
    data: {
      styleObject: {
        color: 'red',
        fontSize: '13px'
      }
    }
    ```


​    

* 数组语法

  * `v-bind:style` 的数组语法可以将多个样式对象应用到同一个元素上：<br>

    ```html
    <div v-bind:style="[font, backgroud]"></div>
    data:{
      font:{
        fontSize:'13px'
      },
      backgroud:{
        backgroundColor:"yellow"
      }
    }
    ```



### 五	条件渲染

#### 5.1 v-if

* `v-if` 用于判断条件性渲染一块内容；也可以添加 `v-else` 块 <br>

  ```html
  <h1 v-if="awesome">Vue is awesome!</h1>
  <h1 v-else>Oh no 😢</h1>
  ```

  

* 如果切换多个元素可以放到 **template** 元素上使用 `v-if` 条件渲染分组<br>

  ```js
  <template v-if="ok">
    <h1>Title</h1>
    <p>Paragraph 1</p>
    <p>Paragraph 2</p>
  </template>
  ```

  

* `v-if-else` 

  * 充当 **v-if** 块可以连续使用<br>

    ```html
    <div v-if="type === 'A'">
      A
    </div>
    <div v-else-if="type === 'B'">
      B
    </div>
    <div v-else-if="type === 'C'">
      C
    </div>
    <div v-else>
      Not A/B/C
    </div>
    ```



#### 5.2 用 **key** 管理可复用的元素

* 用于解决元素切换后带有上次输入数据的问题，可以在元素中增 `key` 属性来避免该问题的发生。例子：<br>

  ```html
  <template v-if="loginType === 'username'">
    <label>Username</label>
    <input placeholder="Enter your username" key="username-input">
  </template>
  <template v-else>
    <label>Email</label>
    <input placeholder="Enter your email address" key="email-input">
  </template>
  ```

  这样每次切换表格框其中的内容都会被重新渲染。



####  5.3 v-show

* 用于更具条件展示元素的选项。实例：<br>

  ```html
  <h1 v-show="ok">Hello!</h1>
  ```

  

* 带有 `v-show` 的元素始终会被渲染并保留在DOM中；`v-show` 只是简单地切换元素的 css property display

* ==注意：`v-show `不支持 <template> 元素，也不支持 `v-else`。== 

 

#### 5.4 v-if 和 v-show 的区别

* **v-if** 是真正的条件渲染，因为它会确保在切换过程中条件块内的事件监听器和子组件适当地被销毁和重建。
* **v-if** 也是***惰性的*** ：如果在初始渲染时条件为假，则什么也不做——直到条件第一次变为真时，才会开始渲染条件块。
* `v-show` 就简单得多——不管初始条件是什么，元素总是会被渲染，并且只是简单地基于 CSS 进行切换。
* 一般来说，`v-if` 有更高的切换开销，而 `v-show` 有更高的初始渲染开销。因此，如果需要非常频繁地切换，则使用 `v-show` 较好；如果在运行时条件很少改变，则使用 `v-if` 较好。



#### 5.5 v-for 



> 注意：当 `v-if` 与 `v-for` 一起使用时，`v-for` 具有比 `v-if` 更高的优先级。

* `v-for` 指令基于一个数组来渲染一个列表。`v-for` 指令需要使用 `item in items` 形式的特殊语法，其中 `items` 是源数据数组，而 `item` 则是被迭代的数组元素的**别名**。<br>

  ```html
  <ul id="example-1">
    <li v-for="item in items" :key="item.message">
      {{ item.message }}
    </li>
  </ul>
  var example1 = new Vue({
    el: '#example-1',
    data: {
      items: [
        { message: 'Foo' },
        { message: 'Bar' }
      ]
    }
  })
  ```

  

* **v-for** 还支持第二个参数 index，例如：<br>

  ```html
  <li v-for="(item, index) in items"></li>
  ```

  

#### 5.6 数组更新检测

1. 数组处理方法
   * **push()**
   * **pop()**
   * **shift()**
   * **splice()**
   * **sort()** 
   * **reverse()** 



### 六	事件处理

#### 6.1 监听事件

* *v-on* 指令来监听DOM事件。
* 将事件定在 **methods** 方法中
* 


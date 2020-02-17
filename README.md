# Vue

  1. 前言
    
    > 静态页面
    - 最初的网页以HTML为主，是纯静态的网页。网页是只读的，信息流只能从服务的到客户端单向流通。**开发人员也只关心页面的样式和内容**即可。

    > 异步刷新，操作DOM
    - 1995年，网景工程师Brendan Eich 花了10天时间设计了JavaScript语言.
      随着JavaScript的诞生，我们可以操作页面的DOM元素及样式，页面有了一些动态的效果，但是依然是以静态为主。
    - ajax盛行：
      - 2005年开始，ajax逐渐被前端开发人员所重视，因为不用刷新页面就可以更新页面的数据和渲染效果。
      - 此时的**开发人员不仅仅要编写HTML样式，还要懂ajax与后端交互，然后通过JS操作Dom元素来实现页面动态效果**。比较流行的框架如Jquery就是典型代       表。

    > MVVM，关注模型和视图
    - 2008年，google的Chrome发布，随后就以极快的速度占领市场，超过IE成为浏览器市场的主导者。
    - 2009年，Ryan Dahl在谷歌的Chrome V8引擎基础上，打造了基于事件循环的异步IO框架：Node.js。
      - 基于时间循环的异步IO
      - 单线程运行，避免多线程的变量同步问题
      - JS可以编写后台diamante，前后台统一编程语言

    - node.js的伟大之处不在于让JS迈向了后端开发，而是构建了一个庞大的生态系统。
    - 2010年，NPM作为node.js的包管理系统首次发布，开发人员可以遵循Common.js规范来编写Node.js模块，然后发布到NPM上供其他开发人员使用。目前已经是世     界最大的包模块管理系统。
    
  2. MVVM模式
  
    - M：即Model，模型，包括数据和一些基本操作
    - V：即View，视图，页面渲染结果
    - VM：即View-Model，模型与视图间的双向操作（无需开发人员干涉）

    在MVVM之前，开发人员从后端获取需要的数据模型，然后要通过DOM操作Model渲染到View中。而后当用户操作视图，我们还需要通过DOM获取View中的数据，然后同     步到Model中。

    而MVVM中的VM要做的事情就是把DOM操作完全封装起来，开发人员不用再关心Model和View之间是如何互相影响的：
    - 只要我们Model发生了改变，View上自然就会表现出来。
    - 当用户修改了View，Model中的数据也会跟着改变。
  
  3. 认识Vue

    Vue (读音 /vjuː/，类似于 **view**) 是一套用于构建用户界面的**渐进式框架**。与其它大型框架不同的是，Vue 被设计为可以自底向上逐层应用。Vue 的核  心库只关注视图层，不仅易于上手，还便于与第三方库或既有项目整合。另一方面，当与[现代化的工具链(https://cn.vuejs.org/v2/guide/single-file-components.html)以及各种[支持类库](https://github.com/vuejs/awesome-vue#libraries--plugins)结合使用时，Vue 也完全能够为复杂的单页应用提供驱动。

    ​	前端框架三巨头：Vue.js、React.js、AngularJS，vue.js以期轻量易用著称，vue.js和React.js发展速度最快，AngularJS还是老大。

    官网：https://cn.vuejs.org/
    参考：https://cn.vuejs.org/v2/guide/
    Git地址：https://github.com/vuejs
    **尤雨溪**，Vue.js 创作者，Vue Technology创始人，致力于Vue的研究开发。
  
4. Node和NPM

    NPM是Node提供的模块管理工具，可以非常方便的下载安装很多前端框架，包括Jquery、AngularJS、VueJs都有。为了方便，先安装node及NPM工具。
    
  4.1 下载Node.js

    下载地址：[https://nodejs.org/en/download/](https://nodejs.org/en/download/)
    推荐下载LTS版本
    下一步安装即可,完成以后，在控制台输入：node -v
    
  4.2 NPM

    安装完成Node应该自带了NPM了，在控制台输入`npm -v`查看
    npm默认的仓库地址是在国外网站，速度较慢，建议大家设置到阿里镜像。但是切换镜像是比较麻烦的。推荐一款切换镜像的工具：nrm
    我们首先安装nrm，这里`-g`代表全局安装
    npm install nrm -g
    然后通过`nrm ls`命令查看npm的仓库列表,带*的就是当前选中的镜像仓库：
    通过`nrm use taobao`来指定要使用的镜像源：
    然后通过`nrm test npm `来测试速度：
    - 安装完成请一定要重启下电脑！！！
    
5. 快速入门
    
  5.1 下载安装

    下载地址：https://github.com/vuejs/vue
    可以下载2.5.16版本https://github.com/vuejs/vue/archive/v2.5.16.zip
    下载解压，得到vue.js文件。
    
  5.2 使用CDN

    或者也可以直接使用公共的CDN服务：
    ```html
    <!-- 开发环境版本，包含了用帮助的命令行警告 -->
    <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
    ```
    或者：
    ```html
    <!-- 生产环境版本，优化了尺寸和速度 -->
    <script src="https://cdn.jsdelivr.net/npm/vue"></script>
    ```
  5.3 推荐npm安装
  
    在idea的左下角，有个Terminal按钮，点击打开控制台：
    进入hello-vue目录：
    先输入：`npm init -y` 进行初始化
    安装Vue，输入命令：`npm install vue --save`
    然后就会在hello-vue目录发现一个node_modules目录，并且在下面有一个vue目录。
    node_modules是通过npm安装的所有模块的默认位置。
  
6. 入门案例
    
  6.1 vue渲染

    然后我们通过Vue进行渲染：
    ```html
    <div id="app">
        <h2>{{name}} 非常帅</h2>
    </div>
    <script src="./node_modules/vue/dist/vue.js"></script>
    <script type="text/javascript">
        // 生成一个Vue实例
        var app = new Vue({
            el:"#app", // el,即element。要渲染的的页面元素
            data:{ // 数据
                name:"明哥"
            }
        })
    </script>
    ```
    - 首先通过 new Vue()来创建Vue实例
    - 然后构造函数接收一个对象，对象中有一些属性：
      - el：是element的缩写，通过id选中要渲染的页面元素，本例中是一个div
      - data：数据，数据是一个对象，里面有很多属性，都可以渲染到视图中
        - name：这里我们指定了一个name属性
    - 页面中的`h2`元素中，我们通过{{name}}的方式，来渲染刚刚定义的name属性。

  6.1 双向绑定

    我们对刚才的案例进行简单修改：
    ```html
    <div id="app">
        <input type="text" v-model="num">
        <h2>
            {{name}} 非常帅,
            有{{num}}位女神为他着迷。
        </h2>
    </div>
    <script src="./node_modules/vue/dist/vue.js"></script>
    <script type="text/javascript">
        // 生成一个Vue实例
        var app = new Vue({
            el:"#app", // el,即element。要渲染的的页面元素
            data:{ // 数据
                name:"明哥",
                num:1
            }
        })
    </script>
    ```
    - 我们在data添加了新的属性：`num`
    - 在页面中有一个`input`元素，通过`v-model`与`num`进行绑定。
    - 同时通过`{{num}}`在页面输出

    可观察到，输入框的变化引起了data中的num的变化，同时页面输出也跟着变化。
    - input与num绑定，input的value值变化，影响到了data中的num值
    - 页面`{{num}}`与数据num绑定，因此num值变化，引起了页面效果变化。
    没有任何dom操作，这就是双向绑定的魅力。
  
  6.3 事件处理

    我们在页面添加一个按钮：
    ```html
    <button v-on:click="num++">点我</button>
    ```
    - 这里用`v-on`指令绑定点击事件，而不是普通的`onclick`，然后直接操作num
    - 普通click是无法直接操作num的。
  
7. Vue实例
  
  7.1 创建Vue实例

    每个 Vue 应用都是通过用 `Vue` 函数创建一个新的 **Vue 实例**开始的：

    ```javascript
    var vm = new Vue({
      // 选项
    })
    ```
    在构造函数中传入一个对象，并且在对象中声明各种Vue需要的数据和方法，包括：
    - el
    - data
    - methods
  
  7.2 模板或元素

    每个Vue实例都需要关联一段Html模板，Vue会基于此模板进行视图渲染。
    我们可以通过el属性来指定。
    例如一段html模板：
    ```html
    <div id="app">

    </div>
    ```
    然后创建Vue实例，关联这个div
    ```js
    var vm = new Vue({
      el:"#app"
    })
    ```
    这样，Vue就可以基于id为`app`的div元素作为模板进行渲染了。在这个div范围以外的部分是无法使用vue特性的。
  
  7.3 数据

    当Vue实例被创建时，它会尝试获取在data中定义的所有属性，用于视图的渲染，并且监视data中的属性变化，当data发生改变，所有相关的视图都将重新渲染，这   就是“响应式“系统。

    html：
    ```html
    <div id="app">
        <input type="text" v-model="name"/>
    </div>
    ```
    js:
    ```js
    var vm = new Vue({
        el:"#app",
        data:{
            name:"刘德华"
        }
    })
    ```
    - name的变化会影响到`input`的值
    - input中输入的值，也会导致vm中的name发生改变
    
  7.4 方法

    Vue实例中除了可以定义data属性，也可以定义方法，并且在Vue的作用范围内使用。

    html:
    ```html
    <div id="app">
        {{num}}
        <button v-on:click="add">加</button>
    </div>
    ```
    js:
    ```js
    var vm = new Vue({
        el:"#app",
        data:{
            num: 0
        },
        methods:{
            add:function(){
                // this代表的当前vue实例
                this.num++;
            }
        }
    })
    ```
  
8. 
  
  9
  
  10



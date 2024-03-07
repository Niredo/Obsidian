# Vue核心

## Vue简介

### 官网

1. Vue2官网：https://v2.cn.vuejs.org/
2. Vue3官网：https://cn.vuejs.org/
### 介绍与描述

Vue是一套用于构建用户界面的[[渐进式]]JavaScript框架
### 特点

1. 遵循==MVVM==模式。
2. 采用==组件化==模式，提高代码复用率、且让代码更好维护。
3. ==声明式==编码，让编码人员无需直接操作DOM，提高开发效率。
4. 使用[[虚拟DOM]]+优秀的==Diff算法==，尽量复用DOM节点。

### 学习Vue之前需要掌握的JavaScript基础知识

- ES6语法规范
- ES6模块化
- 包管理器
- 原型、原型链
- 数组常用方法
- axios
- promise

## 初识Vue

1. 想让Vue工作，就必须创建一个Vue实例，且要传入一个配置对象。
2. root容器里的代码依然符合html规范，只不过混入了一些特殊的Vue语法。
3. root容器里的代码被称为`Vue模板`。
4. Vue实例和容器是一一对应的。
5. 真实开发中只有一个Vue实例，并且会配合着组件一起使用。
6. {{xxx}}中的xxx要写js表达式，且xxx可以自动读取到data中的所有属性。
7. 一旦data中的数据发生改变，那么页面中用到该数据的地方也会自动更新。

```html
    <!-- 准备好一个容器 -->
    <div id="root">
        <h1>Hello,{{name}}!</h1>
    </div>

    <script type="text/javascript">
        Vue.config.productionTip = false // 阻止Vue在启动时生成生产提示。
        // 创建Vue实例
        new Vue({
            el: '#root', // el用于指定当前Vue实例为哪个容器服务，通常为css选择器字符串。
            data: { // data中用于存储数据，数据供el所指定的容器去使用。
                name: 'Vue'
            }
        })
    </script>
```
## 模板语法

html中包含了一些JS语法代码，语法分为两种，分别为：

- ==插值语法==
	- 功能：用于解析标签体内容。
	- 写法：`{{xxx}}`，xxx是js表达式，且可以直接读取到data中的所有属性。
- ==指令语法==
	- 功能：用于解析标签（包括：标签属性、标签体内容、绑定事件......）。
	- 举例：`v-bind:href="xxx"` 或 简写为 `:href="xxx"`，xxx同样要写js表达式，且可以直接读取到data中的所有属性。
	- 备注：Vue中有很多的指令，且形式都是 :v-???，此处我们只是拿v-bind举例。

```html
    <div id="root">
        <h1>插值语法</h1>
        <h3>你好,{{name}}</h3>
        <hr/>
        <h1>指令语法</h1>
        <a v-bind:href="vue2_url">{{vue.vue2_name}}</a><br/>
        <a :href="vue3_url">{{vue.vue3_name}}</a>
    </div>
    
    <script type="text/javascript">
        Vue.config.productionTip = false // 阻止Vue在启动时生成生产提示

        new Vue({
            el:'#root',
            data:{
                name:'Vue',
                vue2_url:'https://v2.cn.vuejs.org/',
                vue3_url:'https://cn.vuejs.org/',
                vue:{
                    vue2_name:'Vue2官网',
                    vue3_name:'Vue3官网'
                }
            }  
        })
    </script>
```
## 数据绑定

- ==单向数据绑定==
	- 语法：`v-bind:href = "xxx"` 或简写为：`:href`
	- 特点：数据只能从data流向页面。
- ==双向数据绑定==
	- 语法：`v-model:value = "xxx"` 或简写为 `v-model = "xxx"`
	- 特点：数据不仅能从data流向页面，还可以从页面流向data。

**备注：**
1. 双向绑定一般都应用在表单类元素上（如：input、select等）。
2. `v-model:value` 可以简写为 `v-model`，因为v-model默认收集的就是value值。
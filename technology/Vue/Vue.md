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
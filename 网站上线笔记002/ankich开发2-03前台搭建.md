# 3. 写网站前台的前端页面

项目域名：ankichina.net

应用技术： vuetify

## 3.1. 创建项目

### 3.1.1. 配置安装环境

```
1. 安装yarn
	npm install -g yarn

2. 设置yarn国内镜像
	yarn config set registry https://registry.npm.taobao.org
```

### 3.1.2. 创建项目

```
yarn create nuxt-app ankichina
```



### 3.1.3. 项目配置(使用vuetify，ssr)

```
  ? Project description My bedazzling Nuxt.js project
  ? Author name John0079
  ? Choose the package manager Yarn     
  ? Choose UI framework Element
  ? Choose custom server framework None (Recommended)
  ? Choose Nuxt.js modules Axios, Progressive Web App (PWA) Support, DotEnv
  ? Choose linting tools ESLint, Prettier 
  ? Choose test framework None
  ? Choose rendering mode Single Page App
  ? Choose development tools jsconfig.json (Recommended for VS Code)
```



### 3.1.4. 项目测试与运行

```
To dev
	cd ankichina
	yarn dev
To build & start for production:
	cd ankichina
	yarn build
	yarn start
```



## 3.2 配置prettier

### 3.2.1 创建配置文件

在项目上一级目录下创建文件 ../vscode_config/.prettierrc 文件， 内容如下：

```
{
  "semi": false,
  "arrowParens": "always",
  "singleQuote": true,
  "endOfLine": "auto"
}
```

### 3.2.2 在vscode中引入配置文件

ctrl + shift + p 打开选项框，

选择点击： prettier.create.config file

引入上面文件

### 3.2.3 代码格式化的快捷键

alt  + shift + f 对当前文件进行格式化



### 3.2.4. 配置完还报错，怎么办？

把vs-code关掉重启就好了







## 3.3. 前端渲染markdown文件

### 3.3.1 首先安装marked插件

```
yarn add marked
```

### 3.3.2 在组件中引入marked

```
<!-- xx.vue -->
<template>
  <div v-html="md"></div>
</template>

<script>
  //引入marked
  const marked = require('marked')
  export default {
    data() {
      return {
        md: ''
      }
    },
    created() {
      // 调用marked函数，传入markdown格式的内容，返回一段html
      this.md = marked('# Marked in the browser\n\nRendered by **marked**.')
    }
  }
</script>
```



### 3.3.3 ？？？？如何引入文件

网上的说法是这样

 https://www.jianshu.com/p/7b608ce22216 

但是没走通



## 3.4. 父组件向子组件传递数据

1. 分别创建父组件与子组件

```
// 父组件名字
manual.vue

// 子组件名字
nanualTree.vue
```

2. 定目标

```
父组件要向子组件传递  listData 
```

3. 怎么传呢? 怎么使用呢？四个步骤搞定：

```
第一个步骤：
	父组件创建的 data中添加一个属性： listData
第二个步骤：
	子组件中创建 props 这么写：  props: ['manualData']
第三个步骤：
	父组件中引用子组件，并传递这个参数： <manual-tree :listData="listData" />
第四个步骤：
	子组件使用这个传递来的参数： <li v-for="item in listData" :key="item.index">{{ item.value }}</li>
```



## 3.5. 组件与组件之间的通信

1. 安装js库

```
yarn add pubsub-js
```

2. 哪个地方将被触发，哪个地方就注册函数

在组件创建的时候，注册这个函数，即在create中执行下面代码

```
PubSub.subscribe('skipToAnchor', function(event, data){
	alert(data)
})
```

3. 哪里要触发这个事件，哪里就发送消息

```
PubSub.publish('skipToAnchor', data)
```









## 3.2. 搭建结构

搭建结构

## 3.3. 核心逻辑











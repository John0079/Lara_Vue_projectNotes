

# 2. 写网站后台的前端页面

项目域名：zang.ankchina.net

应用的技术： element-ui

## 2.1. 创建项目

### 2.1.1. 配置安装环境

```
1. 安装yarn
	npm install -g yarn

2. 设置yarn国内镜像
	yarn config set registry https://registry.npm.taobao.org
```

### 2.1.2. 创建项目

```
yarn create nuxt-app ankich-admin
```

### 2.1.3. 项目配置(使用eliment-ui， spa)

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

### 2.1.4. 项目测试与运行

```
To dev
	cd editortest
	yarn dev
To build & start for production:
	cd editortest
	yarn build
	yarn start
```

### 2.1.5 配置prettier

#### 2.1.5.1 创建配置文件

创建  ~/../vscode_config/.prettierrc 文件

```
{
  "semi": false,
  "arrowParens": "always",
  "singleQuote": true,
  "endOfLine": "auto"
}
```



#### 2.1.5.2 引入配置文件

ctrl + shift + p 打开选项框，引入上面文件



#### 2.1.5.3 格式化

alt  + shift + f 对当前文件进行格式化

### 2.1.6. 安装vue2-editer插件

#### 2.1.6.1 安装插件

```
yarn add vue2-editor
```

#### 2.1.6.2 创建插件配置文件

在plugins目录下创建editor.js文件

```
import Vue from 'vue'
import VueEditor from 'vue2-editor'
Vue.use(VueEditor)
```

#### 2.1.6.3 编辑nuxt.config.js文件

```
plugins: [
  { src: '~/plugins/editor', ssr: false }
],
```

#### 2.1.6.4 测试应用

（修改~/pages/index.vue)

```
<template>
  <div class="container">
    <div>dddd zzzzz</div>
    <vue-editor v-model="content"></vue-editor>
  </div>
</template>

<script>
export default {
  data() {
    return {
      content: ''
    }
  }
}
</script>

```

### 2.1.7 备份项目，便于返工

将当前的项目压缩备份，备份名称为 

```
ankich-admin---for-v01.zip
```



## 2.2. 登陆部分

### 2.2.1 登陆界面搭建



## 2.3. 核心逻辑


# 1. 项目测试结构

## 1.1. 项目初始化的配置

```
? Choose the package manager Yarn     
? Choose UI framework Element
? Choose custom server framework None (Recommended)
? Choose Nuxt.js modules Axios, Progressive Web App (PWA) Support, DotEnv
? Choose linting tools ESLint, Prettier 
? Choose test framework None
? Choose rendering mode Single Page App
? Choose development tools jsconfig.json (Recommended for VS Code)
```

## 1.2. 测试的整体步骤

| 序号 | 项目名        | 作用                                                         | 加插件       |
| ---- | ------------- | ------------------------------------------------------------ | ------------ |
| 1    | yarn-ele-spa  | 创建yarn管理的element-ui的SPA项目                            |              |
| 2    | ankich-adm-02 | 集成插件和script，和login简单页面                            | mavon-editor |
| 3    | ankich-adm-03 | 集成login页面，和home简页面，加入static资源                  |              |
| 4    | ankich-adm-04 | 集成home完整页面，                                           |              |
| 5    | ankich-adm-05 | 完成所有简单页面，及登陆状态判断                             |              |
| 6    | ankich-adm-06 | 完成memberManage/translationManage 以及./addParagraph完整页面 |              |
| 7    | ankich-adm-07 | 完成 ./assignTask  ./paraManage  translationAction页面       |              |
| 8    | ankich-adm-08 | 完成 页面 memberCenter页面                                   |              |
| 9    | ankich-adm-09 | 完成 页面 quanManage rightManage roleManage volunteerManage deckManage |              |



# 2. 测试ankich-adm-02项目

## 2.1. 添加一个简单页面login

```
页面位置： ~/pages/login/index.vue
页面内容：
<template>
  <div>login</div>
</template>

<script>
export default {
  components: { AppLink }
}
</script>

<style scoped></style>

```

结果报错，格式错误，怎么办？

## 2.2. 解决格式校验错误

### 2.2.1. 创建配置文件

创建  ~/../vscode_config/.prettierrc 文件

```
{
  "semi": false,
  "arrowParens": "always",
  "singleQuote": true,
  "endOfLine": "auto"
}
```



### 2.2.2. 引入配置文件

ctrl + shift + p 打开选项框，引入上面文件



### 2.2.3. 修改.prettierrc文件

```
{
  "semi": false,
  "arrowParens": "always",
  "singleQuote": true,
  "endOfLine": "auto"
}
```



### 2.2.4. 重启vscode

。。。。。。



### 2.2.5. 格式化

alt  + shift + f 对当前文件进行格式化



## 2.3. 拷贝ankich-adm项目中的 plugins

### 2.3.1. 拷贝plugins

拷贝到 ~/plugins下面

### 2.3.2. 修改nuxt.config.js

```
1. 添加： MavonEditor

  plugins: ['@/plugins/element-ui', { src: '~/plugins/editor', ssr: false }],
```

这时出错，要求安装  mavon-editor

### 2.3.3. 安装 mavon-editor并测试

```
安装
yarn add mavon-editor

测试， 修改~/page/login/index.vue

<template>
  <div>
    <div>login</div>
    <mavon-editor v-model="value" />
  </div>
</template>

<script>
const value = '## hello nihao a !'
export default {
  data() {
    return {
      value
    }
  }
}
</script>

<style scoped></style>

```

## 2.4. 打包上线测试

打包  yarn generate

上线测试：

​	没有一点问题，完美无缺

## 2.5. 对项目打包备份

对项目打包成 ankich-adm-02.zip， 并修改原有的项目名为 ankich-adm-03



# 3. 测试ankich-adm-03项目

## 3.1. 添加一个完整login

```
并添加：
原项目中的 ~/static/images 文件

```

## 3.2. 创建简单home页面

```
创建文件： ~/pages/home/index.vue
内容：

```

## 3.3. 测试登陆

```
username: 270752265@qq.com
password: 12345678
```

## 3.4. 打包上线测试

测试ok

## 3.5. 项目备份

对项目打包成 ankich-adm-03.zip， 并修改原有的项目名为 ankich-adm-04





# 4. 测试ankich-adm-04项目

## 4.1. 添加一个完整home页面

```
1. 拷贝原有项目的home/index.vue内容
2. 拷贝组件
	~/components/AppHeader
	~/components/AppNavber
	~/components/Link
3. 拷贝layout
	~/layouts/center_layout.vue
	~/layouts/default.vue
4. 测试全部ok
```

## 4.2. 打包上线测试

测试ok

## 4.3. 项目备份

对项目打包成 ankich-adm-04.zip， 并修改原有的项目名为 ankich-adm-05



# 5. 测试ankich-adm-05项目

## 5.1. 完善整个项目结构

```
1. 拷贝原有项目的 的其他剩余页面
        ~/pages/deckManage/index.vue
        ~/pages/memberCenter/index.vue
        ~/pages/memberManage/index.vue
        ~/pages/quanManage/index.vue
        ~/pages/README.md/index.vue
        ~/pages/rightManage/index.vue
        ~/pages/roleManage/index.vue
        ~/pages/translationAction/index.vue
        ~/pages/translationManage/index.vue
        ~/pages/volunteerManage/index.vue
2. 将在这些vue de 内容都简化
	简化成页面的名字
3. 测试左侧导航栏
	测试ok
```

## 5.2. 调试登陆拦截

```
添加middleware
	拷贝 ~/middleware/redirect.js文件到到 新项目下
修改文件 nuxt.config.js
  router: {
    middleware: ['redirect']
  },
测试：
	ok

```



## 5.3. 打包上线测试

测试ok

## 5.4. 项目备份

对项目打包成 ankich-adm-05.zip， 并修改原有的项目名为 ankich-adm-06



# 6. 测试ankich-adm-06项目

## 6.1. 完善页面translationManage

```
1. 拷贝原有项目的 页面
        ~/pages/translationManage/index.vue
```

## 6.2. 完善页面./addParagraph

```
1. 拷贝原有项目的 页面
        ~/pages/translationManage/addParagraph/index.vue
```



## 6.3. 打包上线测试

测试ok

## 6.4. 项目备份

对项目打包成 ankich-adm-06.zip， 并修改原有的项目名为 ankich-adm-07



# 7. 测试ankich-adm-07项目

## 7.1. 完善页面./assignTask

```
1. 拷贝原有项目的 页面
        ~/pages/translationManage/assignTask/index.vue
```

## 7.2. 完善页面./paraManage

```
1. 拷贝原有项目的 页面
        ~/pages/translationManage/paraManage/index.vue
```



## 7.3. 打包上线测试

测试ok

## 7.4. 项目备份

对项目打包成 ankich-adm-07.zip， 并修改原有的项目名为 ankich-adm-08





# 8. 测试ankich-adm-08项目

## 8.1. 完善页面./memberCenter

```
1. 拷贝原有项目的 页面
        ~/pages/memberCenter/index.vue
```

## 8.3. 打包上线测试

测试ok

## 8.4. 项目备份

对项目打包成 ankich-adm-08.zip， 并修改原有的项目名为 ankich-adm-09



# 9. 测试ankich-adm-09项目

## 9.1. 完善页面./memberCenter

```
1. 拷贝原有项目的 页面
        ~/pages/quanManage /index.vue
        ~/pages/rightManage /index.vue
        ~/pages/roleManage /index.vue
        ~/pages/volunteerManage/index.vue
        ~/pages/deckManage/index.vue
```

## 9.3. 打包上线测试

测试ok

## 9.4. 项目备份

对项目打包成 ankich-adm-09.zip，并修改原有的项目名为 ankich-adm-10





# 10. 测试ankich-adm-10项目

## 10.1. 添加 router.js插件

```
1. 修改nuxt.config.js

2. 注入route

import routes from './plugins/router'
。。。。。
  router: {
    middleware: ['redirect'],
    extendRoutes: routes
  },
。。。。。
```

## 10.2. 打包上线测试

测试ok

## 10.3. 项目备份

对项目打包成 ankich-adm-09.zip，并修改原有的项目名为 ankich-adm-11









































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
yarn add mavon-editor
```

#### 2.1.6.2 创建插件配置文件

在plugins目录下创建editor.js文件

```
import Vue from 'vue'
import VueEditor from 'mavon-editor'
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



## 2.3. 翻译任务指派部分





具体工作逻辑步骤：

 1. 补充翻译段落信息

 2. 修改form表单

 3. 分页 doc_type 查询显示 search

 4. 查询的结果包含 所有志愿者信息

 5. 添加翻译者

    












































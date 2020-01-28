# 1. yarn环境配置

1. 安装yarn

   ```
   npm install -g yarn
   ```

2. 设置yarn国内镜像

   ```
   yarn config set registry https://registry.npm.taobao.org
   ```

3. 还原yarn镜像

   ```
   yarn config set registry https://registry.yarnpkg.com
   ```

   

# 2. 创建nuxt.js项目

1. 创建命令

   ```
   yarn create nuxt-app editortest
   ```

2. 项目配置

   ```
   ? Project description My bedazzling Nuxt.js project
     ? Author name John0079
     ? Choose the package manager Yarn     
     ? Choose UI framework Vuetify.js
     ? Choose custom server framework None (Recommended)
     ? Choose Nuxt.js modules Axios, Progressive Web App (PWA) Support, DotEnv
     ? Choose linting tools ESLint, Prettier 
     ? Choose test framework None
     ? Choose rendering mode Universal (SSR)
     ? Choose development tools (Press <space> to select, <a> to toggle all, <i> to invert selection)
     >( ) jsconfig.json (Recommended for VS Code)
   ```

3. 项目测试运行方法

   ```
   	cd editortest
   	yarn dev
   To build & start for production:
   	cd editortest
   	yarn build
   	yarn start
   ```

   

# 3. mavon-editer安装与配置

1. 安装

   ```
   yarn add mavon-editor
   ```

2. 在plugins目录下创建editor.js文件

   ```
   import Vue from 'vue'
   import MavonEditor from 'mavon-editor'
   import 'mavon-editor/dist/css/index.css'
   Vue.use(MavonEditor)
   
   ```

3. 编辑nuxt.config.js文件

   ```
   plugins: [
     { src: '~/plugins/editor', ssr: false }
   ],
   ```

# 4. mavon-editer的使用

```
<template>
  <div>
    <div>hahhahah</div>
    <mavon-editor v-model="handbook" />
  </div>
</template>

<script>
export default {
  components: {
    // Logo,
    // VuetifyLogo
  }
}
</script>


```



# 4. mavon-editor使用参考

```
成功测试的：
http://www.fly63.com/nav/2051



https://www.jianshu.com/p/78ea4f94a3d0
```



# 5. vscode插件Prettier

1. 安装vscode插件，名字如下：

   ```
   prettier - code formatter
   ```

2. 创建prettier配置文件，放在一个目录下：~/vsconfig/.prettierrc

   ```
   {
     "semi": false,
     "arrowParens": "always",
     "singleQuote": true,
     "endOfLine": "auto"
   }
   ```

3. vscode引入配置文件

   ctrl+shift+P 打开命令行，引入上面的配置文件

4. 使用prettier来格式化文件

   使用快捷键 shift + alt + f

以上信息摘于网页： https://segmentfault.com/a/1190000016579279 
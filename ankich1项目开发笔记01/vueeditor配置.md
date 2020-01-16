1. 安装项目

   ```
   yarn config set registry https://registry.npm.taobao.org
   
   yarn create nuxt-app editortest
   ```

安装选项：

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

![1579106703035](C:\Users\Honghu009\AppData\Roaming\Typora\typora-user-images\1579106703035.png)

1. 安装后的运行测试

   ```
   
           cd editortest
           yarn dev
   
     To build & start for production:
   
           cd editortest
           yarn build
           yarn start
   ```

   

2. 安装vue-editor

   ```
   yarn add vue2-editor
   
   ```

   

3. 编辑editor.js

   ```
   import Vue from 'vue'
   import VueEditor from 'vue2-editor'
   Vue.use(VueEditor)
   
   ```

   

4. 编辑nuxt.config.js

   ```
   
     plugins: [
       { src: '~/plugins/editor', ssr: false }
     ],
   ```

   
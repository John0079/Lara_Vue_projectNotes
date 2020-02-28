# 1. 项目测试结构

## 1.1. 项目创建参数

项目没有 Eslint检测，项目是单页面应用---spa

yarn create nuxt-app qt-ele-01

```

? Choose UI framework Element
? Choose custom server framework None (Recommended)
? Choose Nuxt.js modules Axios, Progressive Web App (PWA) Support, DotEnv
? Choose linting tools (Press <space> to select, <a> to toggle all, <i> to invert selection)
? Choose test framework None
? Choose rendering mode Single Page App
? Choose development tools jsconfig.json (Recommended for VS Code)
```



## 1.2. 测试的整体步骤

| 序号 | 项目名     | 作用             | 加插件         |
| ---- | ---------- | ---------------- | -------------- |
| 1    | qt-html-01 |                  |                |
| 2    | qt-html-02 | 简化，打包，上线 |                |
| 3    | qt-html-03 | 测试互发信息     | qwebchannel.js |
|      |            |                  |                |
|      |            |                  |                |
|      |            |                  |                |
|      |            |                  |                |
|      |            |                  |                |
|      |            |                  |                |

## 1.3. 项目备份

备份项目到 qt-html-01.zip,   修改项目名称 qt-html-02



# 2. 测试qt-html-02项目

## 2.1. 简化~/pages/index.vue页面

```
页面位置： ~/pages/login/index.vue
页面内容：
<template>
  <v-layout column justify-center align-center>
    <v-flex xs12 sm8 md6>
      <div class="text-center"></div>
      <v-card>
        <v-card-title class="headline">
          Welcome to the Vuetify + Nuxt.js template
        </v-card-title>
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>
export default {}
</script>

```

结果报错，格式错误，怎么办？

## 2.2. 打包

```
yarn generate
```

## 2.3. Q测试

测试成功

## 2.4. 备份

备份项目到 qt-html-02.zip,   修改项目名称 qt-html-03



# 3. 测试qt-html-03项目

## 3.1. 在~/plugins中加入插件

```
加入插件： ~/plugins/qwebchannel.js
```

## 3.2. 在页面中引用并使用插件

### 3.2.1 template部分：

```

          <div>
            <v-btn small color="primary" dark @click="fromWebToCpp"
              >点击发报</v-btn
            >
          </div>
```

### 3.2.2. script部分：

```

<script>
import QWebChannel from "~/plugins/qwebchannel";
export default {
  data() {
    return {
      userAgent: ""
    };
  },
  created() {
    if (process.browser) {
      this.userAgent = window.navigator.userAgent;

      window.onload = () => {
        if (window.navigator.userAgent.indexOf("Toon-pc") !== -1) {
          new QWebChannel(window.qt.webChannelTransport, channel => {
            window.bridge = channel.objects.cppObject;

            const msec = new Date().getTime();
            // cpp通过signalToWeb信号给web传值:response
            window.bridge.signalToWeb.connect(response => {
              window.alert(msec);
            });
          });
          console.log("==QWebChannel==", QWebChannel);
        } else {
          console.log("==+++=QWebChannel==", QWebChannel);
        }
      };
    }
  },
  methods: {
    fromWebToCpp() {
      // web调用cpp的 sendTextToCpp 方法，并带上参数
      if (process.browser) {
        window.bridge.sendTextToCpp(
          JSON.stringify({
            userId: 100
          })
        );
      }
    }
  }
};
</script>

```



## 3.4. Q测试

打包，并测试成功

## 3.5. 备份

备份项目到 qt-html-03.zip,   修改项目名称 qt-html-04
















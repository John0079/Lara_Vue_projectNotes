# 0. 项目测试结构

## 0.1. 项目创建参数

项目没有 Eslint检测，项目是单页面应用---spa

yarn create nuxt-app qt-ele-00

```

? Choose UI framework Element
? Choose custom server framework None (Recommended)
? Choose Nuxt.js modules Axios, Progressive Web App (PWA) Support, DotEnv
? Choose linting tools (Press <space> to select, <a> to toggle all, <i> to invert selection)
? Choose test framework None
? Choose rendering mode Single Page App
? Choose development tools jsconfig.json (Recommended for VS Code)
```



## 0.2. 测试的整体步骤

| 序号 | 项目名    | 作用                     | 加插件 |
| ---- | --------- | ------------------------ | ------ |
| 1    | qt-ele-01 | 简化，打包，上线，连接Qt |        |
| 2    | qt-ele-02 |                          |        |
| 3    | qt-ele-03 |                          |        |
|      |           |                          |        |
|      |           |                          |        |
|      |           |                          |        |
|      |           |                          |        |
|      |           |                          |        |
|      |           |                          |        |





# 1. 测试qt-ele-01项目

## 1.1. ~/plugins引入qwebchannel.js

拷贝qwebchannel.js到plugins目录,之后的目录结构为：

```
plugins
	qwebchannel.js
	element-ui.js
```



## 1.2. 创建页面结构

```
pages
	pad001
		index.vue
	pad002
		index.vue
	pad004
		index.vue
    index.vue
		
```

## 1.3. 在静态文件中添加目录结构pad003

```
static
	pad003
		icon.png
	....
	....
	....
```

测试成功

## 1.4. 编辑 pad00?/index.vue文件

```
<template>
  <div><img width="100%" src="~/static/pad003/icon.png"/>
  </div>
</template>

<script></script>

```

## 1.5. 编辑入口index.vue文件

```
<template>
  <el-container>
    <el-aside width="200px">Aside</el-aside>
    <el-container>
      <el-header>Header</el-header>
      <el-main>
        <div>
          <el-button type="primary" @click="fromWebToCpp">主要按钮</el-button>
        </div>
        <div>{{ userAgent }}</div>
      </el-main>
      <el-footer>Footer</el-footer>
    </el-container>
  </el-container>
</template>

<script>
import QWebChannel from "~/plugins/qwebchannel";
export default {
  data() {
    return {
      userAgent: ""
    };
  },
  created() {},
  mounted() {
    if (process.browser) {
      this.userAgent = window.navigator.userAgent;
      // that = this
      if (window.navigator.userAgent.indexOf("Toon-pc") !== -1) {
        new QWebChannel(window.qt.webChannelTransport, channel => {
          window.bridge = channel.objects.cppObject;

          const msec = new Date().getTime();
          // cpp通过signalToWeb信号给web传值:response

          window.bridge.signalToWeb.connect(function(response) {
            window.alert(msec);
          });

          window.bridge.signalToWeb_1.connect(this.showDiff);
        });
        console.log("==QWebChannel==", QWebChannel);
      } else {
        console.log("==+++=QWebChannel==", QWebChannel);
      }
    }
  },
  methods: {
    getCppData(response) {
      this.userAgent = response;
    },
    fromWebToCpp() {
      // web调用cpp的 sendTextToCpp 方法，并带上参数
      if (process.browser) {
        if (window.bridge) {
          window.bridge.sendTextToCpp(
            JSON.stringify({
              userId: 100
            })
          );
        } else {
          console.log("this is no bridge");
        }
      }
    },
    showDiff(response) {
      var msec = new Date().getTime();
      var oldSec = response.msec;
      alert(msec - oldSec);
    }
  }
};
</script>

<style>
.el-header,
.el-footer {
  background-color: #b3c0d1;
  color: #333;
  text-align: center;
  line-height: 60px;
}

.el-aside {
  background-color: #d3dce6;
  color: #333;
  text-align: center;
  line-height: 200px;
}

.el-main {
  background-color: #e9eef3;
  color: #333;
  text-align: center;
  line-height: 160px;
}

body > .el-container {
  margin-bottom: 40px;
}

.el-container:nth-child(5) .el-aside,
.el-container:nth-child(6) .el-aside {
  line-height: 260px;
}

.el-container:nth-child(7) .el-aside {
  line-height: 320px;
}
</style>

```

## 1.6. 打包测试

测试Qt项目：D:\QtProjectS\day08\webEng_test02

测试py项目：D:\PyProjectS_32bit\kernalServer01

测试结果：ok

## 1.7. 备份

备份项目到： qt-ele-01.zip, 打包项目到 qt-ele-02



# 2. 测试打通--交通线

## 2.1 html--->cpp 发报

怎么发报？

```
html端：
	ipcRenderer.sendJson(* json)
cpp端：
	ipcMain.on(* json)
	
```



## 2.2 cpp--->html发报

怎么发报？

```
html端：
	ipcMain.send(* json)
cpp端：
	ipcRenderer.on(* json)
```






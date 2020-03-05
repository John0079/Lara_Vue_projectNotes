# 1. 项目测试结构

## 1.1. 项目创建参数

项目没有 Eslint检测，项目是单页面应用---spa

yarn create nuxt-app qt-html-01  (使用vuetify框架)

```
? Choose UI framework Vuetify.js
? Choose custom server framework None (Recommended)
? Choose Nuxt.js modules Axios, Progressive Web App (PWA) Support, DotEnv
? Choose linting tools (Press <space> to select, <a> to toggle all, <i> to invert selection)
? Choose test framework None
? Choose rendering mode Single Page App
? Choose development tools (Press <space> to select, <a> to toggle all, <i> to invert selection)
```



## 1.2. 测试的整体步骤

| 序号 | 项目名     | 作用                    | 加插件         |
| ---- | ---------- | ----------------------- | -------------- |
| 1    | qt-html-01 |                         |                |
| 2    | qt-html-02 | 简化，打包，上线        |                |
| 3    | qt-html-03 | 测试互发信息            | qwebchannel.js |
| 4    | qt-html-04 | 规范化cpp---web通信标准 |                |
| 5    | qt-html-05 | 引进pubsub-js           | pubsub-js      |
|      |            |                         |                |
|      |            |                         |                |
|      |            |                         |                |
|      |            |                         |                |

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
```



## 3.4. Q测试

打包，并测试成功，Qt端项目，webEng_test03， html页面：~/build_temp/index002.html

## 3.5. 美化页面布局

借用vuetify的功能来美化页面

## 3.6. 备份

备份项目到 qt-html-03.zip, 修改现有项目为qt-html-04



# 4. 测试qt-html-04,标准化交通线

## 4.1. 规划ipc接口

### 4.1.1. cpp端

```
发报：综合信息
	ipcMainSend(const QJsonObject &json)
		------->ipcRendererOn(response)
发报：单信息
	ipcMainSendStr(const QString &text)
		------->ipcRenderOnStr(response)

接收信息：综合信息
	ipcMainOn(const QJsonObject &request)
接收信息：单信息
	ipcMainOnStr(const QString &request)
```

### 4.1.2. html端

```
发报：综合信息
	ipcRendererSend(json)
		------->ipcMainOn(request)
发报：单信息
	ipcRenderSendStr(text)
		------->ipcMainOnStr(request)

接收信息：综合信息
	ipcRendererOn(response)
接收信息：单信息
	ipcRenderOnStr(response)
```



## 4.2. 双端方法规划

### 4.2.1. cpp调用html端

```
执行方法：
	toWeb_swithPadHome() {
		var json = {
			"action": "fromQt_swithPadHome",
			"paras": {"aa": "aaaaaaa"}
		}
		ipcMainSend(json);
	}
	
目标方法：
	fromQt_swithPadHome()

```



### 4.2.2. html调用cpp端

```
执行方法：
	toQt_queryWord() {
		var json = {
			"action": "fromWeb_queryWord",
			"paras": {"word": "schama"}
		}
		ipcMainSend(json);
	}
	
目标方法：
	fromWeb_queryWord()

	
```



## 4.3. Q测试

打包，并测试成功，Qt端项目，webEng_test04， html页面：~/build_temp/index004.html

## 4.4. 备份

备份项目到 qt-html-04.zip, 修改现有项目为qt-html-05





# 5. 测试qt-html-05,引进pubSub.js

## 5.1. 三个页面,排兵布阵

### 5.1.1. welcome页面

```
这个页面内容：程序的首页
要求：
{
	1. 切换layout模式：即隐藏appbar,隐藏drawer,隐藏footer
	2. 主页面切换到组件 pageWelcome
	3. 
}
```

### 5.1.2. Course页面

```
这个页面内容：程序的第二个页面，让用户选择课程
要求：
{
	1. 切换layout模式：即隐藏appbar,隐藏drawer,隐藏footer
	2. 主页面切换到组件 pageCourses
	3. 
}
```

### 5.1.3. learning页面，即主页面

```
这个页面内容：程序的第三个页面，学习状态的页面
要求：
{
	1. 切换layout模式：即显示appbar,显示drawer,显示footer
	2. 
	3. 
}
```

## 5.2. 安装插件

安装插件：yarn add pubsub-js  

## 5.3. Q测试

打包，并测试成功，Qt端项目，webEng_test04，

## 5.4. 备份

备份项目到 qt-html-05.zip, 修改现有项目为qt-html-06










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

| 序号 | 项目名     | 作用                                   | 加插件         |
| ---- | ---------- | -------------------------------------- | -------------- |
| 1    | qt-html-01 |                                        |                |
| 2    | qt-html-02 | 简化，打包，上线                       |                |
| 3    | qt-html-03 | 测试互发信息                           | qwebchannel.js |
| 4    | qt-html-04 | 规范化cpp---web通信标准                |                |
| 5    | qt-html-05 | 引进pubsub-js                          | pubsub-js      |
| 6    | qt-html-06 |                                        |                |
| 7    | qt-html-07 |                                        |                |
| 8    | qt-html-08 |                                        |                |
| 9    | qt-html-09 | 实现鼠标单击，双击，右击，选中事件分离 | jquery         |

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

## 5.3. 建立桥接

```

    void toWeb_swithPadHome();
    void toWeb_swithPageWelcom();
    void toWeb_swithPageCourse();
    void toWeb_swithPageLearning();
    void toWeb_swithPadGeneral();

    void toWeb_showNoAnki();
    void toWeb_showFirstWithAnki();
    void toWeb_showSecondWithAnki();
    void toWeb_showLclFlag();
    void toWeb_showWaiting();
    void toWeb_showCourseList();
    void toWeb_showUpdateNewVersion();
    void toWeb_showNoInternet();
    void toWeb_getLocalTime();
```



## 5.3. Q测试

打包，并测试成功，Qt端项目，webEng_test05，打包vue项目为 dist5, dist5 内置服务器LclServer.exe

## 5.4. 备份

备份项目到 qt-html-05.zip, 修改现有项目为qt-html-06

# 6. 测试qt-html-06

## 6.1. 建立welcome页面，和course页面的桥接

```

```



## 6.3. Q测试

打包，并测试成功，Qt端项目，webEng_test06，打包vue项目为 dist6, dist6 内置服务器LclServer.exe

## 6.4. 备份

备份项目到 qt-html-06.zip, 修改现有项目为qt-html-07

# 7. 测试qt-html-07

## 7.1. 实现Qt向html发送wordSStr

```

```



## 7.2. Q测试

打包，并测试成功，Qt端项目，webEng_test07，打包vue项目为 dist7, dist7 内置服务器LclServer.exe

## 7.3. 备份

备份项目到 qt-html-07.zip, 修改现有项目为qt-html-08

# 8. 测试qt-html-08

## 8.1. 实现Qt加载WaveWidget

```

```

## 8.2. 实现audioContrl



## 8.3. Q测试

打包，并测试成功，Qt端项目，webEng_test08，打包vue项目为 dist8, dist8 内置服务器LclServer.exe

## 8.4. 备份

备份项目到 qt-html-08.zip, 修改现有项目为qt-html-09

# 9. 测试qt-html-09

## 9.1. 实现鼠标单击，双击，右击，选中事件分离

```

    registAllMouseEvent() {
      if (process.browser) {
        // 1. 先清除已经绑定的事件
        $(".word").off();

        //2. 添加单击左键事件
        $(".word").on("click", event => {
          // this.wordClick(event);
          // 让段落播放暂停到这里了
          if (this.clickFlag) {
            //取消上次延时未执行的方法
            this.clickFlag = clearTimeout(this.clickFlag);
          }

          this.clickFlag = setTimeout(function() {
            // click 事件的处理
            console.log("播放进度，暂停到这个单词---", event.target.id);
          }, 300); //延时300毫秒执行
        });

        //3. 添加 鼠标双击 事件
        $(".word").on("dblclick", event => {
          // this.wordClick(event);
          // 选中这个单词，要查单词啦
          // console.log("选中这个单词，要查单词啦---", event.target.id);
          if (this.clickFlag) {
            //取消上次延时未执行的方法
            this.clickFlag = clearTimeout(this.clickFlag);
          }

          // dblclick 事件的处理
          console.log("zheshi 鼠标逐渐的-----双击时间");
        });

        //4. 鼠标拖拽选中和--右键单击事件
        $(".word").on("mouseup", event => {
          // 4.1 鼠标拖拽选中事件
          var selection = window.getSelection();
          var range00 = document.createRange();
          var str = selection.toString();
          if (str.length > 0) {
            //myAlert(selection.anchorNode.parentElement.id + "-" + selection.focusNode.parentElement.id);
            var startNode = selection.anchorNode.parentElement;
            var endNode = selection.focusNode.parentElement;
            range00.setStart(startNode, 0);
            range00.setEnd(endNode, 1);
            selection.removeAllRanges();
            selection.addRange(range00);
            // selectThisSegment(startNode.id, endNode.id);
            console.log(
              "选中了一个段落，起始位置",
              startNode.id,
              "---结束位置--",
              endNode.id
            );
            return;
          }

          // 4.2 鼠标右键点击事件
          if (event.button === 2) {
            var NodeId = event.target.id;
            console.log("鼠标右键单机了---", NodeId);
          }
        });
      }
    },
```

## 9.2. 结合LcLSerNew.py实现自动查单词

这个时候的py项目为newLcLser09



## 9.3. Q测试

打包，并测试成功，Qt端项目，webEng_test09，打包vue项目为 dist9, dist9 内置服务器LclServer.exe

测试注意：

```
1. 首先运行 LcLSerNew.py
2. 再发送请求：http://localhost:17701/initUser  以便于开启权限
3. 运行LclServer.exe
4. 运行Qt项目，测试查单词
```



## 9.4. 备份

备份项目到 qt-html-09.zip, 修改现有项目为qt-html-10








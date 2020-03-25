# 0. 项目测试结构

## 0.1. 项目创建参数

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



## 0.2. 测试的整体步骤

| 序号 | 项目名     | 作用                                           | 加插件         |
| ---- | ---------- | ---------------------------------------------- | -------------- |
| 1    | qt-html-01 |                                                |                |
| 2    | qt-html-02 | 简化，打包，上线                               |                |
| 3    | qt-html-03 | 测试互发信息                                   | qwebchannel.js |
| 4    | qt-html-04 | 规范化cpp---web通信标准                        |                |
| 5    | qt-html-05 | 引进pubsub-js                                  | pubsub-js      |
| 6    | qt-html-06 |                                                |                |
| 7    | qt-html-07 |                                                |                |
| 8    | qt-html-08 |                                                |                |
| 9    | qt-html-09 | 实现鼠标单击，双击，右击，选中事件分离, 查单词 | jquery         |
| 10   | qt-html-10 | 开始项目路径开发                               |                |
|      |            |                                                |                |
|      |            |                                                |                |
|      |            |                                                |                |
|      |            |                                                |                |

## 0.3. 项目备份

备份项目到 qt-html-01.zip,   修改项目名称 qt-html-02



# 10. 测试qt-html-10项目

## 10.1. 修改界面上的pad对应的按钮



## 10.2. 连接界面上播放进度条

1. 启动界面的时候，Qt要给html信号，告诉总长度，和当前进度
2. 界面点击 播放的时候，发送消息给 pages/index.vue,  再发给Qt开始播放
3. 界面点击停止的时候，。。。。。。
4. 界面点击暂停的时候，。。。。。
5. 界面拖动的时候，。。。。。。
6. Qt播放的时候，把进度播放给 html



## 10.3. 修改查单词的 释义列表

v-data-table



## 10.4. 实现单词卡片的制作

这个时候的py项目为newLcLser09



## 10.5. 实现单词卡片的制作

这个时候的py项目为newLcLser09



## 10.6. 实现再doc文件中选词，查词制卡

这个时候的py项目为newLcLser09



## 10.7. 将python的lclserNew.py项目集合到Qt中

这个时候的py项目为newLcLser09

## 10.8. Q测试

打包，并测试成功，Qt端项目，webEng_test09，打包vue项目为 dist9, dist9 内置服务器LclServer.exe

测试注意：

```


```



## 10.9. 备份

备份项目到 qt-html-10.zip, 修改现有项目为qt-html-11








# 1. 创建五个域名

## 1.1. 五个域名分别是：

```
1. api.ankichina.net    --------------------------->用于提供api
2. adm.ankichina.net    --------------------------->用于提供后台管理
3. ankichina.net    ------------------------------->用于前台
4. res.ankichina.net    --------------------------->用于下载资源
4. http://pmdzjjjj.ankichina.net/pmd/    -----_---->用于查看服务器的数据库
```

## 1.2. 域名管理

宝塔账号：

```

```



## 1.3. 宝塔管理

宝塔账号：

```
http://49.234.3.219:10079/e8273eaf

username: u1mro4wr
password: a8bf032e
```



## 1.4. 控制台管理

```
https://cloud.tencent.com/ 
点击： 控制台>>云服务器>>实例-->>登陆
"大啊190910honghu&夏"
"Amen190910honghu&xiaji"

```



# 2. 上线ankich-web项目

## 2.1. 项目修改访问了接口路径

1. 在登陆网站头部图标哪里要修改：

```
文件位置： ~/components/navbar.vue
修改method---skipToWebsite()：
  methods: {
  	。。。。。。。
    skipToWebsite() {
      if (process.browser) {
        window.location.href = 'http://ankich-adm.ankichina.net'
      }
    },
  	。。。。。。。
  }
```

2. 根据环境设置baseUrl

```
在~/plugins/utils/request.js文件中修改

if (process.env.NODE_ENV === 'development') {
  baseUrl = 'http://ankich-api.com/'
} else if (process.env.NODE_ENV === 'production') {
  baseUrl = 'http://ankich-api.ankichina.net/'
}
```



## 2.2. 打包

```
1. 进入 ~/ankich-web
2. 测试运行  yarn dev
	测试成功。。。。
3. 打包  yarn generate
4. 压缩 ~/ankich-web/dist文件夹，--->  dist.zip

```

## 2.3. 建立站点，并上传代码

1. 建立站点

```
网站>>添加站点>>ankich-web.ankichina.net
备注：ankich-web.ankichina.net
根目录：/www/wwwroot/ankich-web

```

2. 上传代码并解压

```
首先，定位到目录：ankich-web

文件>>上传>>选择文件>>dist.zip

再解压：--->  dist

```

3. 设置网站入口

```
网站>>ankich-web.ankichina.net

设置>>网站目录>>运行目录>>dist

保存

```

4. 网站测试：

```
http://ankich-adm.ankichina.net
```

# 3. 测试遇到错误

## 3.1 错误表现

2de1a71891dadf3d2e60.js:2 TypeError: Cannot read property 'scrollToTop' of undefined
    at bf6c9026ebd4ff0352cd.js:1
    at Array.every (<anonymous>)
    at Gt.scrollBehavior (bf6c9026ebd4ff0352cd.js:1)
    at Tn.<anonymous> (2de1a71891dadf3d2e60.js:2)
    at Array.<anonymous> (2de1a71891dadf3d2e60.js:2)
    at ie (2de1a71891dadf3d2e60.js:2)

## 3.2 解决办法

项目部署到ngixt服务器上之后就正常了

# 4. 上线ankich-web项目

## 4.1. 项目修改访问了接口路径

1. 在登陆网站头部图标哪里要修改：

```
文件位置： ~/components/common/navbar.vue
修改一个方法：skipToWebsite()，修改跳跃地址

  methods: {
  	。。。。。
    skipToWebsite() {
      if (process.browser) {
        window.location.href = 'http://ankich-adm.ankichina.net/'
      }
    },
    。。。。。
  }
```

## 4.2. 打包

```
1. 进入 ~/ankich-adm
2. 测试运行  yarn dev
	测试成功。。。。
3. 打包  yarn generate
4. 压缩 ~/ankich-adm/dist文件夹，--->  dist.zip

```

## 4.3. 建立站点，并上传代码

1. 建立站点

```
网站>>添加站点>>ankich-adm.ankichina.net
备注：ankich-adm.ankichina.net
根目录：/www/wwwroot/ankich-adm

```

2. 上传代码并解压

```
首先，定位到目录：ankich-adm

文件>>上传>>选择文件>>dist.zip

再解压：--->  dist

```

3. 设置网站入口

```
网站>>ankich-adm.ankichina.net

设置>>网站目录>>运行目录>>dist

保存

```

4. 网站测试：

```
http://ankich-web.ankichina.net
```

# 
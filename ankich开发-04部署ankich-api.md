# 1. 创建四个域名

## 1.1. 三个域名分别是：

```
1. ankich-api.ankichina.net
2. ankich-adm.ankichina.net
3. ankich-web.ankichina.net
4. http://pmdzjjjj.ankichina.net/pmd/
```

## 1.2. 宝塔管理

宝塔账号：

```
http://49.234.3.219:10079/e8273eaf

username: u1mro4wr
password: a8bf032e
```

## 1.3. 控制台管理

```
https://cloud.tencent.com/ 
点击： 控制台>>云服务器>>实例-->>登陆
"大啊190910honghu&夏"
"Amen190910honghu&xiaji"

```



# 2. 上线 ankich-api

## 2.1. 数据库备份

备份数据库为： ankich-api.sql

```
这个最好用phpmyadmin导出
phpmyadmin访问地址：http://localhost/pmd/


```



## 2.2. ankich-api项目打包

将C:\laragon\www\ankich-api 压缩成 ankich-api.zip

并通过 宝塔上传到站点

## 2.3. 宝塔上创建站点

```
域名：ankich-api.ankichina.net
根目录：/www/wwwroot/ankich-api
```

## 2.4. 创建数据库

```
数据库名：ankich_api
数据库账号：root
数据库口令：zhjp0079W$sfsgdzjp
数据库口令：zhjp0079W$sfsgdzjp
```



## 2.5. 上传站点文件

1. 删除两个文件  404.html   index.html
2. 上传 ankich-api.zip
3. 解压 ankich-api.zip 到 /www/wwwroot/ankich-api 目录下

# 3. mysql配置（mariadb）

## 3.1. 卸载之前的mysql

```
rpm -aq|grep mariadb
rpm -e --nodeps mariadb-libs-5.5.64-1.el7.x86_64
```



## 3.2. 安装mariadb

```bash
/*******************************/
/************ mariadb *************/
# 网站 https://downloads.mariadb.org/
/*******************************/
# 查询是否默认残留 mariadb
rpm -aq|grep mariadb
# 移除多余的 mariadb
rpm -e --nodeps mariadb-libs-5.5.64-1.el7.x86_64

# 建设 mariadb 源
vi /etc/yum.repos.d/MariaDB.repo

# 查看官网版本，卸载已经是 10.5，应该把下面的 10.4 替换成 10.5
[mariadb]
name = MariaDB
baseurl = https://mirrors.ustc.edu.cn/mariadb/yum/10.4/centos7-amd64/
gpgkey=https://mirrors.ustc.edu.cn/mariadb/yum/RPM-GPG-KEY-MariaDB
gpgcheck=1

# 安装客户端和服务端
yum install MariaDB-server MariaDB-client -y
# 自启动
systemctl enable mariadb
# 启动
systemctl start mariadb
# 初始化
mysql_secure_installation

# 修改root名称为xly
pdate user set user='xly' where user='root'; 
# 刷新权限
flush privileges 
```

## 3.3. 配置php.ini连接mysql

 参考位置： https://zhidao.baidu.com/question/2270352115086717508.html 

把php.ini里面所有的default_socket都改成MAMP的mysql.sock的正确位置即可。 

```
pdo_mysql.default_socket=/Applications/MAMP/tmp/mysql/mysql.sock
mysql.default_socket = /Applications/MAMP/tmp/mysql/mysql.sock
mysqli.default_socket = /Applications/MAMP/tmp/mysql/mysql.sock
```

具体操作：

```
定位文件： locate php.ini
找到文件： /www/server/php/72/etc/php.ini

vim /www/server/php/72/etc/php.ini

```



## 3.4 修改mysql授权

```
摘自：https://stackoverflow.com/questions/31244041/pdoexception-sqlstate28000-1698-access-denied-for-user-rootlocalhost-s

GRANT ALL PRIVILEGES ON *.* TO 'root'@'localhost';
GRANT ALL PRIVILEGES ON *.* TO 'root'@'localhost' IDENTIFIED BY 'root';


```

具体操作：

```
mysql -uroot -p
输入密码***
>GRANT ALL PRIVILEGES ON *.* TO 'root'@'localhost';
>GRANT ALL PRIVILEGES ON *.* TO 'root'@'localhost' IDENTIFIED BY 'root';
>FLUSH PRIVILEGES;
>exit

```



## 3.999. 创建phpmyadmin网页具体步骤

```
1. 创建站点
2. 下载phpmyadmin
3. 在站点下解压下载文件
4. 根据myadmin.config.example 创建 myadmin.config文件
5. 完毕，访问这个新的站点即可
```





# 4. 项目配置

## 4.1. 修改.env文件

1. 修改数据库

```
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=anki
DB_USERNAME=root
DB_PASSWORD=zhjp0079W$sfsgdzjp
```

2. 修改baseurl

```
#BASE_URL=http://ankich-api.com
BASE_URL=http://ankich-api.ankichina.net
```



## 4.2. 路由访问不通

具体表现：网站入口能访问通，但是其他路由访问不通，

```
解决办法：
找到nginx的配置文件 /www/server/panel/vhost/nginx/your_website_name.conf
添加如下代码：

    location / {
        try_files $uri $uri/ /index.php?$query_string;
    }

```



## 4.3. 修改nginx配置文件

```
1.定位文件： locate nginx.conf
找到文件： /www/server/php/72/etc/php.ini

vim /www/server/php/72/etc/php.ini
```

## 4.4. 测试接口（注册一个用户）

```
接口地址：    
参数：  
```

测试出错：错误信息如下：

```
SQLSTATE[HY000] [1698] Access denied for user 'root'@'localhost' 
```

## 4.5. 1698错误的解决办法

解决核心，是创建一个新的用户

```
mysql -uroot -p
输入密码***  zhjp0079#@$sfsgdzjp
>use mysql;
>SELECT User, Host, plugin FROM mysql.user;

>CREATE USER 'ankich_api_user'@'localhost' IDENTIFIED BY '';

>GRANT ALL PRIVILEGES ON ankich_api.* TO 'ankich_api_user'@'localhost';
>SELECT User, Host, plugin FROM mysql.user;

>FLUSH PRIVILEGES;
>exit;
```

为新用户设置新密码

```
mysql -uroot -p
输入密码***  zhjp0079#@$sfsgdzjp
>use mysql;
>set password for 'ankich_api_user'@'localhost'=Password('zhjp0079#@$sfsgdzjp');

>SELECT User, Host, plugin FROM mysql.user;

>flush privileges;
>exit;
```

做了这些改变之后还是有错误，错误的信息是：

```
SQLSTATE[HY000] [1045] Access denied for user 'ankich_api_user'@'localhost' (using password: YES)
```

## 4.6. 1045错误解决办法

```
最终错误原因就是，密码设置的有问题，密码中用到了特殊字符 @和#
解决问题的办法，重新设置密码，把@和#去掉
还用起初的root账号登陆数据库
.env的配置如下：

DB_CONNECTION=mysql
DB_HOST=localhost
DB_PORT=3306
DB_DATABASE=ankich_api
DB_USERNAME=root
DB_PASSWORD=zhjp0079W$sfsgdzjp

```


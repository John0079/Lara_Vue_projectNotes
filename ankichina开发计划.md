# 1. 先写服务端接口

项目域名： api.ankichina.net

认证模式： passport的秘密模式

## 1.1. 创建项目

可以直接解压 laravel6c.zip文件即可

1. 将项目laravel6c改名为ankich-api

2. 修改.env里面的配置

   ```
   DB_DATABASE=ankich-api
   ```

3. 在mysql里面创建数据库 ankich-api

4. 执行数据库迁移动作

   ```
   cd ankich-api
   php artisan migrate
   ```

5. 执行命令创建access_token的key

   ```
   php artisan passport:install --force
   //如果是先创建的项目我们可以不加--force选项
   php artisan passport:install
   ```

6. 如果数据库创建错误，可以清空数据库

   ```
   php artisan migrate:fresh
   //这个操作只是清空了表的内容，如果还不可以，你可以直接删除表
   删除表之后，我们还可以重新迁移：
   php artisan migrate
   然后在执行
   php artisan passport:install --force
   ```

7. 我们顺利得到 access_token的key,并处理

   这个key值，会在PassportController文件中被引入进去

   ```
   public function __construct()
   {
       $this->middleware('auth')->except('login', 'register', 'refresh');
       $client = \DB::table('oauth_clients')->where('id', 2)->first();
       $this->clientId = $client->id;
       $this->clientSecret = $client->secret;
   }
   
   ```

8. 测试接口

   ```
   1. 测试网站入口
   http://ankich-api.com/ 
   2. 测试注册接口， 使用哪个网站  http://apizza.net/pro/#/
   
   ```

## 1.2. 配置环境

配置环境

在上一步中已经配置过了

## 1.3. 创建表，模型，控制器

### 1.3.1 总表设计：

| 表名      | 作用               | 备注： |
| --------- | ------------------ | ------ |
| user      | 略。。。           | 一期   |
| paragraph | 记录翻译的段落     | 一期   |
| deck      | 各种牌组           | 一期   |
| catagory  | 牌组类别           | 一期   |
| vedio     | 网站的各种视频资源 | 一期   |
| artical   | 各种博文资源       | 一期   |
| picture   | 各种图片资源       | 一期   |
| right     | 管理权限           | 一期   |
| role      | 角色管理           | 一期   |
| comment   | 评论               | 二期   |
| zan       | 点赞               | 二期   |

### 1.3.2 数据库重置操作

直接删除数据库,删除后要执行的操作

```
1. 先创建数据库 ankich-api
2. 迁移数据库，创建所有的表
	php artisan migrate
3. 创建 access-token 的key
	php artisan passport:install --force
4. 测试接口
	register
```



### 1.3.3 user表再设计

#### 1.3.3.1 创建user表

| 字段名            | 类型          | 默认值 | 注释             |
| ----------------- | ------------- | ------ | ---------------- |
| id                | bigIncrements |        |                  |
| name              | string        |        |                  |
| email             | string        |        |                  |
| email_verified_at | timestamp     |        |                  |
| password          | string        |        |                  |
| avatar            | string        | ‘’     | 头像             |
| is_active         | smallInteger  | ‘’     | 激活否？         |
| level             | smallInteger  | ‘’     | 用户等级         |
| production        | string        | ‘’     | 用户在网站的贡献 |
| setting           | string        | ‘’     | 用户的偏好设置   |

#### 1.3.3.2 创建paragraph表

| 字段名              | 类型          | 默认值 | 注释                  |
| ------------------- | ------------- | ------ | --------------------- |
| id                  | bigIncrements |        |                       |
| title               | string        | ‘’     | 标题                  |
| title_translation   | string        | ‘’     | 标题翻译              |
| content             | string        | ‘’     | 内容                  |
| content_translation | string        | ‘’     | 内容翻译              |
| translators         | string        | '[]'   | 翻译者id              |
| index_code          | string        | ‘’     | 索引编码              |
| doc_type            | string        | ‘’     | 文档类型（安卓？ios） |
| complete_status     | smallInteger  | ‘’     | 完成状态              |

#### 1.3.3.3 创建vedio表

| 字段名    | 类型          | 默认值 | 注释 |
| --------- | ------------- | ------ | ---- |
| id        | bigIncrements |        |      |
| name      | string        | ''     | 名字 |
| title     | string        | ''     | 标题 |
| introduce | string        | ''     | 简介 |
| author    | string        | ''     | 作者 |
| url       | string        | ''     | 网址 |
| picture   | string        | ''     | 图片 |
| tags      | string        | '[]'   | 标签 |

#### 1.3.3.4 创建article表

| 字段名    | 类型          | 默认值 | 注释 |
| --------- | ------------- | ------ | ---- |
| id        | bigIncrements |        |      |
| name      | string        | ''     | 名字 |
| title     | string        | ''     | 标题 |
| introduce | string        | ''     | 简介 |
| author    | string        | ''     | 作者 |
| url       | string        | ''     | 网址 |
| picture   | string        | ''     | 图片 |
| tags      | string        | ''     | 标签 |

#### 1.3.3.5 创建deck表

| 字段名          | 类型          | 默认值 | 注释                               |
| --------------- | ------------- | ------ | ---------------------------------- |
| id              | bigIncrements |        |                                    |
| name            | string        |        | 牌组名                             |
| size            | string        |        | 牌组大小                           |
| icon            | string        | ''     | 牌组图标                           |
| maker_id        | bigIncrements | ''     | 内容制作者                         |
| designer_id     | bigIncrements | ''     | 模板设计者                         |
| developer_id    | bigIncrements | ‘’     | 模板开发者                         |
| show_pictures   | string        | ‘’     | 展示牌组的图片                     |
| detail_pictures | string        | ‘’     | 牌组详情的图片（第一个为牌组图标） |
| vedio           | string        | ‘’     | 卡片演示视频                       |
| description     | string        | ‘’     | 牌组简介                           |
| created_time    | timestamp     | ‘’     | 创建时间                           |
| url             | string        | ‘’     | 牌组地址                           |
| download_times  | bigIncrements | ‘’     | 下载次数                           |
| tags            | string        | ‘’     | 标签                               |

#### 1.3.3.6 创建category表

| 字段名     | 类型          | 默认值 | 注释         |
| ---------- | ------------- | ------ | ------------ |
| id         | bigIncrements |        |              |
| name       | string        | ''     | 分类名称     |
| pid        | string        | ''     | 父id         |
| manager_id | bigIncrements |        | 该类型管理员 |

#### 1.3.3.6 创建right表

| 字段名      | 类型          | 默认值 | 注释     |
| ----------- | ------------- | ------ | -------- |
| id          | bigIncrements |        |          |
| name        | string        | ''     | 权限名称 |
| description | string        | ''     | 权限描述 |

#### 1.3.3.6 创建role表

| 字段名      | 类型          | 默认值 | 注释               |
| ----------- | ------------- | ------ | ------------------ |
| id          | bigIncrements |        |                    |
| name        | string        | ''     | 角色名称           |
| right_ids   | string        | ''     | 该权限拥有的权限id |
| description | string        | ''     | 角色描述           |



# 2. 写网站后台的前端页面

项目域名：zang.ankchina.net

应用的技术： element-ui

## 2.1. 创建项目

创建项目

## 2.2. 搭建结构

搭建结构

## 2.3. 核心逻辑



# 3. 写网站前台的前端页面

项目域名：ankichina.net

应用技术： vuetify

## 3.1. 创建项目

创建项目

## 3.2. 搭建结构

搭建结构

## 3.3. 核心逻辑


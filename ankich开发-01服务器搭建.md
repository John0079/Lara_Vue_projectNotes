# 1. 先写服务端接口

项目域名： api.ankichina.net

项目git仓库：https://github.com/John0079/ankich-api.git

认证模式： passport的秘密模式

postman工具：  https://apizza.net/pro/#/ 

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

8. 修改域名

   ```
   将域名 laravel6c.com ------->  修改成  ankich-api.com
   ```
   
   
   
9. 测试接口

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

| 字段名            | 类型          | 默认值     | 注释             |
| ----------------- | ------------- | ---------- | ---------------- |
| id                | bigIncrements |            |                  |
| name              | string        |            |                  |
| email             | string        | unique()   |                  |
| email_verified_at | timestamp     |            |                  |
| password          | string        |            |                  |
| avatar            | string        | ‘’         | 头像             |
| is_active         | smallInteger  | ‘’         | 激活否？         |
| level             | smallInteger  | ‘’         | 用户等级         |
| production        | json          | nullable() | 用户在网站的贡献 |
| setting           | json          | nullable() | 用户的偏好设置   |

#### 1.3.3.2 创建paragraph表

| 字段名              | 类型          | 默认值     | 注释                  |
| ------------------- | ------------- | ---------- | --------------------- |
| id                  | bigIncrements |            |                       |
| index_code          | string        | unique()   | 索引编码              |
| title               | string        | ‘’         | 标题                  |
| title_translation   | string        | ‘’         | 标题翻译              |
| content             | string        | ‘’         | 内容                  |
| content_translation | string        | ‘’         | 内容翻译              |
| translators         | json          | nullable() | 翻译者id              |
| doc_type            | string        | ‘’         | 文档类型（安卓？ios） |
| complete_status     | smallInteger  | ‘’         | 完成状态              |

#### 1.3.3.3 创建cartoon表(视频表)

| 字段名    | 类型          | 默认值     | 注释 |
| --------- | ------------- | ---------- | ---- |
| id        | bigIncrements |            |      |
| title     | string        | ''         | 标题 |
| introduce | string        | ''         | 简介 |
| author    | string        | ''         | 作者 |
| url       | string        | unique()   | 网址 |
| picture   | string        | ''         | 图片 |
| tags      | json          | nullable() | 标签 |

#### 1.3.3.4 创建article表

| 字段名    | 类型          | 默认值     | 注释 |
| --------- | ------------- | ---------- | ---- |
| id        | bigIncrements |            |      |
| title     | string        | ''         | 标题 |
| introduce | string        | ''         | 简介 |
| author    | string        | ''         | 作者 |
| url       | string        | ''         | 网址 |
| picture   | string        | ''         | 图片 |
| tags      | json          | nullable() | 标签 |

#### 1.3.3.5 创建deck表

| 字段名          | 类型          | 默认值     | 注释           |
| --------------- | ------------- | ---------- | -------------- |
| id              | bigIncrements |            |                |
| name            | string        |            | 牌组名         |
| size            | float         |            | 牌组大小       |
| icon            | string        | ''         | 牌组图标       |
| maker_id        | bigIncrements | ''         | 内容制作者     |
| designer_id     | bigIncrements | ''         | 模板设计者     |
| developer_id    | bigIncrements | ‘’         | 模板开发者     |
| show_pictures   | string        | ‘’         | 展示牌组的图片 |
| detail_pictures | string        | ‘’         | 牌组详情的图片 |
| cartoon         | string        | ‘’         | 展示卡片的视频 |
| description     | string        | ‘’         | 牌组简介       |
| url             | string        | ‘’         | 牌组地址       |
| download_times  | bigIncrements | ‘’         | 下载次数       |
| tags            | json          | nullable() | 标签           |

#### 1.3.3.6 创建category表

| 字段名     | 类型          | 默认值 | 注释         |
| ---------- | ------------- | ------ | ------------ |
| id         | bigIncrements |        |              |
| name       | string        | ''     | 分类名称     |
| pid        | bigIncrements | ''     | 父id         |
| manager_id | bigIncrements |        | 该类型管理员 |

#### 1.3.3.7 创建right表

| 字段名      | 类型          | 默认值 | 注释     |
| ----------- | ------------- | ------ | -------- |
| id          | bigIncrements |        |          |
| name        | string        | ''     | 权限名称 |
| description | string        | ''     | 权限描述 |

#### 1.3.3.8 创建role表

| 字段名      | 类型          | 默认值     | 注释               |
| ----------- | ------------- | ---------- | ------------------ |
| id          | bigIncrements |            |                    |
| name        | string        | ''         | 角色名称           |
| right_ids   | json          | nullable() | 该权限拥有的权限id |
| description | string        | ''         | 角色描述           |

### 1.3.4 创建模型，及magration

```
1. 	php artisan make:model Paragraph -m
2.	php artisan make:model Cartoon -m
3.	php artisan make:model Article -m
4.	php artisan make:model Deck -m
5. 	php artisan make:model Category -m
6.	php artisan make:model Right -m
7.	php artisan make:model Role -m


```

### 1.3.6 迁移数据库

#### 1.3.6.1 修改迁移文件

0. 修改xxxxxxxxx_create_users_table.php

   ```
   
       public function up()
       {
           Schema::create('users', function (Blueprint $table) {
               $table->bigIncrements('id');
               $table->string('name');
               $table->string('email')->unique();
               $table->timestamp('email_verified_at')->nullable();
               $table->string('password');
               $table->string('avatar')->default('default')->comment('用户头像');
               $table->smallInteger('is_active')->default(0)->comment("用户是否激活");
               $table->smallInteger('level')->default(1)->comment('用户级别，普通用户-1，志愿者-2， 管理者-3， 高级管理者-4');
               $table->json('production')->nullable()->comment('在网站上的贡献');
               $table->json('setting')->nullable()->comment('用户设置');
               $table->rememberToken();
               $table->timestamps();
           });
       }
   ```

   

1. 修改xxxxxxxxx_create_paragraphs_table.php

   ```
   
       public function up()
       {
           Schema::create('paragraphs', function (Blueprint $table) {
               $table->bigIncrements('id');
               $table->string('index_code')->unique()->comment('序号编码');
               $table->string('title')->comment('段落标题');
               $table->string('title_translation')->comment('段落标题翻译');
               $table->text('content')->comment('段落内容');
               $table->text('content_translation')->comment('段落内容翻译');
               $table->json('translators')->nullable()->comment('翻译者，可能是多个人');
               $table->string('doc_type')->default("")->comment('指定是哪个文档anki, android, ios');
               $table->smallInteger('complete_status')->default(0)->comment('是否翻译完整');
               $table->timestamps();
           });
       }
   
   ```

   

2. 修改xxxxxxxxx_create_cartoons_table.php

   ```
   
       public function up()
       {
           Schema::create('cartoons', function (Blueprint $table) {
               $table->bigIncrements('id');
               $table->string('title')->comment('视频标题');
               $table->string('introduce')->comment('视频简介');
               $table->string('author')->comment('作者');
               $table->string('url')->unique()->comment('视频地址');
               $table->string('picture')->comment('视频插图地址');
               $table->json('tags')->nullable()->comment('视频标签');
               $table->timestamps();
           });
       }
   ```

   

3. 修改xxxxxxxxx_create_articles_table.php

   ```
   
       public function up()
       {
           Schema::create('articles', function (Blueprint $table) {
               $table->bigIncrements('id');
               $table->string('title')->comment('博文标题');
               $table->string('introduce')->comment('博文介绍');
               $table->string('author')->comment('作者');
               $table->string('url')->unique()->comment('博文地址');
               $table->string('picture')->comment('博文图标');
               $table->json('tags')->nullable()->comment('博文标签');
               $table->timestamps();
           });
       }
   ```

   

4. 修改xxxxxxxxx_create_decks_table.php

   ```
   
       public function up()
       {
           Schema::create('decks', function (Blueprint $table) {
               $table->bigIncrements('id');
               $table->string('name')->unique()->comment('牌组名称');
               $table->float('size')->comment('牌组大小');
               $table->string('icon')->comment('牌组图标');
               $table->bigInteger('maker_id')->comment('内容制作者');
               $table->bigInteger('designer_id')->comment('模板设计者');
               $table->bigInteger('developer_id')->comment('模板开发者');
               $table->string('show_pictures')->comment('展示牌组的图片');
               $table->json('detail_pictures')->comment('牌组详情的图片');
               $table->string('gif')->comment('展示卡片的动图');
               $table->string('description')->comment('牌组简介');
               $table->string('url')->comment('牌组地址');
               $table->bigInteger('download_times')->comment('下载次数');
               $table->json('tags')->nullable()->comment('牌组标签');
               $table->timestamps();
           });
       }
   ```

   

5. 修改xxxxxxxxx_create_categorys_table.php

   ```
   
       public function up()
       {
           Schema::create('categories', function (Blueprint $table) {
               $table->bigIncrements('id');
               $table->string('name')->unique()->comment('分类名称');
               $table->bigInteger('pid')->comment('父id');
               $table->bigInteger('manager_id')->comment('管理员id');
               $table->timestamps();
           });
       }
   ```

   

6. 修改xxxxxxxxx_create_rights_table.php

   ```
   
       public function up()
       {
           Schema::create('rights', function (Blueprint $table) {
               $table->bigIncrements('id');
               $table->string('name')->unique()->comment('权限名称');
               $table->string('description')->comment('权限描述');
               $table->timestamps();
           });
       }
   ```

   

7. 修改xxxxxxxxx_create_roles_table.php

   ```
   
       public function up()
       {
           Schema::create('roles', function (Blueprint $table) {
               $table->bigIncrements('id');
               $table->string('name')->unique()->comment('角色名称');
               $table->json('right_ids')->nullable()->comment('该权限拥有的权限id');
               $table->string('description')->comment('角色描述');
               $table->timestamps();
           });
       }
   ```

   

#### 1.3.6.2 迁移数据库

```
php artisan migrate

迁移完数据库，不要忘记啦
	1. 	php artisan passport:install --force
	
	2.  测试接口
		register
```



### 1.3.7 创建控制器，路由

#### 1.3.7.1 创建控制器，路由

```
0.  php artisan make:controller UserController --resource
	创建资源理由
	Route::resource('user', 'UserController');
	
1.	php artisan make:controller ParagraphController --resource
	创建资源理由
	Route::resource('paragraph', 'ParagraphController');

2.	php artisan make:controller CartoonController --resource
	创建资源理由
	Route::resource('cartoon', 'CartoonController');

3.	php artisan make:controller ArticleController --resource
	创建资源理由
	Route::resource('article', 'ArticleController');

4.	php artisan make:controller DeckController --resource
	创建资源理由
	Route::resource('deck', 'DeckController');

5.	php artisan make:controller CategoryController --resource
	创建资源理由
	Route::resource('category', 'CategoryController');

6.	php artisan make:controller RightController --resource
	创建资源理由
	Route::resource('right', 'RightController');

7.	php artisan make:controller RoleController --resource
	创建资源理由
	Route::resource('role', 'RoleController');



```

#### 1.3.7.2 资源路由，详细

| 序号 | 动作      | url             | 行为    | 路由名称     | 注释           |
| ---- | --------- | --------------- | ------- | ------------ | -------------- |
| 1    | get       | /user           | index   | user.index   | 获取表全部记录 |
| 2    | get       | /user/{id}      | show    | user.show    | 查询某一记录   |
| 3    | get       | /user/create    | create  | user.create  | 创建单个记录   |
| 4(*) | put/patch | /user/{id}      | update  | user.update  | 更新一条记录   |
| 5    | get       | /user/{id}/edit | edit    | user.edit    | 编辑一条记录   |
| 6(*) | post      | /user           | store   | user.store   | 存储记录       |
| 7    | delete    | /user/{id}      | destroy | user.destroy | 删除一条记录   |

#### 1.3.7.3 查看路由的命令：

```
php artisan route:list
```

# 2. 写前端服务接口

## 2.1. 创建控制器

### 2.1.1. 创建一个获取翻译段落内容的控制器

```
0.  php artisan make:controller front/MamualController
	创建资源理由
	
```













# 3. 遇到的大坑

## 3.1. json字段的处理问题：

参考博文：  https://www.jianshu.com/p/fe2e753a5d5f 

重点：数据库定义了json字段，则要在model中进行声明哟！！！

```
class JsonDemo extends Model
{
    protected $table = 'json_demo';

    protected $guarded = ['id'];

    protected $casts = [
        'attr' => 'json', // 声明json类型
    ];
}
```


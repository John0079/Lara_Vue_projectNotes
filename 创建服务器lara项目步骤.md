### 1. 所有这些步骤，都是参照leon的网站：

https://qianjinyike.com/laravel-passport-%e5%af%86%e7%a0%81%e6%a8%a1%e5%bc%8f/

### 2. 创建项目
    composer create-project --prefer-dist laravel/laravel ankich-api
  (为提高效率，可从ankich1-aa---fro-laravel.zip文件中解压出来)
### 3. 修改默认数据字符串长度：

（在AppServiceProvider.php文件中）

    public function boot()
    {
        //
        Schema::defaultStringLength(191);
    }

### 4. 通过.env配置数据库
    DB_DATABASE=ankich-api
### 5. 创建数据库ankich-api
### 6. 创建BaseRequest文件
    php artisan make:request BaseRequest

### 7. 修改BaseRequest文件
    <?php
    
    namespace App\Http\Requests;
    
    use Illuminate\Http\Request;
    
    class BaseRequest extends Request
    {
    
        public function expectsJson()
        {
            return true;
        }
        public function wantsJson()
        {
            return true;
        }
    }

### 8. 修改index.php出口文件
    // index.php
    $response = $kernel->handle(
        $request = \App\Http\Requests\BaseRequest::capture()
    );

### 9. 创建PassportController
    php artisan make:controller PassportController
### 10. 安装laravel的包passport
    cd ankich-api
    composer require laravel/passport
### 11. 迁移数据库
    php artisan migrate
### 12. 生成加密access_token的key
    php artisan passport:install
### 13. 在App\User 模型中修改

添加Laravel\Passport\HasApiTokens（注意：要手敲）

### 14. 安装laravel包guzzle
    composer require guzzlehttp/guzzle
### 15. 修改~/config/auth.php配置文件
    'defaults' => [
        'guard' => 'api',
        'passwords' => 'users',
    ],
    
    'guards' => [
        'web' => [
            'driver' => 'session',
            'provider' => 'users',
        ],
    
        'api' => [
            'driver' => 'passport',
            'provider' => 'users',
            'hash' => false,
        ],
    ],
### 16. 设置 token 过期时间

在AuthServiceProvider 中的boot方法中设置 token 过期时间

    public function boot()
    {
        $this->registerPolicies();
    
        Passport::tokensExpireIn(now()->addDays(15)); // access_token 过期时间
        Passport::refreshTokensExpireIn(now()->addDays(60)); // refresh_token 过期时间
    
        //
    }
### 17. 修改api路由 api.php如下：
    Route::post('/oauth/token', '\Laravel\Passport\Http\Controllers\AccessTokenController@issueToken');


    Route::post('/register', 'PassportController@register');
    Route::post('/login', 'PassportController@login');
    Route::post('/refresh', 'PassportController@refresh');
    Route::post('/logout', 'PassportController@logout');


    Route::get('test', function () {
        return 'ok';
    })->middleware('auth');

### 18. 修改PassportController文件
      <?php
      namespace App\Http\Controllers;
    
      use App\User;
      use GuzzleHttp\Client;
      use Illuminate\Http\Request;
      use Illuminate\Support\Facades\Validator;
    
      class PassportController extends Controller
      {
          protected $clientId;
          protected $clientSecret;
    
          public function __construct()
          {
              $this->middleware('auth')->except('login', 'register', 'refresh');
              $client = \DB::table('oauth_clients')->where('id', 2)->first();
              $this->clientId = $client->id;
              $this->clientSecret = $client->secret;
          }
    
          protected function username()
          {
              return 'email';
          }
    
          public function register()
          {
              $this->validator(request()->all())->validate();
    
              $this->create(request()->all());
    
              return $this->getToken();
          }
    
          protected function validator(array $data)
          {
              return Validator::make($data, [
                  'name' => ['required', 'string', 'max:255', 'unique:users',],
                  'email' => ['required', 'string', 'email', 'max:255',],
                  'password' => ['required', 'string', 'min:8', 'confirmed'],
              ]);
          }
    
          protected function create(array $data)
          {
              return User::forceCreate([
                  'name' => $data['name'],
                  'email' => $data['email'],
                  'password' => password_hash($data['password'], PASSWORD_DEFAULT),
              ]);
          }
    
      //    public function logout(Request $request)
      //    {
      //        auth()->user()->token()->revoke(); // 只会使 access_token 失效
      //
      //        return ['message' => '退出登录成功'];
      //    }


          public function logout()
          {
              $tokenModel = auth()->user()->token();
              $tokenModel->update([
                  'revoked' => 1,
              ]);
    
              \DB::table('oauth_refresh_tokens')
                  ->where(['access_token_id' => $tokenModel->id])->update([
                      'revoked' => 1,
                  ]);
    
              return ['message' => '退出登录成功'];
          }
    
          public function login()
          {
              $user = User::where($this->username(), request($this->username()))
                  ->firstOrFail();
    
              if (!password_verify(request('password'), $user->password)) {
                  return response()->json(['error' => '抱歉，账号名或者密码错误！'],
                      403);
              }
    
              return $this->getToken();
          }
    
          public function refresh()
          {
              $response = (new Client())->post('http://lishen.com/api/oauth/token', [
                  'form_params' => [
                      'grant_type' => 'refresh_token',
                      'refresh_token' => request('refresh_token'),
                      'client_id' => $this->clientId,
                      'client_secret' => $this->clientSecret,
                      'scope' => '*',
                  ],
              ]);
    
              return $response;
          }
    
          /**
          * @param Request $request
          * @param Client  $guzzle
          *
          * @return \Psr\Http\Message\ResponseInterface
          */
          private function getToken()
          {
              $response = (new Client())->post('http://lishen.com/api/oauth/token', [
                  'form_params' => [
                      'grant_type' => 'password',
                      'username' => request('email'),
                      'password' => request('password'),
                      'client_id' => $this->clientId,
                      'client_secret' => $this->clientSecret,
                      'scope' => '*',
                  ],
              ]);
    
              return $response;
          }
      }
### 19. 注册scope 在AppServicePrivider中注册
    public function register()
    {
        //
        Passport::tokensCan([
            'test1' => 'for test1',
            'test2' => 'for test2',
        ]);
    }

### 20. 注册scope的中间件 

在Http/kernel.php文件中的 $routeMiddleware 属性中追加两行

    protected $routeMiddleware = [
        'auth' => \App\Http\Middleware\Authenticate::class,
        'auth.basic' => \Illuminate\Auth\Middleware\AuthenticateWithBasicAuth::class,
        'bindings' => \Illuminate\Routing\Middleware\SubstituteBindings::class,
        'cache.headers' => \Illuminate\Http\Middleware\SetCacheHeaders::class,
        'can' => \Illuminate\Auth\Middleware\Authorize::class,
        'guest' => \App\Http\Middleware\RedirectIfAuthenticated::class,
        'password.confirm' => \Illuminate\Auth\Middleware\RequirePassword::class,
        'signed' => \Illuminate\Routing\Middleware\ValidateSignature::class,
        'throttle' => \Illuminate\Routing\Middleware\ThrottleRequests::class,
        'verified' => \Illuminate\Auth\Middleware\EnsureEmailIsVerified::class,
        'scopes' => \Laravel\Passport\Http\Middleware\CheckScopes::class,  // and
        'scope' => \Laravel\Passport\Http\Middleware\CheckForAnyScope::class,  // or
    ];
### 21. 使用scope，第一个中方式：
    Route::get('test', function () {
        return 'ok';
    })->middleware('scopes:test2');

### 22. 使用scope, 第二种方式：
    Route::get('test', function () {
        if(auth()->user()->tokenCan('test1')){
            return "123";
        }
    })->middleware('auth');

### 23. scope设置在哪里呢？ 

在PassportContrller.php的 getToken方法中

    private function getToken()
    {
        $response = (new Client())->post('http://laravel6c.com/api/oauth/token', [
            'form_params' => [
                'grant_type' => 'password',
                'username' => request('email'),
                'password' => request('password'),
                'client_id' => $this->clientId,
                'client_secret' => $this->clientSecret,
                'scope' => 'test1',
            ],
        ]);
    
        return $response;
    }

### 24. scope的其他操作

    if (auth()->user()->tokenCan('place-orders')) {
        //
    }
    
    Laravel\Passport\Passport::scopeIds(); // ["test1","test2"]
    
    Laravel\Passport\Passport::scopes(); // [{"id":"test1","description":"for test1"},{"id":"test2","description":"for test2"}]
    
    Laravel\Passport\Passport::scopesFor(['test1', 'check-status']); // [{"id":"test1","description":"for test1"}]
    
    Laravel\Passport\Passport::hasScope('place-orders'); // false

### 25. scope使用请注意：
  当更新access_token的时候，scope的参数要与登陆的时候scope的参数一致
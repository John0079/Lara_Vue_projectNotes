# 1. 时间date的比较

在这里获取了时间

![1580120491016](C:\Users\Honghu009\AppData\Roaming\Typora\typora-user-images\1580120491016.png)

这个时间怎么在服务端比较，然后获得到这个日期后的所有记录

# 2. laravel创建一条记录的流程

直接用get方法，传递参数即可，请求create接口

## 2.1. 客户端的代码

```

  // 新增会员
  addNewMember(token, pojo) {
    let theUrl = '/api/user/create?'
    for (const key of Object.keys(pojo)) {
      theUrl += key
      theUrl += '='
      theUrl += pojo[key]
      theUrl += '&'
    }

    return request({
      url: theUrl,
      method: 'get',
      data: pojo,
      headers: {
        Authorization: `Bearer ${token}`
      }
    })
  }
```

## 2.2. 服务端代码

```

    public function create()
    {
        //
        $requestData = \request()->all();
        $info = User::forceCreate([
            'name' => $requestData['name'],
            'email' => $requestData['email'],
            'password' => password_hash($requestData['password'], PASSWORD_DEFAULT),
            'level' => $requestData['level'],
        ]);


        return response($info);
    }
```



# 3. Put方法不被允许怎么办？

## 3.1. 错误提示

![1580153564358](C:\Users\Honghu009\AppData\Roaming\Typora\typora-user-images\1580153564358.png)

## 3.2. 解决办法

![1580155528273](C:\Users\Honghu009\AppData\Roaming\Typora\typora-user-images\1580155528273.png)



# 3. 再想想。。。。。。。。


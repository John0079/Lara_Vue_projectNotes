# 1. 客户端api 接口

## 1.1. 拿到数据

```

  // 通过ID查询会员信息
  getMemberByIdto(token, id) {
    return request({
      url: `/api/user/${id}`,
      method: 'get',
      data: {},
      headers: {
        Authorization: `Bearer ${token}`
      }
    })
  },

```

## 1.2. 更新数据

```

  // 更新数据
  updateMember(token, id, pojo) {
    return request({
      url: `/api/user/${id}`,
      method: 'put',
      data: pojo,
      headers: {
        Authorization: `Bearer ${token}`
      }
    })
  }

```



# 2. 服务端api接口

## 2.1. 给他数据

```

    public function show($id)
    {
        //1. 判断当前登陆用户
        $user = Auth::user();
        $userId = $user['id'];
        if ($userId == 4) {
            $user = \App\User::find($id);
            return $user;
        } else {
            return $user;
        }
    }
```

## 2.2. 更新数据

```

    public function update(Request $request, $id)
    {
        $password = $request['password'];
        if($password){
            $rs = DB::table('users')
                ->where('id', $id)
                ->update([
                    'name' => $request['name'],
                    'email' => $request['email'],
                    'password' => password_hash($request['password'], PASSWORD_DEFAULT),
                    'level' => $request['level'],
                ]);
            return $rs;
        }else{
            $rs = DB::table('users')
                ->where('id', $id)
                ->update([
                    'name' => $request['name'],
                    'email' => $request['email'],
                    'level' => $request['level'],
                ]);
            return $rs;
        }
    }

```


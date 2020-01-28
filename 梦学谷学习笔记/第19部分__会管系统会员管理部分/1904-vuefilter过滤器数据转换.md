

# 1. es6的箭头函数演变

## 1.1 原始函数

```
const memberLevels = [
  { type: 0, name: '普通用户' },
  { type: 1, name: '志愿者' },
  { type: 2, name: '管理者' },
  { type: 3, name: '高级管理者' }
]

//即 Array的find函数，它的参数是一个function, 只要这个function的值返回是true,那么就找到需要找的哪个元素啦。

memberLevelFilter(type) {
	memberLevels.find( function(obj) {
		return obj.type === type
	})
}
```

## 1.2 箭头函数

```

memberLevelFilter(type) {
	memberLevels.find( (obj) => {
		return obj.type === type
	})
}
```

## 1.3 箭头函数再简写（因为箭头函数内只有一行代码）

```

memberLevelFilter(type) {
	memberLevels.find( (obj) => return obj.type === type )
}
```



# 2. vue的过滤器使用。

## 2.1 定义一个过滤器

```
const memberLevels = [
  { type: 0, name: '普通用户' },
  { type: 1, name: '志愿者' },
  { type: 2, name: '管理者' },
  { type: 3, name: '高级管理者' }
]

。。。。。。。。。。。。。。。。。。。。。。。。。

  filters: {
    memberLevelFilter(type) {
      // 注意过滤器中不能引用当前vue实例的this,因此memberLevels必须定义在vue外层
      const levelObj = memberLevels.find((obj) => obj.type === type)
      return levelObj ? levelObj.name : null
    }
  }

```

## 2.2. 过滤器使用方法

要在template中 

```
//使用标准
值 | 过滤器

//使用演示
<span>{{ scope.row.level | memberLevelFilter }}</span>
```

## 2.3. 使用实例

```
      <el-table-column prop="level" label="会员等级" width="100">
        <template slot-scope="scope">
          <span>{{ scope.row.level | memberLevelFilter }}</span>
        </template>
      </el-table-column>
```

# 3. 过滤器里面不能用this

```
//这里是指：
// 注意过滤器中不能引用当前vue实例的this,因此memberLevels必须定义在vue外层
```


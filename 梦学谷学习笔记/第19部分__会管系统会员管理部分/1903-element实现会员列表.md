# 1. 引入element-ui的表

引入表格的代码

```

    <el-table :data="list" border style="width: 100%">
      <el-table-column type="index" label="序号" width="80"> </el-table-column>
      <el-table-column prop="id" label="id" width="80"> </el-table-column>
      <el-table-column prop="name" label="姓名" width="100"> </el-table-column>
      <el-table-column prop="email" label="email" width="180">
      </el-table-column>
      <el-table-column prop="is_active" label="激活否" width="70">
      </el-table-column>
      <el-table-column prop="level" label="会员等级" width="100">
      </el-table-column>
      <el-table-column prop="created_at" label="注册时间"> </el-table-column>
    </el-table>
```

# 2. 表格数据的序号，怎么得到？

使用 index ， type="index"

```
<el-table-column type="index" label="序号" width="80"> </el-table-column>
```



# 3. 表格中添加操作列，

```

      <el-table-column label="操作">
        <template slot-scope="scope">
          <el-button size="mini" @click="handleEdit(scope.$index, scope.row)"
            >编辑</el-button
          >
          <el-button
            size="mini"
            type="danger"
            @click="handleDelete(scope.$index, scope.row)"
            >删除</el-button
          >
        </template>
      </el-table-column>
```

## 3.1. 这里有个socpe对象

@click="handleEdit(scope.$index, scope.row)

## 3.2. 获取当前行的数据

```
//它将获得所在行的raw数据，比如，id, name, email等
scope.row

//例如：
const id = scope.row.id
const email = scope.row.email
```

## 3.3. 获取当前行的索引

```
scope.$index
```


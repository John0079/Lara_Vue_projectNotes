# 1. 实现分页的代码

```

    <el-pagination
      @size-change="handleSizeChange"
      @current-change="handleCurrentChange"
      :current-page="currentPage"
      :page-sizes="pageSizes"
      :page-size="pageSize"
      layout="total, sizes, prev, pager, next, jumper"
      :total="total"
    >
    </el-pagination>
```

## 1.1. 原理

总条目数total,  

每页的条目数page-size

每页的条目数可以选择 page-sizes, 默认值是一个数组[50, 100, 200, 400]

有了total和page-size就可以得到<1 2 3 4 5 6....>这样的数码标签了

## 1.2. total

总条目数

## 1.3. page-size

每页的条目数

## 1.4. page-sizes

每页的条目数，可选参数

默认值给 [50, 100, 200, 400]，即表示每页显示50个条目，每页显示100个条目，每页显示200个条目，或是每页显示400个条目，这个将会以下拉框的形式渲染，让用户选择
# 1. 点击删除弹出--确认消息

## 1.1. 代码

```
<template>
  <el-button type="text" @click="open2">点击打开 Message Box</el-button>
</template>

<script>
  export default {
    methods: {
      open2() {
        this.$confirm('此操作将永久删除该文件, 是否继续?', '提示', {
          confirmButtonText: '确定',
          cancelButtonText: '取消',
          type: 'warning'
        }).then(() => {
          this.$message({
            type: 'success',
            message: '删除成功!'
          });
        }).catch(() => {
          this.$message({
            type: 'info',
            message: '已取消删除'
          });          
        });
      }
    }
  }
</script>
```

## 1.2. 关键

关键是js代码，写一个方法就可以啦


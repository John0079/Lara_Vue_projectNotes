# 1. 引入element-ui的对话框

## 1.1.嵌套form表单的代码

```

<el-dialog title="收货地址" :visible.sync="dialogFormVisible">
  <el-form :model="form">
    <el-form-item label="活动名称" :label-width="formLabelWidth">
      <el-input v-model="form.name" auto-complete="off"></el-input>
    </el-form-item>
    <el-form-item label="活动区域" :label-width="formLabelWidth">
      <el-select v-model="form.region" placeholder="请选择活动区域">
        <el-option label="区域一" value="shanghai"></el-option>
        <el-option label="区域二" value="beijing"></el-option>
      </el-select>
    </el-form-item>
  </el-form>
  <div slot="footer" class="dialog-footer">
    <el-button @click="dialogFormVisible = false">取 消</el-button>
    <el-button type="primary" @click="dialogFormVisible = false">确 定</el-button>
  </div>
</el-dialog>


```

## 1.2 基本用法

1. 需要设置`visible`属性，它接收`Boolean`，当为`true`时显示 Dialog。
2. Dialog 分为两个部分：`body`和`footer`，`footer`需要具名为`footer`的`slot`。
3. `title`属性用于定义标题，它是可选的，默认值为空。
4. 最后，还有before-close的用法。 

 

# 2. 注意要点

## 2.1. 设置对话框宽度

用width="500px", 代码如下：

```
<el-dialog title="新增会员" :visible.sync="dialogFormVisible" width="500px">
```

## 2.2. 设置el-form宽度

用style

```
      <el-form
        ref="pojoForm"
        label-width="100px"
        label-position="right"
        style="width: 400px;"
        :model="pojo"
      >
```


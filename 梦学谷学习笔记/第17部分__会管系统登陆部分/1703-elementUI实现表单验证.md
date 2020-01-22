# 1. 表单验证步骤

## 1.1. el-form节点添加 rules属性

```
<el-form ref="form" :rules="rules" :model="form" label-width="80px" class="login-form">
```

## 1.2. data里添加 rules数据

```
data() {
      return {
        rules: {
          name: [
            { required: true, message: '请输入活动名称', trigger: 'blur' },
            { min: 3, max: 5, message: '长度在 3 到 5 个字符', trigger: 'blur' }
          ],
          region: [
            { required: true, message: '请选择活动区域', trigger: 'change' }
          ],
        }
      };
    },
```

## 1.3. el-form-item节点添加 prop属性

```
<el-form :model="ruleForm" :rules="rules" ref="ruleForm" label-width="100px" class="demo-ruleForm">
  <el-form-item label="活动名称" prop="name">
    <el-input v-model="ruleForm.name"></el-input>
  </el-form-item>
</el-form>
```

## 1.4. 测试校验方法（）

```

    submitForm(formName) {
      this.$refs[formName].validate((valid) => {
        if (valid) {
          alert('good')
        } else {
          alert('bad')
        }
      })
    }
```



# 2 error容易错误的地方



## 2.1 是prop属性-----prop属性-----prop属性

是在el-form-item里面添加”prop“属性，而不是”:prop“属性


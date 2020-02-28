# 1. 不同环境变量的配置：

## 1.1. 配置依据

```
我们有一个全局的环境变量 process.env.NODE_ENV，默认情况下，这个变量的值要么是 production，要么是 development，分别表示生产环境和开发环境。

具体使用：
    if (process.env.NODE_ENV === 'development') {
      this.textData = '这是开发-开发开发开发--环境'
    } else if (process.env.NODE_ENV === 'production') {
      this.textData = '这是shengshengsheng生产环境'
    }
    
```


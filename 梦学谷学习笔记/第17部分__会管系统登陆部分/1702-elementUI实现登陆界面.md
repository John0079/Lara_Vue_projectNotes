# 1. 让form窗口居中的css代码样式：

```
.login-form {
	width: 350px;
	margin: 160px auto;
}
.login-container {
	position: absolute;
	width: 100%
	height: 100%;
}
```

# 2. nuxt.js的css样式背景图片设置

```
//背景图片的位置：
  ~/static/image/login.jpg
//在css中引用的方式
.login-container {
	position: absolute;
	width: 100%
	height: 100%;
  	background: url('/image/login.jpg');
}
```

# 3. 兼顾login界面的布局-default.vue

```
//template部分
<template>
  <div>
    <app-header v-if="showHeader"></app-header>
    <app-navbar v-if="showNavbar"></app-navbar>
    <div id="main" ref="main">
      <nuxt />
    </div>
  </div>
</template>

//js核心部分

  data() {
    return {
      showHeader: true,
      showNavbar: true
    }
  },
  mounted() {
    const routePath = this.$route.path.slice(1)
    if (routePath === 'login') {
      this.showHeader = false
      this.showNavbar = false
      this.$refs.main.style.top = '0px'
      this.$refs.main.style.left = '0px'
    }
  },
  
```

# 4. 半透明背景的设置

```

.login-form {
  width: 350px;
  margin: 160px auto;
  background-color: rgb(255, 255, 255, 0.8);
  padding: 30px;
  border-radius: 20px;
}
```


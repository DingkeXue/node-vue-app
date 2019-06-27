# node-vue-app

# 基于 node、vue 实现的一个程序猿交友网。
# 主要涉及到的技术有 vue vuex vue-router axios bootstarp 等
# 特点：可以实现一般网站的登录注册（带验证）、留言和管理留言、查看用户详情、修改个人信息、等功能，并将页面模块化，便于维护。
# 难点：需要使用 keep-alive 来保持跳转页面不刷新。修改个人信息时既要提交相关操作还要更新 vuex 中的数据。检测当前用户来决定是否显示删除等操作。

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run dev
```

### Compiles and minifies for production
```
npm run build
```

### Run your tests
```
npm run test
```

### Lints and fixes files
```
npm run lint
```

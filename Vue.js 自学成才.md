# Vue.js 自学成才

#### vue的入口

vue的入口即为main.js文件，他引入了一个项目所有需要用到的文件，即把资源整合到了一起。

#### App.vue作用

app.vue可以当做是网站首页，是一个vue项目的主组件，页面入口文件 ，所有页面都是在App.vue下进行切换的。是整个项目的关键，app.vue负责构建定义及页面组件归集。

#### vue跑项目命令

```
//主要看项目内的package.json里有serve还是dev
npm run serve
npm run dev
```

#### vue-cli创建项目命令

在对应的文件夹cmd下敲vue ui即可

#### vue安装less

npm install --save less less-loader

注：less是一种css预编译器，非常强大，但这里可能出现问题，因为有可能less-loader的版本太新了不兼容，所以建议less-loader换成npm install less-loader@5.0.0


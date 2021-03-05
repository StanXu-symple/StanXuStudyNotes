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

------

### vuex组件

vuex是一个专门为vue.js应用程序开发的状态管理模式

这个模式我们可以理解为在data中的属性，需要共享给其他组件使用的部分

也就是说，是我们需要共享的data,使用vuex进行统一集中式管理

#### **vuex中，有默认的五种基本的对象：**

- state：存储状态（变量）
- getters：对数据获取之前的再次编译，可以理解为state的计算属性。我们在组件中使用 $sotre.getters.fun()
- mutations：修改状态，并且是同步的。在组件中使用$store.commit('',params)。这个和我们组件中的自定义事件类似。
- actions：异步操作。在组件中使用是$store.dispath('')
- modules：store的子模块，为了开发大型项目，方便状态管理而使用的。这里我们就不解释了，用起来和上面的一样。

#### this.$store.dispatch() 与 this.$store.commit()方法的区别

目前我接触到的调用vuex里的actions和mutations属性是标题的两种方式，发现commit适合mutations属性，而dispatch适合commit属性，原因是actions是异步操作，mutations是同步操作         

   而：

commit: 同步操作

dispatch: 异步操作

#### vuex actions方法区参数约定

1.vuex中actions方法去第一个参数是约定好的，第二个是用户自定义的(如果有)。第一个参数为:context,即：store的对象context,如果想限定只能使用context中的属性或者方法，则需要使用{}来限定，如:{commit}

2.Promise可以将异步方法按一定的顺序执行，其自带2个参数。参数一：resolve正确返回后使用的参数，reject为异步函数调用失败后的调用参数

3.vuex中的multation同理，第一个参数为state

------

#### vue对于components文件夹和views文件夹的思考

入门vue，看到这两个文件夹感觉没什么差别，但个人仔细一想，其中的细节还是有必要记录一下，我个人认为components存放的是每一个单独的组件，而views则是每个组件的入口，为主界面，通过main.js加上router来路由到views，在views导入每个单独的组件再组成一个页面，这样想来设计非常合理!


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

## vue跨域问题

妈的，困扰了我五个小时的跨域问题，在第二天地铁上找到了解决方案，可让我好找啊兄弟！

### 什么是跨域

```
在浏览器里面域名、端口、ip地址、协议、有任何一项不同，则称为跨域
例如：A网站：http://localhost:8080/#/
	 B网站：http://localhost:8081/#/
处理跨域的方式？
JsonP(只能处理get请求),cors(后端开启),代理服务器
```

### vue代理服务器解决跨域

#### 1.安装webpack-dev-server

```vue
npm install webpack-dev-server  --save
```

#### 2.为webpack-dev-server配置devServer.proxy

```js
//1.在vue项目目录下新建vue.config.js文件，里面我们可以进行自定义配置
//2.在vue.config.js里配置devServer.proxy
代码如下：
devServer:{
        host:'localhost',    //指定要使用的主机
        port:'8084',		//端口号
        proxy:{
        //配置不同的后台API地址
        /*前缀为/api的方法则需要代理，如http://localhost:8084/api/test*/
            '/api':{   
                target:'http://localhost:8081', /*代理路径，服务器去请求的真正地址*/
                changeOrigin:true   //是否开启代理，true为开启,false关闭
            }
        }
    }
```

#### 总结

vue跨域问题是一个非常常规的开发时问题，由于跨域请求不到数据是常有的事，也非常容易解决(不论是前端解决还是后端解决)，这里只写了前端解决方法，而困扰我五个小时的原因是因为我真的蠢，没有安装webpack-dev-server就想配置它的属性，因此一个小的错误便困扰我许久，加油吧

## Vue CLI4 vue.config.js标准配置

```js
// const path = require('path');
// const CompressionWebpackPlugin = require("compression-webpack-plugin"); // 开启gzip压缩， 按需引用
// const productionGzipExtensions = /\.(js|css|json|txt|html|ico|svg)(\?.*)?$/i; // 开启gzip压缩， 按需写入
// const BundleAnalyzerPlugin = require("webpack-bundle-analyzer").BundleAnalyzerPlugin; // 打包分析
// const IS_PROD = ['production', 'prod'].includes(process.env.NODE_ENV);
// const resolve = (dir) => path.join(__dirname, dir);

module.exports = {
  // baseUrl:"",//从 Vue CLI 3.3 起已弃用，使用blicPath
  /**
   * 设置项目的基路径,设置process.env.BASE_URL
   * 例如：http://192.168.43.243:8080  ==>  http://192.168.43.243:8080/test
   * 默认：'/'
   * 注意：使用 publicPath 而不要直接修改 webpack 的 output.publicPath
   */
  publicPath: '/',
  /**
   * vue-cli-service build 时生成的生产环境构建文件的目录
   * 默认：'dist'
   * 默认删除构建目录，--no-clean可消除行为
   * 注意：使用 outputDir 而不要修改 webpack 的 output.path
   */
  outputDir: 'dist',
  /**
   * 放置生成的静态资源 (js、css、img、fonts) 的 (相对于 outputDir 的) 目录
   * 默认：''
   */
  assetsDir: '',
  /**
   * 指定生成的 index.html 的输出路径 (相对于 outputDir)
   * 默认：'index.html'
   */
  indexPath: 'index.html',
  /**
   * 生成的静态资源在它们的文件名中包含了 hash 以便更好的控制缓存
   * 例如：true==>app.e2713bb0.css        false==>app.css
   * 默认:true
   */
  filenameHashing: true,
  pages: undefined,
  lintOnSave: false, // 在保存后eslint检查代码。将值设置为'error'是把错误直接输出为编译错误。process.env.NODE_ENV !== 'production'，在生产环境上设为false。
  transpileDependencies: [],
  /**
   * 是否生成.map文件`
   * 默认：true
   * 开发环境设置为false加速开发
   * 发布环境设置为true
   * .map文件作用：项目打包后，代码都是经过压缩加密的，如果运行时报错，输出的错误信息无法准确得知是哪里的代码报错
   */
  productionSourceMap: false,
  /**
   * 设置生成的 HTML 中 <link> 和 <script> 标签的 crossorigin 属性
   * 默认：undefined
   */
  crossorigin: undefined,
  /**
   * 在生成的 HTML 中的 <link> 和 <script> 标签上启用 Subresource Integrity (SRI)
   * 默认：false
   */
  integrity: true,
  /**
   * 配置webpack(简单配置)
   */

  // chainWebpack: (config) => {
  //   // 添加别名
  //   config.resolve.alias
  //     .set('@', resolve('src'))
  //     .set('src', resolve('src'))
  //     .set('common', resolve('src/common'))
  //     .set('components', resolve('src/components'));
  //   // 压缩图片
  //   // 需要 npm i -D image-webpack-loader
  //   config.module
  //     .rule('images')
  //     .use('image-webpack-loader')
  //     .loader('image-webpack-loader')
  //     .options({
  //       mozjpeg: { progressive: true, quality: 65 },
  //       optipng: { enabled: false },
  //       pngquant: { quality: [0.65, 0.9], speed: 4 },
  //       gifsicle: { interlaced: false },
  //       webp: { quality: 75 },
  //     });
  //   // 打包分析, 打包之后自动生成一个名叫report.html文件(可忽视)
  //   if (IS_PROD) {
  //     config.plugin('webpack-report').use(BundleAnalyzerPlugin, [
  //       {
  //         analyzerMode: 'static',
  //       },
  //     ]);
  //   }
  // },
  // configureWebpack: (config) => {
  //   // 开启 gzip 压缩
  //   // 需要 npm i -D compression-webpack-plugin
  //   const plugins = [];
  //   if (IS_PROD) {
  //     plugins.push(
  //       new CompressionWebpackPlugin({
  //         filename: '[path].gz[query]',
  //         algorithm: 'gzip',
  //         test: productionGzipExtensions,
  //         threshold: 10240,
  //         minRatio: 0.8,
  //       })
  //     );
  //   }
  //   config.plugins = [...config.plugins, ...plugins];
  // },
  /**
   * 配置webpack(链式操作)
   */
  // chainWebpack:{},
  /**
   * css配置
   * css.modules:
   * css.extract:
   * css.sourceMap:是否生成css.map文件
   * css.loaderOptions:
   */
  css: {
    modules: false,
    extract: true,
    sourceMap: true,
    loaderOptions: {
      //配置全局scss变量或者mixin....
      sass: {
        // data: `@import "@/global.scss";`
      },
      // 给 less-loader 传递 Less.js 相关选项
      // less: {
      //   // `globalVars` 定义全局对象，可加入全局变量
      //   globalVars: {
      //     primary: '#333',
      //   },
      //   lessOptions: {
      //     modifyVars: {
      //       'primary-color': 'pink',
      //       'link-color': '#pink',
      //       'border-radius-base': '2px',
      //     },
      //     javascriptEnabled: true,
      //   },
      // },
    },
  },
  /**
   * webpack-dev-server配置
   * devServer.proxy:
   */
  devServer: {
    open: false, //配置自动启动浏览器
    hot: true, // 热模块替换，就是热更新页面
    compress: true, // 为所服务的一切启用gzip压缩
    host: '0.0.0.0', // 指定要使用的主机。默认情况下这是localhost。
    port: 8080, // 端口号，
    // 所有 webpack-dev-server 的选项都支持。注意：
    // 有些值像 host、port 和 https 可能会被命令行参数覆写。
    // 有些值像 publicPath 和 historyApiFallback 不应该被修改，因为它们需要和开发服务器的 publicPath 同步以保障正常的工作。
    // proxy:"url地址",// 前端应用和后台API服务没有运行在一个主机上，设置此项在开发环境下代理到API服务器。
    // proxy: 'http://localhost:8080'  // 配置跨域处理,只有一个代理
    //配置多个跨域
    proxy: {
      // 配置不同的后台API地址
      '/http://a.itying.com': {
        target: 'http://a.itying.com',
        ws: true,
        changeOrigin: true,
        pathRewrite: {
          '^/http://a.itying.com': '',
        },
      },
      '/foo': {
        target: '<other_url>',
      },
    },
  },
  // parallel:require('os').cpus().length > 1,
  // pwa:{},
  // pluginOptions:{}
};


```


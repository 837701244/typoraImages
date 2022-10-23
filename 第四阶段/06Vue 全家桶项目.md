## 创建 Vue 全家桶项目

### 脚手架 Vue CLI

可以先通过以下命令查看本机电脑中是否有安装过 Vue CLI：

```
vue --version
# @vue/cli 4.5.13
```

如果本机电脑中没有安装 Vue CLI，可以通过以下命令来安装：

```js
npm i -g @vue/cli
```

###  创建 Vue 项目

将终端路径定位到需要创建项目的目录，执行以下命令创建 Vue 项目：

最好小写

```js
vue create vue-system
```

###  选择安装模式

```js
? Please pick a preset:
  Default ([Vue 2] babel, eslint)
  Default (Vue 3) ([Vue 3] babel, eslint)
> Manually select features
```

选择最后一个，自定义安装模式。

### 4. 选择项目插件

```js
? Check the features needed for your project:
 ( ) Choose Vue version
 (*) Babel//es6高级语法转换为低点的语法
 ( ) TypeScript
 ( ) Progressive Web App (PWA) Support
 (*) Router//路由插件
 (*) Vuex//状态机
>(*) CSS Pre-processors//css预处理器
 ( ) Linter / Formatter
 ( ) Unit Testing
 ( ) E2E Testing
```

### 5. 选择路由模式

```js
? Use history mode for router? (Requires proper server setup for index fallback in production) (Y/n) n
```

Vue Router 路由模式分为：history 和 hash。

### 6. 选择 CSS 预处理器

```js
? Pick a CSS pre-processor (PostCSS, Autoprefixer and CSS Modules are supported by default): 
> Sass/SCSS (with dart-sass)
  Sass/SCSS (with node-sass)
  Less
  Stylus
```

### 7. 选择配置代码位置

```js
? Where do you prefer placing config for Babel, ESLint, etc.? (Use arrow keys)> In dedicated config files  In package.json? Where do you prefer placing config for Babel, ESLint, etc.? (Use arrow keys)
> In dedicated config files
  In package.json
```

### 8. 是否保存设置

```js
? Save this as a preset for future projects? (y/N) y
? Save preset as: Vue-All
```

### 9. 开始创建项目

### 10. 启动项目

项目创建完成后，终端进入到项目根目录，执行项目启动命令启动项目。

#### 项目启动命令

Vue 项目的默认启动命令是 `npm run serve`，如果发生改变，可以查看 `package.json` 文件以下属性：

```json
{
    "scripts": {
        "serve": "vue-cli-service serve",
        "build": "vue-cli-service build"
    },
}
```

scripts 属性用来配置项目操作命令。

## 后台EXPRESS  数据库版本对应的操作

- 数据库版本 mongodb  `mongod -version`

- 注意数据库版本与对应的mongodb版本 [参考](https://mongoosejs.com/docs/compatibility.html#mongodb-server-version-compatibility)

```js
MongoDB Server 2.4.x: mongoose ^3.8 or 4.x
MongoDB Server 2.6.x: mongoose ^3.8.8 or 4.x
MongoDB Server 3.0.x: mongoose ^3.8.22, 4.x, or 5.x
MongoDB Server 3.2.x: mongoose ^4.3.0 or 5.x
MongoDB Server 3.4.x: mongoose ^4.7.3 or 5.x
MongoDB Server 3.6.x: mongoose 5.x
MongoDB Server 4.0.x: mongoose ^5.2.0 or 6.x
MongoDB Server 4.2.x: mongoose ^5.7.0 or 6.x
MongoDB Server 4.4.x: mongoose ^5.10.0 or 6.x
MongoDB Server 5.x: mongoose ^6.0.0
```

Note that Mongoose 5.x dropped support for all versions of MongoDB before 3.0.0. If you need to use MongoDB 2.6 or older, use Mongoose 4.x.

## vue.config.js 代理与配置

```js
module.exports = {

    // 支持webPack-dev-server的所有选项(https://webpack.js.org/configuration/dev-server/)
    devServer: {
        host: "0.0.0.0",
        port: 8090, // 端口号
        https: false, // https:{type:Boolean}
        open: true, //配置自动启动浏览器
        // 设置请求头
        headers: {
            "Access-Control-Allow-Origin": "*"
        },
        // proxy: 'http://localhost:4000' // 配置跨域处理,只有一个代理
        // 配置多个代理
        proxy: {
            "/api": {
                target: "http://localhost:6600", // 要访问的接口域名
                ws: false, // 是否启用websockets
                changeOrigin: true, //开启代理：在本地会创建一个虚拟服务端，然后发送请求的数据，并同时接收请求的数据，这样服务端和服务端进行数据的交互就不会有跨域问题
                pathRewrite: {
                    //"^/api": "" 
                    //这里理解成用'/api'代替target里面的地址,比如我要调用'http://40.00.100.100:3002/user/add'，直接写'/api/user/add'即可
                }
            },

        }
    }
};
```


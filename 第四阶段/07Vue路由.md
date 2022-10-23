#  Vue Router 路由

##  Vue Router 路由

### 路由的概念

在前端里，路由可以理解为用来描述页面地址 URL 和组件之间的映射关系。

### 单页面应用的概念

单页面应用，简称 SPA，Single Page Application，指的是只有一个 HTML 页面的应用程序。单页应用中的组件切换就需要靠路由来进行管理。

### 安装 Router

如果需要在一个已经创建好的 Vue 项目中添加 Vue Router，可以通过以下命令：

```js
vue add router
```

执行完成后，也会在项目中自动生成路由的基本配置代码。

##  路由基础配置

### 定义路由

路由的配置文件在 `/src/router/index.js` 中，所有项目中的路由都在以下数组中进行配置：

```js
  import Vue from 'vue'
import VueRouter from 'vue-router'  //路由类
import ExploreView from "../views/ExploreView.vue"
import HomeView from "../views/HomeView.vue"
const originalPush = VueRouter.prototype.push
VueRouter.prototype.push = function push(location) {
    return originalPush.call(this, location).catch(err => {
    })
}
Vue.use(VueRouter)  //中间件
/*路由表*/
const routes = [
    {
        path: "/",   //首页
        alias: ["/index"],    //路由别名 支持字符串,支持数组
        name: "home",
        component: HomeView
    },
    {    //路由节点
        path: "/explore",   //表示路由的路径
        name: "explore",   //路由名称 在路由表中唯一 可选
        component: ExploreView         //加载路径显示哪个组件
    },
    {
        path: "/tv",
        name: "tv",
        component: () => import("../views/TvView.vue")    //访问时加载组件? 懒加载
    },
    {
        // path: "/detail/:id?", //电影详情 带参数, ?该参数可以不带
        path: "/detail/:id/:name?", //电影详情 带参数, ?该参数可以不带
        props:true,    //路由传参可以通过 props 接收
        name: "detail",
        component: () => import("../views/DetailView.vue")
    },
    {
        path: "/admin",
        //当有二级路由的时候name最好不写
        component: () => import("../views/AdminView.vue"),
        children: [
            {   //默认二级路由
                path: "",  // ""
                name: "adminindex",
                component: () => import("../views/admin/IndexView.vue")    //访问时加载组件? 懒加载
            },
            {          //路由嵌套,子路由
                path: "manageuser",  //子路由最前不要写 /
                name: "manageuser",
                component: () => import("../views/admin/ManageUserView.vue")    //访问时加载组件? 懒加载
            }]
    },
    {
        path:"/err",
        component: () => import("../views/ErrorView.vue")
    },
    {
        path: "*",   //通用路由 写在路由表中的最后面
        //component: () => import("../views/ErrorView.vue")  //404
        redirect:"/err"//重定向
    }
]
const router = new VueRouter({  //实例化
    mode: "history",   //history 没有 #, hash 有 # 模式
    routes
})
export default router
```

- path 表示路由的路径
- name 是路由名称
- component 是路径对应的组件

当浏览器的 URL 匹配到某一个路由的 path 时，就会加载该路由对应的组件。

![image-20221013150607407](C:\Users\TOM\AppData\Roaming\Typora\typora-user-images\image-20221013150607407.png)





### 路由出口

Vue Router 中提供了 `<router-view />`标签来设置路由出口，即当 path 对应的组件加载成功后，在页面中的渲染位置。

```html
 app.vue
<router-view/>
```

### 路由跳转

Vue Router 中提供了两种路由跳转的方式：

- 标签跳转
- JS 跳转

#### 标签跳转

我们可以通过 `<router-link>` 标签来实现路由之间的跳转：

```html
 <router-link to="/">Home</router-link> |
<router-link to="/about">About</router-link> |
<router-link v-bind:to="'/movie'">Movie</router-link>
```

#### JS 跳转

也可以在事件中通过 `this.$router.push()` 或`this.$router.replace()` 方法实现路由之间的跳转：

```js
 // <span @click="toUrl('/movie')"> 事件跳转Movie </span>
toUrl(str){
  // this.$router.replace(str)
  this.$router.push(str)
}
//注意以上操作 相同地址跳转时会出现错误
router/index.js
//解决重复路由跳转错误的问题
const originalPush = VueRouter.prototype.push
VueRouter.prototype.push = function push(location) {
    return originalPush.call(this, location).catch(err => {
    })
}
```

## 路由的其他配置

### 路由重定向

可以将某一个路由直接跳转到另一个路由。

```js
  {
        path:"/err",
        component: () => import("../views/ErrorView.vue")
    },
    {
        path: "*",   //通用路由 写在路由表中的最后面
        //component: () => import("../views/ErrorView.vue")  //404
        redirect:"/err"//重定向
    }
```

上例中将路径 `'/home'` 直接跳转到了根目录 `'/'`。

### 路由懒加载

路由懒加载，指的是当路由匹配到对应的路径后，才开始加载该路径对应的组件：

```js
  {
        path: "/tv",
        name: "tv",
        component: () => import("../views/TvView.vue")    //访问时加载组件? 懒加载
    },
```

### 路由模式

Vue Router 中，路由分为两种模式：

- hash：在浏览器 URL 路径中会有一个 `#`
- history：在浏览器 URL 路径中没有 `#`

可以在路由的配置文件中更改路由模式：

```js
 const router = new VueRouter({  //实例化
    mode: "history",   //history 没有 #, hash 有 # 模式
    routes
})
```

不设置 mode 属性，则默认为 hash 模式。

### 路由别名（扩展）

在路由配置时，可以通过 `alias` 来配置路由别名，即 path 的备用地址。支持数组的方式

```js
  {
        path: "/",   //首页
        alias: ["/home", "/index"],    //路由别名 支持字符串,支持数组
        name: "home",
        component: HomeView
    },
```

配置完成后，我们访问 `/home` 和 `/index` 都可以进入到 Home 组件。

### 通用路由

可以给路由的 path 属性设置为 `*`，表示通用路由，可以匹配任意路由。通常将该路由配置放在所有路由最后，用来进行错误路径的处理：

```js
 {
        path: "*",   //通用路由 写在路由表中的最后面
        component: () => import("../views/ErrorView.vue")  //404
    }
```

## 嵌套路由

嵌套路由，也叫做子路由。

在路由配置文件中，每一个路由对象都有 children 属性用来设置嵌套路由：

```js
 {
        path: "/admin",
        component: () => import("../views/AdminView.vue"),
        children: [
            {   //默认二级路由
                path: "",  // ""
                name: "adminindex",
                component: () => import("../views/admin/IndexView.vue")    //访问时加载组件? 懒加载
            },
            {          //路由嵌套,子路由
                path: "manageuser",  //子路由最前不要写 /
                name: "manageuser",
                component: () => import("../views/admin/ManageUserView.vue")    //访问时加载组件? 懒加载
            }]
    }, 
```

注：子路由的 path 不需要以 `/` 开头。

嵌套路由配置好后，还需要在父级路由的组件中去设置子路由出口：

```html
  <router-view>二级栏目出口</router-view>
```

## 动态路由

动态路由，指的是在路由的路径中有一部分内容是动态变化，而这一部分的变化并不会影响到路由本身的跳转。

### 动态路由的配置

在路由配置中配置动态路由时：

```js
  {
        path: "/detail/:id", //电影详情 带参数, ?该参数可以不带
        name: "detail",
        component: () => import("../views/DetailView.vue")
    },
```

动态路由中动态部分，需要通过 `:变量名` 来与路径匹配。

#### 可选动态路由

如果希望动态路由的动态部分是可选的，可以在末尾添加一个问号：

```js
  {
        path: "/detail/:id?", //电影详情 带参数, ?该参数可以不带
        name: "detail",
        component: () => import("../views/DetailView.vue")
    },
```

这样就表示 `detail` 路径末尾有没有动态部分都可以匹配到该路由。

### 动态路由跳转

当需要跳转到一个动态路由时，跳转的路径中必须有一部分和动态路由中动态部分进行匹配：

```html
  <router-link :to="'/detail/'+item._id"> 带参数的跳转 </router-link>
```

### 获取动态路由的数据

在动态路由对应的组件中，可以获取到动态路由中的数据：

```js
  created() {
    console.log(this.$route.params)
}
```

还可以通过 props 获取动态路由的参数：

1. 在路由配置文件中，添加 `props: true`

```js
{
        path: "/detail/:id/:name?", //电影详情 带参数, ?该参数可以不带
        props:true,    //路由传参可以通过 props 接收
        name: "detail",
        component: () => import("../views/DetailView.vue")
    }, 
```

1. 在组件中，用 props 接收参数：

```js
  props:["id","name"],
```

## 路由扩展

### router-link 属性

#### active-class

active-class 用于设置被激活的 router-link 标签的 class。

```vue
  <li class="flex-item-1">
    <router-link to="/home/about" :active-class="active">关于我们</router-link>
</li>
<script>
    ...
    data() {
            return {
                active:"text-red"
            }
        },
</script>
<style scoped lang="scss">
    .router-link-exact-active{
        background-color: black;
        color: white;
    }
</style>
```

#### tag

router-link 标签默认渲染为 a 标签，tag 属性可以设置渲染为其他标签：

```html
  <router-link to="/home" tag="b" :active-class="active">首页推荐</router-link>
tag="h1 ....."
```

#### JS路由跳转扩展

在 push 和 replace 方法中，也可以通过对象的形式进行跳转：

```js
 this.$router.push(url)//算第二种简写
this.$router.push({path:url}) // this.$router.push({path:"/home"})
this.$router.push({name:"adminIndex"}) // 查找name为movies的节点，如果是有二级内容的话需要写二级路由下的默认的那个name


注意路由配置 router/index.js
{
path: "/movies",
name: "movies",
component: () => import('../views/home/MoviesView.vue')
},
```

### 路由传参

通常来说，路由传参可以直接通过动态路由来实现。但是除了动态路由外，还可以用以下方式：

```js
  toURL(url){
     this.$router.push(url)
     this.$router.push({path:url})
     this.$router.push({name:"movies"})
     this.$router.push("/home/detail/"+"6311c57641300a7ba0dd7018/战争")
    //this.$router.push({path:"/home/detail",query:{id:'6311c57641300a7ba0dd7018',auther:'战争'}})
}
```

query 传参不是动态路由，所以路由的配置和普通路由一致。

#### 组件接收 query 参数

```js
  created() {
         console.log(this.$route)
 }
```

##  路由元信息

### meta

在路由配置文件中，每一个路由对象，都有一个 meta 属性，用来设置路由的元信息。

```js
 {
    path: "reg",
    name:"reg",
    component:()=>import("../views/home/RegView.vue"),
    meta:{
        title:"会员注册"    
    }
},
```

### 应用场景

例如，我们在通过路由渲染组件时，有一些组件需要缓存(keep-alive)，有一些组件不需要缓存时，就可以通过 meta 来对路由状态进行标记：

```js
  {
                path: "reg",
                name:"reg",
                component:()=>import("../views/home/RegView.vue"),
                meta:{
                    isKeepAlive:true,  //该路由节点被缓存
                }
            },
```

在渲染时，就可以通过 meta 值对路由状态进行判断：

```html
<keep-alive>
    <router-view v-if="$route.meta.isKeepAlive">前台二级路由</router-view>
</keep-alive>
<router-view v-if="!$route.meta.isKeepAlive">前台二级路由</router-view> 
```

## 导航守卫

导航，表示路由正在发生改变。当路由发生改变时，会触发守卫函数，在函数中，我们可以做一些业务逻辑判断等，最后通过代码控制当前路由到底是成功跳转还是停留在当前页面或者跳转到登录current等…

### 导航守卫分类

- 全局守卫：作用于所有路由
- 路由独享守卫：只作用于当前路由
- 组件内的守卫：作用于当前组件对应的路由

### 全局守卫

全局守卫中有一种“全局前置守卫”，通常可以用来继续用户的身份认证：

```js
/*
全局守卫
to:表示用户要进入的路由节点
from:当前路由节点
next:下一跳
* */

router.beforeEach((to, from, next)=>{
  console.log(to,from)
  if (to.path.includes("admin")){
    //判断路由中是否包含admin
    const token =false
        // localStorage.getItem("token")
    if (token){//判断用户是否登录
        next()
    }else {
      alert("宁没有登录，不能访问")
      next("/home");
    }

  }else {
      next()
  }
}) 
```

### 路由独享守卫

路由独享守卫中有一种“路由前置独享守卫”：

```js
 {          //路由嵌套,子路由
        path: "ucenter",  //子路由最前不要写 /
        name: "ucenter",
        component: () => import("../views/home/UcenterView"),    //访问时加载组件? 懒加载
        /*独享守卫*/
        beforeEnter:(to,from,next)=>{
          const token = false //localStorage.getItem("token")
          if (token){//判断用户是否登录
            next()
          }else {
            alert("请先登录")
            next("/home/login")
          }
        } 
```

### 组件内的守卫

组件内的守卫有一个离开组件之前触发的守卫：

```js
/*组件内的守卫*/
beforeRouteLeave(to,from,next){  //判断当前路由离开时触发 函数
    if(confirm("你确定要离开吗?")){  //当前确定后,才进入下一跳
        next()
    }
} 
```


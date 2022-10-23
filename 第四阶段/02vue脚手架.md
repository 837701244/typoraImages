# Vue脚手架

## 创建 Vue.js 项目

### 安装脚手架工具（Vue CLI）

- 查看 CLI 的版本号

```js
vue --version 
vue -V
注意-V ：V 是大写
如果已经安装的版本是 2.x 或 2.x 以下的版本，需要卸载后重新安装最新的版本。

yarn -v  //查看yarn版本
npm install yarn -g //全局安装yarn
```

- 安装 CLI   

```js
npm install -g @vue/cli
# OR
yarn global add @vue/cli
```

- 升级. 如需升级全局的 Vue CLI 包，请运行：

```js
npm update -g @vue/cli
或者
yarn global upgrade --latest @vue/cli
```

### 创建项目

- 运行以下命令来创建一个新项目：

```js
vue create vue-demo
最后的是名字
```

2）选择项目的创建模式

```js
Vue CLI v4.5.15
? Please pick a preset: (Use arrow keys)
  Default ([Vue 2] babel, eslint)
  Default (Vue 3) ([Vue 3] babel, eslint)
> Manually select features

最后一个是自己选择安装市面插件
```

3）选择插件

```js
? Check the features needed for your project:
 ( ) Choose Vue version
>(*) Babel
 ( ) TypeScript
 ( ) Progressive Web App (PWA) Support
 ( ) Router
 ( ) Vuex
 (*) CSS Pre-processors
 ( ) Linter / Formatter//严格模式，一个空格错都会报错
 ( ) Unit Testing
 ( ) E2E Testing
 
 目前就是这两个
```

4）选择插件配置代码位置

```js
? Where do you prefer placing config for Babel, ESLint, etc.? (Use arrow keys)
> In dedicated config files
  In package.json
  
  
  第一个是把别的配置文件放到新的文件中
  第二个是都装在一个文件中
```

5）是否保存以上配置

```js
? Save this as a preset for future projects? (y/N) n

如果选择的是y的话是保存自己的配置
先写配置名字
然后就自动完成安装了

```

当有这个的时候就可以了

```js
cd 项目名
npm run serve
就可以了
```





### 启动项目

在终端中进入项目根目录：

```js
cd vue-demo

cd .. 是返回上一级
```

执行启动命令：

```js
npm run serve
//or
yarn serve
```

## 目录结构

| 目录          | 说明                   |
| ------------- | ---------------------- |
| dist          | 打包后生成目录         |
| node_modules  | 项目所依赖的工具包     |
| src           | 源码目录(项目核心目录) |
| - assets      | 静态资源目录(图片)     |
| - components  | 组件目录               |
| - App.vue     | 根组件,页面级组件      |
| - main.js     | 页面入口JS文件         |
| public        | 公共资源目录           |
| package.json  | 项目描述文件           |
| vue.config.js | (vue配置)              |

## 单文件组件 

Vue 项目中，出现了一种以  `.vue` 为后缀的文件，我们将这种文件称为“单文件组件”，每一个文件都是一个组件。

###  组件

Vue 中，我们可以将页面看作是由一个一个的组件组成的，例如头部是一个组件，底部是一个组件。组件与组件之间相互嵌套，就可以组成一个完整的 Vue 应用。

###  创建组件

每一个单文件组件，实际都是以 `.vue` 为后缀的文件。创建组件文件时，建议组件名首字母大写。

- template 标签内只允许出现一个父级标签
- script 可以没有, 表示是设置标签对象的实例
- style 可以没有,表示css效果,scoped:表示样式只有当前实例中有效.lang="scss" 表示支持sass的写法.

如果不加scoped就代表是全局的样式了，当冲突时，优先执行scoped里面的样式

```vue
 
```



在组件文件中的script中的export default是实例也是之后暴露的东西，也就是说每一个模板中都有一个对应的实例。name 无所谓，components就是注册组件，其余的data之类的就可以在这之间写

我们再写组件的时候就可以在最大的组件中写小组件，跟套娃类似

如果需要在大组件中引入小组件需要，impot 直接引入就行





### 组件嵌套

- 引入组件
- 注册组件
- 调用组件

```js
1.在大的里面的script 里

import  HeaderCom from "./components/HeaderCom";

2.在实例下的 components: {
    HeaderCom
  }
放入import的名字

3.调用
当做标签直接插入到想要的标签中
<HeaderCom></HeaderCom>
```

## 计算属性 Computed

每一个 Vue 组件都有一个 `computed` 属性，用来设置组件的计算属性。在模板中使用计算属性时，直接通过属性名进行渲染：

```js
  <li>   页面对外访问人数: {{otherI}}</li>
data() {  //初始数据
    return {
        i:1
    }
},
computed: {  //属于DATA的衍生产品
    otherI(){
        return this.i+2000
    },
}, //计算属性
```

###  特点

1.   计算属性通常都会依赖一个或多个源数据，在这些源数据的基础之上，通过计算得到一个新数据；
2.   计算属性在对源数据进行计算时，不会改变源数据；
3.   计算属性在首次使用时会执行一次，后续只有在源数据发生变化时才会执行；
4.   计算属性具有缓存的功能，只要源数据没有发生改变，多次使用同一个计算属性，也只会执行一次；

### 计算属性的 set (扩展)

默认情况下，计算属性是没有 set 方法，因此也不能修改。如果想要去修改计算属性，就需要手动添加 set 方法：

我们修改计算属性时，会触发对应的 set 方法，该方法可以通过一个形参获取到想要修改的新的值。然后在通过 set 方法对计算属性依赖的源数据进行修改。

```js
  <input type="text" v-model="firstName">
fullName:{  //计算属性的扩展 set get
    get(){  //获取值执行的函数
        return this.firstName+" "+this.lastName
    },
    set(newValue){  //改变值执行的函数
        const [a,b]=newValue.split(" ")
        this.firstName=a
        this.lastName=b
    }
}
```

## 监听器(侦听器)

- 每一个组件都有一个 watch 属性,用来设置组件的侦听器

```js
  data() {  //初始数据
            return {
                name:"",
                age:1,
            }
        }, 
watch: { //监听数据
    name(newValue,oldValue){
        console.log(newValue,oldValue)
        if(newValue.length>=4&&newValue.length<=6){
            this.msg[0]="<b class='text-green'>输入正确</b>"
        }else {
            this.msg[0]="<b class='text-red'>请输入4到6位数</b>"
        }
    },
    age(newValue,oldValue){
        console.log(newValue,oldValue)
        if(newValue>0&&newValue<=120){
            this.msg[1]="<b class='text-green'>输入正确</b>"
        }else {
            // this.age=oldValue
            // alert("请输入1到120")
            this.msg[1]="<b class='text-red'>请输入1到120</b>"
        }
    },
},  //监听
```

### 侦听引用类型数据

默认情况下，watch 无法侦听到引用类型数据内部的变化。只有当引用类型的地址发生改变，watch 对应的侦听函数才会执行。

#### 监听对象中某个属性

```js
 需要在里面写 watch
 "user.name"(n,o){   //监听对象数据中具体的值
    console.log(n,o)
},
```

#### 深度监听

-  deep:true

```js
user:{
    deep:true,  //开启深度监听
    handler(n,o){
        console.log("监听user")
        // console.log(n==o,n.name,n.pwd)
        if(n.name.length>=4&&n.name.length<=6 && n.pwd.length>=6 &&n.pwd.length<=12){
            this.onOff=false
        }else {
            this.onOff=true
        }
    }
}   
```

### 立即侦听

默认情况下，侦听器在页面首次刷新时不会执行，只会在数据发生变化时才执行。如果希望侦听器能够在页面首次刷新时执行，可以设置“立即侦听”。

- immediate: true  // 立即侦听

```js
在watch中
user:{
    deep:true,
     immediate: true,
         handler(n,o){
         
     }
}

 user:{
    deep:true,  //开启深度监听
    immediate:true, //开启立即监听
    handler(n,o){
        console.log("监听user")
        // console.log(n==o,n.name,n.pwd)
        if(n.name.length>=4&&n.name.length<=6 && n.pwd.length>=6 &&n.pwd.length<=12){
            this.onOff=false
        }else {
            this.onOff=true
        }
    }
}
```

## 数据变化检测(深度监听的使用范围)

在 Vue 中，当我们把数据设置在 data 属性中后，Vue 会将 data 中的数据加入到“响应式系统”中。后续的使用中，Vue 内部会实时的检测 data 中数据的变化，一旦检测到 data 的数据发生变化，Vue 内部会主动的去更新页面。

但是，有几种特殊情况在操作数据时，是 Vue 内部无法检测到的。也就意味着，当数据发生改变后，页面不会主动更新。

- 对象  深度监听
- 数组中的节点中有对象时不能被监听 ,(修改,删除)内存中栈的地址发生变化才能监听.增加可以直接监听.

```js
 
```

## 集成 bootstrap

- 安装bs依赖

  ```js
  yarn add bootstrap @popperjs/core
  //or 
  npm install bootstrap @popperjs/core
  ```

- 项目中使用CSS,与JS

```js
import "bootstrap/dist/css/bootstrap.min.css"  //main.js
//\node_modules\bootstrap\js\dist  按需导入
import Alert from 'bootstrap/js/dist/alert';    
import Carousel from 'bootstrap/js/dist/carousel.js';

//main.js 引入
import "bootstrap/dist/css/bootstrap.min.css" //所有样式
import "@popperjs/core"//所以bs的自建库
import "bootstrap/dist/js/bootstrap.min.js"  //所有全局脚本
```


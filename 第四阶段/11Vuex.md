## Vuex 核心属性

Vuex，状态管理模式。状态，指的就是 Vue 应用中的数据。

简单来看，Vuex 就是一个数据仓库，项目中所有的公共数据都可以交给 Vuex 来进行管理，包括数据的**访问、修改、删除**等。

### 项目中安装 Vuex

如果需要在一个已经创建完成的 Vue 项目中，安装 Vuex，可以通过以下命令：

```
vue add vuex
```

### Vuex 五大核心概念

- state
- getters
- mutations
- actions
- modules

#### state

状态，保存初始数据。可以看作是组件中的 data。

```js
state: {
    
    pv:1,//网站访问人数
    categoryList: ["默认", "喜剧", "爱情", "动作", "科幻", "动画", "悬疑", "犯罪", "惊悚", "冒险", "音乐", "历史", "奇幻", "恐怖", "战争", "传记", "歌舞", "武侠", "情色", "灾难", "西部", "纪录片", "短片"],
    area:["中国", "美国", "香港", "台湾", "日本", "韩国", "英国", "法国", "德国", "意大利", "西班牙", "印度", "泰国", "俄罗斯", "伊朗", "加拿大", "澳大利亚", "爱尔兰", "瑞典", "巴西", "麦丹"],
    
},
```

#### getters

用来管理从 state 派生出来的数据。可以看作是组件中的 computed。

```js
getters: {
     showPv(state){
      return state.pv*1+200
},
```

getters 中的每一个方法的第一参数，默认都是 state。

#### mutations

mutations，用来管理所有修改 state 的方法，也是**唯一修改 state 途径**。

```js
mutations: {
    addPv(state){
      state.pv++
    }
},
```

mutations 中所有方法的第一个参数，默认都是 state，第二参数，是调用该方法时传递的数据。

#### actions

actions，用来管理所有的异步方法。

```js
actions: {
     getAjax(context){
      context.commit('addPv')
    }
     
},
```

actions 中的所有方法的第一个参数，默认都是 context，指向当前仓库对象。

如果希望从 actions 中去修改 state，只能通过 `commit()` 去触发 mutations 中的方法，然后通过 mutations 去修改 state：

```js
actions: {
     
},
```

注意：

1. actions 可以触发 mutations 的方法，但是 mutations 中不能触发 actions 中的方法；
2. actions 可以触发 actions 中的其他方法：`context.dispatch('getStudents')`；

#### modules

modules 用于将仓库对象拆分成多个模块。

##  组件中操作 Vuex

### 只能传一个参数

### 组件中获取 state

组件中可以通过 `this.$store.state` 获取到 Vuex 中的 state 对象。

通常我们会通过 computed 来获取 Vuex 中的 state：

```js
computed: {
    pv(){
      return this.$store.state.pv
    },
    showPv(){
      return this.$store.getters.showPv
    }
    
},
```

### 组件中获取 getters

组件中获取 getters 的方式和 state 一致：

```js
computed: {
    pv(){
      return this.$store.state.pv
    },
    showPv(){
      return this.$store.getters.showPv
    }
     
},
```

### 组件中调用 mutations

组件中通过 `commit` 方法触发 Vuex 的 mutations 中的方法：

```js
methods: {
    ,mounted() {
    //vuex的方法
    this.$store.commit('addPv')
  }
     
},
```

### 组件中调用 actions

组件中通过 `dispatch` 方法触发 Vuex 的 actions 中的方法(只能传一个参数)：

```js
methods: {
     
},
```

`dispatch` 方法的参数，就是 actions 中的方法名。

## 34, 辅助函数

Vuex 中提供了四个辅助函数：

- mapState()
- mapGetters()
- mapMutations()
- mapActions()

### 引入辅助函数

使用哪个就引入哪个

```js
import { mapState, mapGetters, mapMutations, mapActions } from 'vuex';
```

### 辅助函数的使用

#### mapState 和 mapGetters

mapState 和 mapGetters 都是在获取 Vuex 中的数据，因此，这两个函数在组件的 computed 中调用：

```js
computed: {
    ...mapState(["..."]),
    ...mapGetters(["..."])
},
```

数组中传递的参数，就是我们想要从 Vuex 中获取的数据的属性名。获取成功后，这些数据就都作为组件的计算属性进行使用。

#### mapMutations 和 mapActions

mapMutations 和 mapActions 都是在获取 Vuex 中的方法，因此，这两个函数在组件的 methods 中调用：



1. ```js
   methods: {
       ...mapMutations(["..."]),
       ...mapActions("...")
   },
   ```

数组中传递的参数，就是我们想要从 Vuex 中获取的方法的方法名。获取成功后，这些方法就都作为组件自己的 methods 进行调用。



使用的时候最好再用另一个函数调用他

```js
methods: {
    ...mapMutations(["..."]),
    ...mapActions("..."),
      likeFn(){
   			 this.xx()
		}
},
    还可以重新命名
     ...mapMutations([newApp:"addPv"]),


```



### 辅助函数的扩展语法

所有的辅助函数中，除了可以传递一个数组作为参数外，也可以传递一个对象作为参数：(可以有效解决变量名冲突问题)

```js
computed: {
 
},
// 注意数据绑定时使用的变量为  nav,person
```

上面代码中，对象中的键可以任意命名，用来表示当前组件中计算属性的属性名。对象中的值是真正要从 Vuex 中获取的数据的属性名，不可任意更改，必须和仓库一致。

## modules 

用于将仓库对象分成多个对象引用。

### 仓库分类

我们再项目开发之前一般就会将仓库进行分类. 在store文件夹下面创建modules文件夹里面存放你们的数据模块(子仓库)

```js
//子模块  store/modules/adminModule.js
export default {
    namespace:true,//开启命名空间
    state:{
        title:"电影后台管理"
    },
    getters:{

    },
    mutations:{

    },
    actions:{

    }
}

在index.js中

import adminModule from "./modules/adminModule.js";

//加载子状态机
  modules: {
    adminModule
  }
 
```

**注意:**

- 开启命名空间，默认会将文件名字作为仓库名字

- `namespaced:true`必须加上,代表开启命名空间,默认会将文件导入模块作为命名空间名字

### 组件调用子仓库数据

要获取子仓库的数据,需要createNamespacedHelpers函数来指定你的仓库名字.这样才能获取指定仓库的数据

命名空间作用就是隔离了你们的数据

```js
//加载命名空间助手
import {createNamespacedHelpers} from "vuex"
const { mapState, mapGetters, mapMutations, mapActions }  = createNamespacedHelpers('adminModule')

```

一个页面引入多个模块化.你可能会遇到一个页面需要引入多个模块,不同的命名空间.我们需要mapState函数设置别名

```js
子组件const { mapState:adminState, mapGetters, mapMutations, mapActions }  = createNamespacedHelpers("adminModule");

或者直接
import obj form "vuex"
然后我们可以直接obj.mapState使用



```












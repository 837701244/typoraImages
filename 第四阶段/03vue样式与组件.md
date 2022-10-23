# 	vue样式与组件

## 样式处理

### 动态样式 

```vue
<dl class="card">
    <dt class="card-header">StyCom</dt>
    <dd class="card-body">
          <div :class="myclass"></div>
          <div :style="sty"></div>
    </dd>
  </dl>


<script>
export default {
  name: "StyCom",
  data() {
    return {
      // myclass:"bg-black"   字符串
      // myclass:["bg-black","text-red"]  数组 
      myclass:{"bg-red":true,'text-white':false}, //对象
       // sty不能使用数组
      // sty:"background-color:blue;color:white"
      sty:{backgroundColor:"green",color:"red"}
    }
  },
  computed: {},
  watch: {},
  methods: {},
  components: {},
  created() {

  }
}
</script>
```

### 静态样式

#### 内部样式

```vue
<style scoped lang="scss">

</style>
```

- 任何引入组件的样式在
  - 没有 scoped 限制时,都会作用于全局
  - 有 scoped 作用于当前组件
  - lang="scss"  没有该属性时,只支持CSS写法

#### 外部样式 

 **@代表的是根目录，src**

```js
//在main.js中全局引入
import "bootstrap/dist/css/bootstrap.min.css" //所有样式
import "@popperjs/core"//所以bs的自建库
import "bootstrap/dist/js/bootstrap.min.js"  //所有全局脚本



//其他方式引入

//局部引用
在assets中创建一个css文件，里创建一个scss文件

在想使用的组件中
<style scoped lang="scss">
		@import "@/assets/css/sty.scss"
</style>


//简写
<style scoped lang="scss" src="@/assets/css/sty.scss">
	
</style>

```

在scss中可以用@import，也就是可以在一个style加载另一个样式CSS文件



我们也可以直接在<script>中直接impirt引用，但是没有scoped的话这个样式就变成全局的样式了

## 组件的数据传递(通信)

### 父组件 传递数据

- 通过标签自定义属性的方法来传递数据



```js
<template>
  <dl class="card">
    <dt class="card-header">FaCom</dt>
    <dd class="card-body">
          <SonCom v-bind:i="i" auther="xxxxx" :friend="user"></SonCom>
    </dd>
  </dl>
</template>



<script>
import SonCom from "@/components/SonCom.vue"
export default {
  name: "FaCom",
  data() {
    return {
      i:1，
      user:{
        name:111,
        age:111
    }
       
    }
  },
  computed: {},
  watch: {},
  methods: {},
  components: {
    SonCom
  },
  created() {

  }
}
</script>
```

在通过自定义属性给 `props` 传递数据时，我们需要考虑数据的不同类型。例如：字符串、数字、布尔值、数组、对象等。或者是 data 中的动态数据，都需要通过 `v-bind` 将这些属性变成动态属性。

### Props 接收数据

每一个组件都有一个 `props` 属性用来接收外部传递的数据，数组中的值就是组件需要接收的数据名称。



**<font color='red'>接收的参数挂载到实例的根节点下</font>**

接收的数据不能修改，子级修改就会报错

**$attr 就是接收没有在proprs里写的数据**

```js
<script>
export default {
  name: "SonCom",
   props:["i","auther",friend],
  data() {
    return {
     
    }
  },
  computed: {},
  watch: {},
  methods: {},
  components: {},
  created() {

  }
}
</script>
```

### 访问 Props 传递来的数据

组件中通过 `props` 接收到的数据，可以直接在 `<template>` 中进行渲染，也可以在 `<script>` 通过 `this` 进行访问：

```vue
<script>
export default {
  name: "SonCom",
   props:["i","auther",friend],
  data() {
    return {
     
    }
  },
  computed: {},
  watch: {},
  methods: {},
  components: {},
  created() {

  }
}
</script>
```

- **注意：props:**
  - 专门用于接受别的组件发送过来的数据
  - 使用props接受过来的数据，使用的过程与 使用自己属性的方式完全一样
  - Vue 中规定，通过`props`获取到的值，可以访问，但是不能修改。

### Props 的验证

Props 的验证是指子组件可以对外部传递进来的数据的类型或内容设置验证规则。例如在子组件组中设置想要接收dataI数据的值是`Number`类型，如果接收到的不是`Number`类型，浏览器中就会抛出报错。

如果要设置验证，`props`属性的值需要切换为对象：



**<font color='red'>如果类型不一样的数据接收过来会报错但不会阻止事件的发展</font>**



**<font color='red'>如果 required:true的时候的这个数据没传也会报错</font>**



如果传过来的是数组，不能给默认值,需要给函数才能给默认值



如果传过来的是对象，不能给默认值,需要给函数才能给默认值

```js
<script>
export default {
  name: "SonCom",
      
   props:["i","auther","friend"],//就是普通接收参数
       
   props：{就是带有验证的参数，接收
   
		i:Number,  //数据类型验证
            
        i:[Number,String],//可以是数字类型也可以是字符串类型
          
          
        a:{//a没传，但是要接收
            type：String, //类型
            required:true，//必传数据
            default："a"//如果没传可以给个默认值
        },	
        arr:{  //默认值是数组时使用，函数方式返回
            type:Array, //类型
            default:()=>[1,2,3,4],
        },
        obj:{  //默认值是对象时使用，函数方式返回
            type:Object, //类型
                default:()=>（{name:"xingyu"}）//箭头函数返回对象数据时，需要加个小括号
        },
        
        money:{
            type:Numver,
            validator:(valu)=>{//自定义验证,返回为真时通过，只会报错，还会往下走
                if(value<0){
                    alert("参数不能为负数")
                    return false
                }else{
                    return true
                }
            } 
            
        }
   }
  data() {
    return {
     
    }
  },
  computed: {},
  watch: {},
  methods: {},
  components: {},
  created() {

  }
}
</script>
```

数据类型不匹配时出现的错误

### Props验证扩展

除了定义简单的数据类型验证外，props 还支持其他的一些验证规则：

#### 设置多个数据类型

例如 `dataI` 属性接收数字和字符串都可以(如上)

#### 必填属性 required:true

```js
<script>
export default {
  name: "SonCom",
   props:["i","auther","friend"],
   props：{就是带有验证的参数，接收
		i:Number,  //数据类型验证
        i:[Number,String]//可以是数字类型也可以是字符串类型
        a:{//a没传，但是要接收
            type：String, //类型
            required:true，//必传数据
        }
   }
  data() {
    return {
     
    }
  },
  computed: {},
  watch: {},
  methods: {},
  components: {},
  created() {

  }
}
</script>
```

- 以上会抛出错误,因为 dataAddr 属性是必填属性

#### 默认值 default:符合验证的任何数类型

```js
<script>
export default {
  name: "SonCom",
   props:["i","auther","friend"],
   props：{就是带有验证的参数，接收
		i:Number,  //数据类型验证
        i:[Number,String]//可以是数字类型也可以是字符串类型
        a:{//a没传，但是要接收
            type：String, //类型
            required:true，//必传数据
            default："a"//如果没传可以给个默认值
        }
   }
  data() {
    return {
     
    }
  },
  computed: {},
  watch: {},
  methods: {},
  components: {},
  created() {

  }
}
</script>
```

- 没有属性 dataAddr 时,输出是 "china"  ,有 dataAddr 时,是dataAddr的值该值.

#### 对象和数组类型的默认值

- 必须通过函数的返回值来设置：

```js
   arr:{  //默认值是数组时使用，函数方式返回
            type:Array, //类型
            default:()=>[1,2,3,4],
        },
        obj:{  //默认值是对象时使用，函数方式返回
            type:Object, //类型
                default:()=>（{name:"xingyu"}）//箭头函数返回对象数据时，需要加个小括号
        },
```

#### 自定义验证规则 validator 验证器

```js
  
        money:{
            type:Numver,
            validator:(valu)=>{//自定义验证,返回为真时通过
                if(value>0){
                    return ture
                }else{
                    return false
                }
            } 
```

- 以上代码不符合验证器规则的判断,会抛出检测失败的错误
  - Invalid prop: custom validator check failed for prop "dataAge".

### 自定义事件的传递

- 父组件给子组件传递了数据,子组件不能修改数据.
- **子组件想修改父组件传递来的数据,可能通过父组件传递事件,子组件调用该事件来实现 **

####  给子组件绑定事件 

触发事件向父组件传递数据(点击子组件的按钮完成向父组件传值的过程)

```vue
父组件
<template>
  <dl class="card">
    <dt class="card-header">FaCom</dt>
    <dd class="card-body">
          <SonCom 
                  v-bind:i="i" 
                  auther="xxxxx" 
                  :friend="user"
                  @addFn：addFn
                  >
    
    	</SonCom>
    </dd>
  </dl>
</template>

<script>
    export default{
        name: "FaCom",
         methods: {
             addFn(n){
                 this.i+=n
             }
         },
         components: {
            SonCom
          },
    }
</script>




```

#### 触发子组件中的点击事件 

通过触发点击事件向父组件传递数据

- this.$emit("父组件事件名",实参数)





$emit也同样在根节点下

```js
子组件

<button @click=$emit('addFn',x)> </button>


<script>
    export default{
        name: "FaCom",
   		data(){
            return{
               x :2,
            }
        }
       
    }
</script>



也可以在方法中调用
<button @click=FaAdd> </button>


<script>
    export default{
        name: "FaCom",
   		data(){
            return{
               x :2,
            }
        }，
        methods:{
            FaAdd(){
                this.$emit('addFn',this.x)
            }
        }
       
    }
</script>




```

####  父组件通过自定义事件接收数据

```vue

```



## 练习

```js


在Vue.vue 中
<template>
  <div id="app">
    <FaCom></FaCom>
  </div>
</template>

<script>

import FaCom from "@/components/FaCom";

export default {
  name: 'App',
  data(){
    return{

    }
  },
  computed: {
  },
  watch: {


  },
  methods: {


  },
  components: {
      FaCom

  },
  created() {
  }
}
</script>

<style lang="scss">

</style>


在Fa中
<template>
  <dl class="card">
    <dt class="card-header">FaCom</dt>
    <dd class="card-body">
      <div class="container text-center">
        <h1>查看电影</h1>
      </div>
      <div class="container">
        <div >
          <SonCom1 @changeWord="searchMov"></SonCom1>
        </div>
        <SonCom2 :arr="searchArr"></SonCom2>
      </div>



    </dd>
  </dl>
</template>

<script>
import  Arr from "../assets/movie.json"
import SonCom1 from "@/components/SonCom1.vue";
import SonCom2 from "@/components/SonCom2.vue";

Arr = Arr.map((item,index)=>item.id = index)

export default {
  name: "FaCom",
  data() {
    return {
      Arr :[...Arr],
      searchArr:[],
      word:"",
    }
  },
  computed: {},
  watch: {},
  methods: {
    searchMov(name){
      this.word = name
      if (name){
        this.searchArr = this.Arr.filter(item=>item.title.includes(this.word))
      }else {
        this.searchArr = []
      }

    },
  },
  components: {
    SonCom1,
    SonCom2
  },
  created() {

  }
}
</script>

<style scoped lang="scss">

</style>


在Son1中
<template>
  <div class="row">
    <div class="col-md-8">
      <input  type="text" id="inputPassword5" class="form-control" aria-describedby="passwordHelpBlock" v-model.trim="data">
    </div>
    <div class="col-md-2 ">
      <button @click="searchFn" class="btn btn-primary">查询</button>

    </div>
    <div class="col-md-2 ">
      <button class="btn btn-info col align-self-end "  style="color: white" > 增加电影</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "SonCom1",
  data() {
    return {
      data:''
    }
  },
  computed: {},
  watch: {},
  methods: {
    searchFn(){
      this.$emit('changeWord',this.data)
    }
  },
  components: {},
  created() {

  }
}
</script>

<style scoped lang="scss">

</style>



在Son2中

<template>
  <div class="table-responsive"  style="margin-top: 20px">
    <table class="table" v-if="arr">
      <thead>
      <tr>
        <td>
          <label >全选</label>
          <input type="checkbox" v-model="xuanzeAll" @change="changeXuanze">
        </td>
        <td>link</td>
        <td>image</td>
        <td>title</td>
        <td>rating</td>
        <td>judge</td>
        <td>brief</td>
        <td>actor</td>
        <td>pbtime</td>
        <td>category</td>
        <td>state</td>
        <td>操作</td>
      </tr>
      </thead>
      <tbody>
      <tr v-if="arr" v-for="item in arr" :key="item.id">
        <td>
          <input type="checkbox" v-model="chooseArr" :value="item.id">
        </td>
        <td><a :href="item.link">地址</a></td>
        <td><img  :src="'http://localhost:6600/'+item.image" width="50" height="50" class="img-thumbnail">
        </td>
        <td>{{item.title}}</td>
        <td>{{item.rating}}</td>
        <td>{{item.judge}}</td>
        <td>{{item.brief}}</td>
        <td>{{item.actor}}</td>
        <td>{{item.pbtime}}</td>
        <td>{{item.category}}</td>
        <td>{{item.state}}</td>
        <td>
          <button class="btn btn-danger" @click="editMov(item.id)">修改</button>
          <button class="btn btn-success"  @click="delOne(item.id)">删除</button>
        </td>
      </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "SonCom2",
  props:{
    arr:{
      type:Array,
      default:()=>["没有数值"]
    }
  },
  data() {
    return {
      chooseArr:null,
      xuanzeAll:null

    }
  },
  computed: {},
  watch: {},
  methods: {
    editMov(){},
    delOne(){},
    changeXuanze(){}
  },
  components: {},
  created() {

  }
}
</script>

<style scoped lang="scss">

</style>
```














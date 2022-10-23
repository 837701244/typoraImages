# vue过滤器

解释：过滤器是针对于数据进行过滤。

现在vue2.6版本中过滤器没有内置的。全是自定义。

## 使用的位置：

过滤器用于{{}}数据模板或者v-bind指令当中。不能使用于v-text,text-html，v-for



### 过滤器中是没有this的，是undeifind



## 过滤器定义的方式：

1. 全局注册
2. 局部注册

关键词：filters||filter

## 局部注册：

```js
//声明过滤器
filters:{
    //过滤器对象
    toCateString(){

    }
},
```



将数字转化为对应字符格式：

```js
  // 时间处理
    skSetDate(self,str="yyyy年MM月dd日 HH mm ss"){
      console.log(self)
      let skDate=new Date(self);
      //获取时间对象
      let year = skDate.getFullYear()   //获取年
          , moth = skDate.getMonth() + 1   //获取月
          , _day = skDate.getDate()      //获取日
          , hours = skDate.getHours()    //小时
          , minutes = skDate.getMinutes() //分钟
          , seconds = skDate.getSeconds(); //秒
      hours = hours < 10 ? "0" + hours : hours;             //判断小时如果小于10则与0字符拼接
      minutes = minutes < 10 ? "0" + minutes : minutes;
      seconds = seconds < 10 ? "0" + seconds : seconds;
      str = str.replace("yyyy", year);
      str = str.replace("MM", moth);
      str = str.replace("dd", _day);
      str = str.replace("HH", hours);
      str = str.replace("mm", minutes);
      str = str.replace("ss", seconds);
      return str; //返回
    },
```

过滤器如何使用：

符号：| 管道符

```vue
                 <span>上映时间:<span>{{movie.pbtime|skSetDate('yyyy年MM月dd日')}}</span></span><br>

```

过滤器的参数

第一个参数：为管道符前面的数据变量

```js
filters:{
    //过滤器对象
    toCateString(self){}
}
```

在v-for中不能使用过滤器，可以使用computed计算属性来模拟过滤器

 ![](https://woniumd.oss-cn-hangzhou.aliyuncs.com/web/gengyahui/20220721114547.jpg)

过滤器中不存在this指向 undefined

过滤器传参使用（如果存在多个参数继续向后补）

```js

```

日期转化过滤器自己可以写代码实现

```js
 
```

局部注册的过滤器只能在当前组件内部使用。

## 全局注册过滤器

在 main.js中 设置过滤器,可以设置多个.

```js
Vue.filter("过滤器名字",function (前面的值,参数) {
    return 返回值
})
```

写法：

```js
 在plugins中创建一个filter.js文件


import Vue from "vue";


Vue.filter("skSetDate",function (self,str="yyyy年MM月dd日 HH mm ss") {
    console.log(self)
    let skDate=new Date(self);
    //获取时间对象
    let year = skDate.getFullYear()   //获取年
        , moth = skDate.getMonth() + 1   //获取月
        , _day = skDate.getDate()      //获取日
        , hours = skDate.getHours()    //小时
        , minutes = skDate.getMinutes() //分钟
        , seconds = skDate.getSeconds(); //秒
    hours = hours < 10 ? "0" + hours : hours;             //判断小时如果小于10则与0字符拼接
    minutes = minutes < 10 ? "0" + minutes : minutes;
    seconds = seconds < 10 ? "0" + seconds : seconds;
    str = str.replace("yyyy", year);
    str = str.replace("MM", moth);
    str = str.replace("dd", _day);
    str = str.replace("HH", hours);
    str = str.replace("mm", minutes);
    str = str.replace("ss", seconds);
    return str; //返回
})
Vue.filter("skSetState",function (self) {
    return self == 1 ? "上架":"下架"
})


在mian.js中引入
import './plugins/filter';//加载过滤器插件
```

组件中全局注册的过滤器 整个项目组件都可以使用，使用方式和局部注册过滤器一致。




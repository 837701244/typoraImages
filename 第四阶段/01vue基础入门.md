



## 第四阶段

- vue 2.x (主流核心)
- 微信小程序 uniapp(移动端)

## 框架与库

库: jquery 提供一些方法的集合.

框架: express 针对于项目提供一整套完整的解决方案.



## 前端的主流框架

- angular1,angular3…. 2009 年诞生，现在由谷歌的开发团队在进行维护；
- React：2013 年诞生，现在由 facebook 的开发团队在进行维护；
- Vue：2014 年诞生，现在由尤雨溪的团队在进行维护；

vue create 项目名

### 基本实例

- 挂载方式   (vue 不允许挂载到 body html 标签)
  - new Vue({el:"css选择器"})
  - new Vue().$mount("#content")

```js
const vm=new Vue({
    //el:"#app"  //第一种元素选择器 (Vue的作用范围)
})
//挂载方法二
vm.$mount("#app")
```

- 数据的定义与引用方式
  - new Vue({…})
  - el:"css选择器"
  - data: 变量的定义, 变量会挂载到实例的根节点下;
  - methods 函数的定义, 函数也会挂载到实例的根节点下;
  - created: 实例挂载完毕后执行(自动执行一次)

```js
const vm=new Vue({
        //el:"#app"  //第一种元素选择器 (Vue的作用范围)
        data(){   //初始化数据
            return {
                i:1,
                str:"数据展示",
                onOff:true,
                arr:[1,2,3],
                obj:{name:"shuke",_id:"xxxxxx001"}
            }
        },
        methods:{  //所有方法
            addI(){  //累加 ，3
                console.log(this)
                this.i++
            }
        },
     created(){  //实例加载完成后执行, DOM没有加载完成
            console.log("vm 加载完成",this)1
        }，
    mounted(){  //实例加载完成 -> DOM 渲染完成，一般用于获取数据
            console.log("2,mounted")
           
        }
    })
    //挂载方法二
    vm.$mount("#app")
```











### M V VM模式(双向绑定)

vue.js是一个MVVM的框架，理解MVVM有利于学习vue.js ()
MVVM拆分解释为：
Model:负责数据存储  <===>data中的数据 	(来自于后端接口)

View:负责页面展示   <===>挂载区域对应的html标签 

View Model:负责业务逻辑处理（比如Ajax请求等），对数据进行加工后交给视图展示

MVVM要解决的问题是将业务逻辑代码与视图代码进行完全分离，使各自的职责更加清晰，后期代码维护更加简单
用图解的形式分析Ajax请求回来数据后直接操作Dom来达到视图的更新的缺点，以及使用MVVM模式是如何来解决这个缺点的
Vue中的 MVVM

![image-20220206150737046](https://woniumd.oss-cn-hangzhou.aliyuncs.com/web/gengyahui/202207102025034.png)

## 计算属性

![image-20221012081613979](C:\Users\TOM\AppData\Roaming\Typora\typora-user-images\image-20221012081613979.png)

![image-20221012081710659](C:\Users\TOM\AppData\Roaming\Typora\typora-user-images\image-20221012081710659.png)

![image-20221012081747506](C:\Users\TOM\AppData\Roaming\Typora\typora-user-images\image-20221012081747506.png)



### 简写

当只需要读取，不需要修改

![image-20221012081929820](C:\Users\TOM\AppData\Roaming\Typora\typora-user-images\image-20221012081929820.png)

不是函数，不能直接调用，他是执行完成后，往vm里放一个值叫fullName



## 监视属性

当页面的内容没修改时，Vue就会懒加载，

![image-20221012084150648](C:\Users\TOM\AppData\Roaming\Typora\typora-user-images\image-20221012084150648.png)



### 深度监视

![image-20221012084953017](C:\Users\TOM\AppData\Roaming\Typora\typora-user-images\image-20221012084953017.png)

![image-20221012084508538](C:\Users\TOM\AppData\Roaming\Typora\typora-user-images\image-20221012084508538.png)



![image-20221012084857358](C:\Users\TOM\AppData\Roaming\Typora\typora-user-images\image-20221012084857358.png)



## vue 常见指令

| 指令                  | 解释                                                         |
| --------------------- | ------------------------------------------------------------ |
| v-html                | (绑定元素的innerHTML)     可以使用{{js环境}}代替             |
| v-text                | 等价于 使用{{js环境}}代替                                    |
| v-bind                | 属性名字   （绑定属性 src,style等等。）   :属性名字 代替     |
| v-on                  | 绑定事件     使用@事件类型代替(click,change,mouseover,mouseleave,blur,focus) |
| v-if v-else-if v-else | 判断元素是否需要渲染 (显示或者隐藏的操作  true 显示  false  隐藏) |
| v-show                | 根据表达式之真假值，切换元素的 display CSS 属性。            |
| v-for                 | 用于循环生产元素                                             |
| :key                  | key用于帮助在重新渲染时元素对比，通常和v-for配合使用，提高渲染效率 |
| v-model               | 用于双向绑定，实际上(操作表单)                               |
| v-model.lazy          | 当表单输入框失去焦点是 ，才会将 data中对应的json对象的属性 更新 |
| v-model.input         | 默认值 当表单数据发生改变的时候，data中对应json对象中的属性马上更新 |
| v-model.number        | 默认获取表单数据都是字符串类型，使用.number自动转成数值类型  |
| v-model.trim          | 默认去掉输入框中的左右空格                                   |

### v-html v-text

- v-html:专门用于绑定标签的文本节点(指的是标签所包裹的内容)  

```html
{{title}}
<div v-html="title"></div>
<div v-text="title+'.'"></div>
```

### v-bind

- v-bind 绑定的是标签的属性(已知属性,自定义属性),
  - id title art src href… class checked,seleted,disabled
  - 可使用`:`来替代v-bind  (简写)
  - :style="object变量"  object对象是style对象
  - :class="String|Object|Array"  变量指向可以是字符串,对象,数组

```js
 <dt>v-bind 属性</dt>
    <dd>
        <img v-bind:src="img" alt="">
        <button v-bind:disabled="onOff">不可用按钮</button>
        <button v-bind:disabled="!onOff">可用按钮</button>
        <div v-bind:style="sty">1</div>
        <div :style="sty">2</div>
    </dd>
//eg2
 <dt>v-bind:class 支持 字符串|数组|对象</dt>
<ul>
    <li class="bg-red">content1</li>
    <li :class="bg">content2</li>
    <li :class="[bg,'text-white']">content3</li>
    <li
            :class="{'text-red':true,'bg-green':styState}" 
            @click="styState=!styState"
    >content4</li>
    <li>content5</li>
    <li>content6</li>
    <li>content7</li>
    <li>content8</li>
    <li>content9</li>
    <li>content10</li>
</ul>
```

### v-on

- v-on 事件类型(click,dblclick,change….)
  - 可使用`@`来替代v-on (简写)
  - 事件指向的函数,可以使用小括号,也可以省略.
  - v-on this指向实例,并非对应标签对象 

```html
 <dt>v-on 事件</dt>
<dd>
    <button v-on:click="changeSty">改变样式1</button>
    <button @click="changeSty">改变样式2</button>
</dd>
```



如果是想要取消默认事件还可以

```js
<form v-on:submit.prevent="xxxx">..</form>

简写可以试一下，没尝试过
<form @submit.prevent="xxxx">..</form>
```



在事件的形参中还可以写$event，是vue里默认的占位符，这样也可以在函数中使用event，但是需要按照顺序在实参中写

```js
<button @click="xxxFn($event,id)"></button>

new Vue({
    data:{
        
    },
    methods:{
        xxxFn(event,id){
            event.target.innerText....
        }
    }
})
```



#### 鼠标事件的默认修饰符

修饰符还可以连用



![image-20221011084138442](C:\Users\TOM\AppData\Roaming\Typora\typora-user-images\image-20221011084138442.png)









### 键盘事件的默认修饰符

一般都是keyup，keydown

![image-20221011090356502](C:\Users\TOM\AppData\Roaming\Typora\typora-user-images\image-20221011090356502.png)

![image-20221011090857840](C:\Users\TOM\AppData\Roaming\Typora\typora-user-images\image-20221011090857840.png)

e.key就是按键的名字，e.keyCode就是asuII码的名字

@keuup

### v-if v-else-if v-else

- 分枝结构 (满足条件时标签渲染,不满足时,标签不渲染)

```html
 <dt>
    v-if 分支判断 只有条件为真时,DOM才会加载
</dt>
<dd>
    <div v-if="active==0">为0时显示  男</div>
    <div v-else-if="active==1">为1时显示  女</div>
    <div v-else>为其它时显示 未知</div>
</dd>
```

### v-show

- 判断标签是否显示 (满足条件时标签显示,不满足时,标签不显示) 控制style属性 {display:none}
- v-show 方法,标签还是存在的,只不过不显示.

```js
 <div v-show="active==1">为0时显示  男</div>
<div class="btn" @click="tabFn">详情 <span>{{onOff?'显示':'隐藏'}}</span></div>
<div v-show="onOff">
    ..............................................................................................
</div>
```

### v-for

- v-for 用于遍历 
  - 可以直接遍历数字 从1开始
  - 可以遍历字符串
  - 可以遍历数组
  - 可以遍历对象
  - 提高循环的效率,及数据的处理 会给循环节点 给一个key属性,该属性一般会是数据中的唯一的值.

```html
 <dt>
    v-for 循环
</dt>
<dd>
    <ul>
        <li v-for="(item,index) in members" :key="item.card">
            <div>{{index}}</div>
            <div> {{item.nickname}}</div>
            <div v-text="item.name"> </div>
            <div v-html="item.email"> </div>
            <div>
                <img v-bind:src="item.pic" height="30">
            </div>
        </li>
    </ul>
</dd>
//eg2
<li v-for="(value,key) in obj">
            {{key}} : {{value}}
        </li>
<script>
    data() {
        return {   //初始数据
            num:5,
            str:"abcdef",
            obj:{
                name:"abc",
                age:333,
                gender:1,
                state:2
            }
        }
    },
</script>
```

### v-model

- 双向绑定(表单数据绑定)

- 默认写法是v-model:value="数据"

  双向绑定默认是表单专用

  只能运用于有value的属性

```js
 <h2>{{user}}</h2>
<input type="text" v-model="user.name"> <br>
<input type="text" v-model.input="user.name">
<div>.lazy 延迟加载: 失去光标后再去绑定数据 </div>
<input type="text" v-model.lazy="user.name">
<div>.number 字符转为数字</div>
<input type="text" v-model.number="user.age">
<div>.trim 字符串去除前后空格</div>
<input type="text" v-model.trim="user.pwd">
<script>
    new Vue({
        el: "#app",  //作用域
        data() {
            return {   //初始数据
                user:{
                    name:"qingyu",
                    age:33,
                    pwd:""
                }
            }
        },
        methods: {  //方法 函数
        },
        created() {  //实例加载完成
        }
    })
</script>
```

- v-model.lazy  当表单输入框失去焦点是 ，才会将 data中对应的json对象的属性 更新 
- v-model.input  默认值 当表单数据发生改变的时候，data中对应json对象中的属性马上更新  
- v-model.number  默认获取表单数据都是字符串类型，使用.number自动转成数值类型 
- v-model.trim  默认去掉输入框中的左右空格

## 实战练习

//使用 product.json 完成以下操作

- 表格渲染
- 根据产品名进行模糊查询



以当前学习的知识，是使用两张tbody，第一张tbody是展示所有数据，第二张tbody是过滤完后的数据，当搜索的时候就把第二张tbody显示出来，第一张完全隐藏。

```js
 <!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>电影</title>
    <link rel="stylesheet" href="../source/css/bootstrap.css">
    <link rel="stylesheet" href="../source/css/main.min.css">
    <script src="../source/js/vue.js"></script>
    <script src="../source/js/jquery.1.12.4.js"></script>
    <style>
        #uul>li{
            margin: 10px 0 10px 0 ;
        }
        #uull>li{
            margin: 10px 0 10px 0 ;
        }
    </style>
</head>
<body>
<div class="container" id="app">
    <div class="container" v-show="areaState==0">
        <input type="text" v-model.trim="keyword">
        <button @click="searchFn">查询</button>
        <button class="btn btn-info col-lg-offset-8 " @click="areaState=1"> 增加电影</button>
    </div>
    <div class="table-responsive" v-show="areaState == 0">
        <table class="table">
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
            <tbody v-show="!onOff">
                <tr v-if="Arr" v-for="item in Arr" :key="item.id">
                    <td>
                        <input type="checkbox" v-model="chooseArr" :value="item.id">
                    </td>
                    <td><a :href="item.link">地址</a></td>
                    <td><img v-if="item.image" :src="'../source/'+item.image" width="50" height="50" class="img-thumbnail">
                        <img v-else src="../source/upload/top250/10.jpg" width="50" height="50" class="img-thumbnail">
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
            <tbody v-show="onOff">
            <tr v-if="Arr" v-for="item in newArr" :key="item.id">
                <td>
                    <input type="checkbox" :value="item.id" v-model="chooseAllTwo">
                </td>
                <td><a :href="item.link">地址</a></td>
                <td><img :src="'../source/'+item.image" width="50" height="50" class="img-thumbnail"></td>
                <td>{{item.title}}</td>
                <td>{{item.rating}}</td>
                <td>{{item.judge}}</td>
                <td>{{item.brief}}</td>
                <td>{{item.actor}}</td>
                <td>{{item.pbtime}}</td>
                <td>{{item.category}}</td>
                <td>{{item.state}}</td>
                <td>
                    <button class="btn btn-danger">修改</button>
                    <button class="btn btn-success">删除</button>
                </td>
            </tr>
            </tbody>
        </table>
    </div>

    <div class="container" v-show="areaState == 1">
         <h1>增加电影</h1>
        <button @click="areaState=0">返回</button>
        <form @submit="addMovie">
            <ul id="uul" class="padding">
                <li>电影链接 <input class="form-control" type="text" v-model.trim="addMovies.link"></li>
                <li>电影图片 <input class="form-control" type="text" v-model.trim="addMovies.image"></li>
                <li>电影名称 <input  class="form-control" pattern="^.{4,6}" title="请输入4到6位"  required type="text" v-model.trim="addMovies.title"></li>
                <li>电影评分 <input class="form-control" type="text" v-model.number="addMovies.rating"></li>
                <li>评分人数 <input class="form-control" type="text" v-model.number="addMovies.judge"></li>
                <li>电影简介 <input class="form-control" type="text" v-model.trim="addMovies.brief"></li>
                <li>电影演员 <input class="form-control" type="text" v-model.trim="addMovies.actor"></li>
                <li>上映时间 <input class="form-control" type="text" v-model.number="addMovies.pbtime"></li>
                <li class="form-control" >电影类型
                    <select v-model="addMovies.category" >
                        <option :value="1">动漫</option>
                    </select>
                </li>
                <li class="form-control">电影状态
                    <label><input type="radio" v-model="addMovies.state" :value="1">上映</label>
                    <label><input type="radio" v-model="addMovies.state" :value="0">下架</label>
                </li>
            </ul>
            <button>新增</button>
        </form>

    </div>


    <div class="container" v-show="areaState == 2">
            <h1>修改</h1>
        <button @click="areaState=0">返回</button>
        <form @submit="editMovie()">
            <ul id="uull" class="padding">
                <li>电影链接 <input class="form-control" type="text" v-model.trim="editMovies.link"></li>
                <li>电影图片 <input class="form-control" type="text" v-model.trim="editMovies.image"></li>
                <li>电影名称 <input  class="form-control" pattern="^.{4,6}" title="请输入4到6位"  required type="text" v-model.trim="editMovies.title"></li>
                <li>电影评分 <input class="form-control" type="text" v-model.number="editMovies.rating"></li>
                <li>评分人数 <input class="form-control" type="text" v-model.number="editMovies.judge"></li>
                <li>电影简介 <input class="form-control" type="text" v-model.trim="editMovies.brief"></li>
                <li>电影演员 <input class="form-control" type="text" v-model.trim="editMovies.actor"></li>
                <li>上映时间 <input class="form-control" type="text" v-model.number="editMovies.pbtime"></li>
                <li class="form-control" >电影类型
                    <select v-model="editMovies.category" >
                        <option :value="1">动漫</option>
                    </select>
                </li>
                <li class="form-control">电影状态
                    <label><input type="radio" v-model="editMovies.state" :value="1">上映</label>
                    <label><input type="radio" v-model="editMovies.state" :value="0">下架</label>
                </li>
            </ul>
            <button>修改</button>
        </form>

    </div>
</div>

<script>
    new Vue({
        el: "#app",  //作用域
        data() {
            return {   //初始数据
                Arr:null,
                keyword:"",
                newArr:null,
                onOff:false,
                areaState:0,
                xuanzeAll:false,
                chooseArr:[],
                chooseAllTwo:[],
                addMovies:{
                    link: "",
                    image: "",
                    title: "",
                    rating:"" ,
                    judge: "",
                    brief: "",
                    actor: "",
                    pbtime: "",
                    category: "",
                    state: ""
                },
                editMovies:{
                    link: "https://movie.douban.com/subject/1292052/",
                    image: "upload/top250/1.jpg",
                    title: "肖申克的救赎",
                    rating: 9.7,
                    judge: 2393173,
                    brief: "希望让人自由",
                    actor: "导演: 弗兰克·德拉邦特 Frank Darabont 主演: 蒂姆·罗宾斯 Tim Robbins ... 1994 美国 犯罪 剧情",
                    pbtime: 1658203087939,
                    category: 1,
                    state: 1
                }
            }
        },
        methods: {  //方法 函数
            getDate(){
                $.ajax({
                    url:"../source/upload/movie.json",
                    dataType:"json",
                    success:(data)=>{
                        this.Arr =data.map((item,index)=>{
                            item.id = index
                            return item
                        })

                    }
                })
            },
            searchFn(){
                if (this.keyword){
                    this.newArr =  this.Arr.filter(item=>item.title.includes(this.keyword))
                    console.log(this.newArr)
                    this.onOff = true
                }else{
                    this.onOff = false
                }
            },
            delOne(id){
                if (confirm("宁确定要删除吗")){
                    this.Arr = this.Arr.filter(item=>item.id!=id)
                }
            },
            changeXuanze(){
                    if (this.xuanzeAll){
                        this.chooseArr = this.Arr.map(item=>item.id )
                        this.chooseAllTwo = this.Arr.map(item=>item.id)
                    }else {
                        this.chooseArr=[]
                        this.chooseAllTwo =[]
                    }
            },
            addMovie(){
                event.preventDefault()
                let obj ={...this.addMovies}
                obj.id = this.Arr[this.Arr.length-1].id+1
                this.Arr.push(obj)
                this.areaState = 0
            },
            editMov(id){
                this.areaState = 2;
                let newObj = this.Arr.find(item=>item.id == id);
                let NewObj = {...newObj}
                console.log(NewObj)
                this.editMovies = NewObj
                console.log(this.editMovies)

            },
            editMovie(){
                event.preventDefault()
                console.log(this.editMovies)
                this.Arr = this.Arr.map(item=>{
                    if (item.id == this.editMovies.id){
                        return this.editMovies
                    }else {
                        return  item
                    }
                })
                this.areaState = 0
            }

        },
        created() {  //实例加载完成

        },
        mounted(){
            this.getDate()
        }
    })
</script>
</body>
</html>
```


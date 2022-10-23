# 	ES6

## ES6使用浏览器

###  PC端

| 浏览器       | 特性                   |
| ------------ | ---------------------- |
| Chrome 51版  | 支持95-98%的ES6语法    |
| Firefox 53版 | 支持95%-98%的ES6语法   |
| Safari 10版  | 支持98%-99%的ES6语法   |
| IE Edge 15   | 支持 94%-96%的ES6语法  |
| IE Edge 14   | 支持90%-93#的ES6新特性 |
| IE7-11       | 不支持                 |

### 移动端

| 浏览器       | 特性                     |
| ------------ | ------------------------ |
| IOS  10.0版  | 支持99%的ES6新特性       |
| Android  5.1 | 仅支持25%-30%的ES6新特性 |

##  ES5 变量

### 变量的定义（var）

var作用范围：

- 定义在最外层表示一个全局对象，整个网页中都可以使用。（挂载在window下）;
- 如果定义在函数中表示在函数范围内有用，函数范围外无法使用。
- 如果变量不是声名在函数体内
  - 全局定义：都可使用
  - 全局没有（隐式定义）： （如果赋值）全局都可以使用，（如果没有赋值去使用）报错

- 注意：变量可以先声明，再赋值;(在没有赋值之前是undefined);

###  变量的分类

- 全局变量：（window）任何地方都可使用。
- 局部变量：（function）只能局部使用，不能全局使用。

## ES6变量

ES6新增了块级作用域的概念，经典的就是`let`变量和`const`写法，使用上和`var`一样用来声明变量。

### let

块级作用域{ }，

let 是 ES6新增定义变量的关键字，使用于声名变量

```js
let 变量名=值;
```



特点：

- 使用let定义的变量会自带一个块级作用域;比如（{},if,for,function）
- 不能在定义之前使用。
  - let 变量，实际上是存在声明提升，只不过在提升时没做执行初始化操作，不能访问;必须赋值时才能使用。
- let 变量存在 TDZ(暂时性死区)

```js
function demo(){
    console.log(age); // TDZ  Cannot access 'age' before initialization
    let age=22;
    console.log(age); //22
}
```

### let 与 var 区别与联系

- 相同：都用于定义变量
- var 可以重复定义同一个变量，let 在同一作用域下不可以定义同一个变量。
- var 有声明提升，数据并初始化为 undefined; let 有声明提升，但是不会初始化，只有在赋值后才会被初始化。
- let 变量存在 TDZ(暂时性死区)
- let 分枝与循环时，let 变量都会被重新定义与赋值；保证变量在每个代码块中是单独的。

### const

const 是 ES6新增定义变量的关键字，使用于声名变量

```js
const 变量名=值;
```

const 特点与let：

- 相同：具有与let 一样的特点。

- 不同点

  - 数据定义时必须赋值，数据不可更改。 

  - 如果修改const定义的基本数据类型会报错。但是引用数据类型不会报错。(例如数组中使用push之前的就不会报错)

    

```js
const PI=3.14
PI=3  //ERROR
const ARR=[2,3,4]
ARR.push(5) //改变的是堆的数据,栈地址没有改变, 只要栈中地址没有改变,会认为该值没有被修改
```

## (变量)作用域

- 作用域分类

  全局作用域：(window) 变量在网页中任何地方都可以被访问。

  函数作用域：代码块范围（{}）变量在函数中任何地方都可以被访问。

  

```js
var x=3,y=6,z=9;  //全局使用域 let const
function fn(){ //fn 函数作用域
    var x=33,y=66;  
    console.log(x,y); //33,66
    function sunFn(){ //sunFn 函数作用域
        var x=333,y=666;   
         console.log(x,y,z,m); //333,666,9  error
    }
    sunFn()
}
 fn()
console.log(x,y)  //3,6
```

作用域有包含与被包含的关系（上下级关系），当使用变量时，要注意变量的查找范围(就近原则)

## 作用域链

概念：作用域中变量查找的顺序（使用一个变量时，用户的变量是局部变量，还是全局变量）

流程：当访问变量时，先从访问变量代码所在作用域中查找该变量。如果有则使用。如果没有，则去外层作用域去查找，直到查找到全局作用域中，如果全局也没有，则报错。.这种逐层向上查找的方式。所形成的链条就叫**作用域链**

```js
let c=34
function fa(){
    let c=22,a=33;
    function son(){
        let b=2,a=6;
        console.log(a,b,c) //6,2,22
    }
    son()
}
fa()
console.log(a,b,c)  //error  error  34
```

## 值传递

### 参数传递(基本)

```js
let age=18;
function fn(x){  //var x=age
    x=x*2
    console.log(x) //36
}
fn(age)
console.log(age);  //18
```

**<font color='red'>因为是基本数据类型，所以不会改变原值</font>**

### 参数传递（对象）

```js
let obj={age:10}   //引用数据类型 
function fn(tmpObj){  //var tmpObj=obj   地址
    console.log(tmpObj==obj)   //true
    tmpObj=JSON.parse(JSON.stringify(tmpObj)) //改变了变量所在的栈的地址,不会影响 obj
    console.log(tmpObj==obj)   //false
    tmpObj.age=4;
    console.log(tmpObj) // {age:4}
}
fn(obj)
console.log(obj);  //{age:4}
```

**<font color='red'>因为是引用数据类型，复制的是堆的地址，修改会一起修改</font>**

但是使用JSON的方法就是深拷贝，一样的数据不一样的地址，不会改变原值

## 变量的内存分配(栈与堆)



### 基本数据类型(String,Number,Boolean,undefined,null)

- 变量定义为一个基本数据类型时，JS会在栈里分配一块内存空间用户于保存数据，该区域保存的是变量名与值；当访问变量时，返回变量对应的值。
- 赋值时，var a=33,b=a; 实际是在创建b变量时，JS会分配新的内存空间，把a的值给变量b。实际中a,与b的值不在一起。二者互不干扰。

### 引用数据类型(Array,Object,Function)

- 变量定义为一个引用数据类型时，JS会在堆中分配一块可动态增长的内存区域保存对象的数据（堆地址），然后再到栈里分配一块区域用于保存对象数据对应的堆空间的内存地址;
- 赋值：var obj={},obj2=obj;  将栈里对应的堆空间的内存地址赋给变量。

| 栈 (变量名)       | 值    |
| ----------------- | ----- |
| obj               | 0x001 |
| tmpObj            | 0x001 |
| //deepcopy tmpObj | 0x002 |
| a                 | 33    |
| b                 | 33    |
| obj               | 0x003 |
| obj2              | 0x003 |

| 堆(地址) | 值                  |
| -------- | ------------------- |
| 0x001    | {age:10} -> {age:4} |
| 0x002    | {age:10}            |
| 0x003    | {}                  |



## 变量提升

### 概念

变量提升：指网页中JS代码在解析运行之前，浏览器会对所有的js代码进行一次预解析，在预解析中会找到所有的全局变量（var）全部**声明**到作用域的最前面，然后再开始解析JS代码。

### 全局作用域变量提升

```js
console.log(username); //undefined
var username="yanhong";
console.log(username);
/*
浏览器解析JS代码过程
  */
var username;
console.log(username);  //undefined
username="yanhong";     //赋值
console.log(username);  //输出 yanhong
```

说明：变量 userName 从原来位置被提升到代码的最前面进行声明操作，但是没有被赋值，所以第一次输出是 undefined,再执行赋值操作后，第二次输出就是指定的赋值。

### 函数内的变量提升

```js
  function fn(){
        console.log(username); //undefined
        var username="yanhong";
        console.log(username);
    }
    fn()
    /*
    浏览器解析JS代码过程
      */
    function fn(){
        var username;
        console.log(username);  //undefined
        username="yanhong";     //赋值
        console.log(username);  //输出 yanhong
    }
    fn()
```

###  let没有变量提升动作（const同理）

概念：ES6中为了规范变量的使用，定义 let 没有变量提升的操作。

```js
console.log(user)  //TDZ error
let user="tongqiang"
```

报错说明：let定义不能在数据在初始化之前调用，说明了 let 变量没有提升操作。

## 函数提升

###  函数的定义

在JS中函数的声明分为两种方式：**声明式函数、函数表达式**

- 声明式函数

```js
function fn(){}
```

- 函数表达式

```js
var fn=function(){}
```

### 函数提升

概念：声明式函数和 var声明变量一样，也有提升的动作。

```js
fn()
var method="函数方法"
function fn() {
    console.log("fn")
}
/*
*
* 函数的提升
* 浏览器解析过程
* */
var method;
function fn() {
    console.log("fn")
}
fn()
method="函数方法"
```

- **<font color='red'>注意：函数表达式，是一个变量，存在变量提升，没有“函数提升”的概念;</font>**

```js
console.log(fn)  // undefined
var fn=function () {
    console.log("hello fn")
}
fn()
console.log(fn2)  // function
function fn2 () {
    console.log("hello fn2")
}
fn2()
```

### 函数与变量的名称冲突

编写代码时，要避免变量名与函数名同名.

```js
console.log(fn) //
function fn(){
    console.log("function")
}
var fn="string"
console.log(fn)  
// 浏览器解析代码过程
var fn;
function fn(){
    console.log("function")
}
console.log(fn)   //function
fn="string"
console.log(fn)   //string
```

- 说明：变量与函数都会提升：**变量的提升优于函数的提升**

### 函数参数的默认值

概念：参数（形参，实参。一般来说是一一对应的）

```js
function  fn(x,y,z){  //var x,y,z
   /* if(x==undefined){x=0}
    if(y==undefined){y=0}
    if(z==undefined){z=0}*/
   x=x||0
   y=y||0
   z=z||0
    return x+y+z
}
//fn(1,2,3)
let res=fn(1)
console.log(res)
```

- ES6开始可以增加默认值

```js
function fn(x=0,y=0,z=0){
    return x+y+z
}
fn();   //0
fn(1); //1
......
```

- 注意：当有默认值的参数与普通参数一起调用时，需要把有默认值的参数放到普通参数的后面

```js
function page(arr,page=1,pageSize=10){ // var arr=users
}
page(users)
function get_ajax(url,data={}){
}
```

- **<font color='red'>不能跳过默认参数进行传参</font>**，error

```js
function fn(x=0,y,z=0){  
    console.log(x+y+z)
}
fn(,3,)  //error
```



###  ES6 可变参数

当函数的参数个数不确定时，可以使用不定参数来接收，不定参数的接收形式为 `...变量名`(**三个小点是扩展运算符**)

```js
/*  function fn() {
      console.log(arguments)
  }*/
function fn(...arg) {
   console.log(arg)
}
fn(1,3,5,"abc",{name:"tom"},[1,67])
```

- 不定参数arg只能定义在**形参**的**最后**,并且只能有**<font color='red'>一个不定参数</font>**。否则会报错。不定参数没有默认值。

```js
function fn(x,y,...arg){ //var x=1,y=2,arg=[3,4,5,,6]
    console.log(x,y,arg)
}
fn(1,2,3,4,5,6)
```

## 扩展运算符

是ES6 新增的一个特殊的运算符，也称Rest运算符。能够简化一些针对**数组**和**对象**的复制和合并、展开等操作

###  语法

```js
...变量名
```

- 变量名保存数据类型的不同，扩展运算符会有不同的效果

  **<font color='red'>可变参数一定要放在形参的最后位置并且只能使用一次</font>**

### 数组中的应用

官方的源代码中push就是使用...item的





- 合并数组

  ```js
  var arr1=[1,2,3],arr2=["a","b","c"];
  console.log(arr1.concat(arr2))  //es5
  console.log([...arr1,...arr2]) //es6
  ```

- 复制数组(产生的是一个新数组)

  ```js
  ////////es5/////////////
  let arr4 = []
  for(let arr of arr1){
      arr4.push(arr)
  }
  
  ////////es6/////////////
  var arr3=[...arr1]
  console.log(arr1==arr3)  //false
  
  
  ```

- 在数组api中的应用

  ```js
  var arr4=["yangjing"]
  arr4.push(arr1) //["yangjing",[1,2,3]]
  arr4.push(..arr1)  // ['yangjing', 1, 2, 3]
  ```

- 将dom标签的类数组对象转为真正的数组

  原生获取的结点是数组，但是jq获取的是类数组

```js
let lis=document.querySelectorAll("#nav li")
console.log(lis); //类数组
let arr=[...lis]
console.log(arr); //真数组
```

**<font color='red'>只能深拷贝第一层的数据，第二层的数组还是复制堆里的地址</font>**

### 对象中的使用

- 合并对象 (产生的是一个新对象)

  ```js
  var user={name:"xingyu",age:18}
  var userInfo={gender:1,tel:13456789786,name:"abc"}
  
  /////////es5//////////////////
  es5中对对象的深拷贝
  let newObj={};
  for (let key in user){//获取对象的所有属性名
      不能直接user.key,因为key可能是字符串但是可以用user['key']
      let val = obj[key]//获取到属性的值
      newObj[key] = val;//给新对象添加属性
  }
  
  
  
  
  /////////es6///////////////
  //展开对象的数据，然后放入到新的对象中
  var obj={
    ...userInfo,
    ...user
  }
  //属性相同情况下,以最后录入的属性为准
  console.log(obj);  //{gender: 1, tel: 13456789786, name: 'xingyu', age: 18}
  ```

- 复制对象(产生的是一个新对象)

  ```js
  var obj2={...user}
  ```

- 在网络请求中的作用

  ```js
  //let users=[{username:”tongqiang”,pwd:”tttqqq”}]
  var formObj={ //0x001
      username:"root",
  	pwd:"123456"
  }
  function post_ajax(){
      $.ajax({
      url:"....",
      type:"POST",
      data:{...formObj},
         //.....
  })
      }
  ```

**<font color='red'>可以避免改变原对象数据</font>**

### 函数中的运用

- 作为形式参数：将所有的实际参数组合成一个**<font color='red'>数组</font>**

  ```js
   function fn(...arg) {//[1,3,5,"abc",{name:"tom"},[1,67]]
       console.log(arg)
    }
    fn(1,3,5,"abc",{name:"tom"},[1,67])
  ```

- 作为实际参数：将数组里的每个数据都作为一个实际参数

  <font color='red'>arguments是类数组对象</font>
  
  ```js
  function fn() {
    console.log(arguments)
    let arr=[...arguments]
    console.log(arr)
  }
  fn(1,3,5,"abc",{name:"tom"},[1,67])
  ------------------------------------
  var arr=[1,2,3,4,5,6]
  function sum(x,y,z) {
      console.log(x+y+z)
  }
  // sum(arr[0],arr[1],arr[2])
  sum(...arr)
  ```

### 字符串中的应用

- 展开字符串（字符串转化为数组）

```js
var str="abcdefgh";

///////////es5////////////////////////////////
let xx = []
for(let i =0; i<str.length;i++){
    xx.push(str.charAt(i))
}

//////////es6//////////////////////////
console.log(str.split(""))
console.log([...str])// ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h']
```

### 总结

- 一般来说，无论是数组还是对象，扩展运算符作用是展开里面的内容。
- <font color='red'>在函数中作为形参</font>时，扩展运算符会把所有的实参合并成一个数组。（一个形参的情况下）



## 函数的扩展 ES6 箭头函数（匿名函数）

###  箭头函数语法

ES6中提供了一种简洁的函数写法，称作“箭头函数”。

**特点**：写法中注意点

- 箭头函数只能使用赋值写法，不能使用声明式写法。
- 如果箭头参数只有一个，可以省略小括号。
- 如果箭头函数代码块只有一句话，可以不加大括号。
- 如果箭头函数代码块没有大括号，后面值会默认加return.
- 箭头函数没有自己的,arguments,this,super
- 箭头函数不能使用new 语法。
- 箭头函数没有 prototype 属性
- <font color='red'>使用箭头函数只返回的是一个对象时，要使用小括号.()=>({name:"xxx"})</font>

```javascript
let fn=()=>{
}
let fn=res=>{
}
let fn=()=>console.log("hello");
let fn=(a,b)=>a+b  //let fn=(a,b)=>{return a+b} 
let fn=()=>({name:"shuke"})

使用箭头函数只返回的是一个对象时，要使用小括号()=>({name:"xxx"})

let f6 =()=>{
    return {id;1,name:'xx'}
}


let f6 = ()=>({id:1,name:'xxx'})

```

#### 使用场景：

可以替代数组高级方法中的匿名函数



#### 不能使用的场景

箭头函数本身是没有this的，如果在箭头函数中使用了this，则这个this指向的是父级作用域

如果用let创建变量的话，使用this一定是指向window，但是用let创建不会挂载在window下，用this是默认指向window

**<font color='red'>不能再DOM事件中使用箭头函数来绑定元素事件</font>**

```javascript
let ipt = document.getElementById("keyword");
//真确写法
ipt.onchange=function(){
    console.log(this.value)
    //在Dom事件函数中的this：就是触发该事件的这个HTMl节点
}
```



#### this

普通函数中的this就是谁调用就是谁

### 无参数无返回值

```js
var fn=()=>{
    console.log("hello")
}
```

###  单个参数无返回值

```javascript
var fn=(x)=>{
    console.log(x)
}
fn(3)
```

### 多个参数无返回值

```javascript
var fn=(x,y,z)=>{
    console.log(x)
}
```

###  有参数有返回值

```javascript
var fn=(x,y,z)=>{
  return x+y+z
}
let res=fn(3,6,8)
console.log(res) //17
```

### 箭头函数处理this

特点：箭头函数中的this始终指向箭头函数定义的离this最近的一个函数，如果没有最近的函数就指向window.

箭头函数会默认绑定外层this值，所有在箭头函数中this的值与外层的this是一样的。

```javascript
//<button id="btn">按钮</button>
var btn=document.getElementById("btn")
btn.onclick=()=>{
    console.log(this)   //window
}
```

**<font color='red'>也就是说在箭头函数中国，this会指向是点击他的父母而不是点击他的那个</font>**

##  函数扩展

### 上级作用域

函数包裹函数时，subFn函数的上级作用域在哪里创建，subFn函数的上级作用域就是谁。

```javascript
var x=3
function fn(){
    var x=54
    function subFn(){
        console.log(++x)
    }
    subFn()
    return subFn
}
var res=fn()  //55  res-> subFn
res()  //?56
```

###  IIFE

(immediately invoked Function Expression)- 立即调用函数表达式

```javascript
//写法1
(fuction(形参){
 //code
 })(实参)
(function (x) {
    console.log(x)
})(3)
//写法2
(fuction(形参){
 //code
 }(实参))
(function (x) {
    console.log(x)
}(3))
```

- 优点
  - 创建一个块级作用域，避免与全局的变量与函数冲突，也避免了多人协作开发时引发的命名冲突;
  - IIFE中任何的变量与函数，都会在执行后销毁。减少了占用内存问题。IIFE执行完成后会立即销毁其作用域链。（自己也会销毁）

## 回调函数

```js
1. 回调函数一般都作为另一个函数的参数来使用
2. 回调函数不会立即执行，而是满足一定条件后执行

 let arr = [1,2,3,4,5,6,7,8,9,10];
    arr.forEach(function (val) {
        console.log(val);
    }); // 每循环一次，回调函数function就会执行一次



 // 回调函数的场景
    function f(callbackfn) {
        setTimeout(function () {
            let msg = "今天是个好日子!!!";
            callbackfn(msg);  // 条件满足时调用该回调函数
        },1000);
    }

    // 回调函数可以处理异步编码中的结果
    f(function (data) {
        console.log(data);
    });


```

##  递归

递归是程序的编程技巧，指的是**函数调用自身的过程**。

应用1、计算阶乘

```js
递归的递推公式
6! = 6*5*4*3*2*1
6！=6*5！
5！=5*4！
4！=4*3！
3！=3*2！
2！=2*1！
1！=1

function jiecheng(num){
    if(num == 0 || num == 1){
        return 1
    }
	return num*jiecheng(num-1)
}
console.log(jiecheng(6))
```

应用2、后台列表菜单动态增加

多级菜单首选 dl>dt+dl

当循环也解决不了的时候用递归肯定是第一选择

```js
<dl>自定义列表
    <dt></dt>标题
	<dd></dd>列表项
</dl>



[
  {"title" : "首页"},
  {
    "title" : "学生管理",
    "items" : [
      {"title" : "学生列表"},
      {"title" : "新增学生"}
    ]
  },
  {
    "title" : "班级管理",
    "items":[
      {"title" : "班级列表"},
      {"title" : "新增班级"},
      {
        "title" : "班级专业",
        "items" : [
          {"title" : "Web前端", "items" : [{"title":"TC58期"},{"title":"TC62期"},{"title":"TC65期"}]},
          {"title" : "Java开发","items" : [{"title":"TC50期"},{"title":"TC59期"},{"title":"TC60期"}]},
          {"title" : "测试开发","items" : [{"title":"TC59期"},{"title":"TC64期"}]}
        ]
      }
    ]
  },
  {
    "title" : "讲师管理",
    "items": [
      {"title" : "讲师列表"},
      {"title" : "新增讲师"}
    ]

  },
  {
    "title" : "班主任管理",
    "items": [
      {"title" : "班主任列表"},
      {"title" : "新增班主任"}
    ]
  },
  {
    "title" : "教室管理",
    "items" :[
      {"title" : "教室列表"},
      {"title" : "新增教室"},
      {"title" : "编辑教室"}
    ]
  }
]

在企业中有多级菜单
function menu (data){
    let tmp = data.map(item=>{
        if(menu.items){
            return`<dl>
				<dt>${item.title}</dt>
				<dd>${menu(item.items)}</dt>
</dl> `
        }else{
            return`<dl>
				<dt>${item.title}</dt>
				
</dl> `
        }
    })
}

```









```js
function fn(){
    //需要条件判断来结束递归
    if(condition){
        return ;  //结束递归
    }
    fn() //函数通过调用自己来实现循环
}
fn()
//eg1
var i=1
function fn() {
 console.log(i++)
 if(i>10){
     return;
 }
 fn()
}
fn()
//eg2
function fn(i) {
   if(i>10){
       return;
   }
   console.log(i)
   fn(++i)
}
fn(1)
```

- 实现的一般流程
  - 使用前要确定使用递归来做什么，功能点在哪？
  - 递归实现的是把一个大的功能分解成小的功能块。
  - 设置递归结束的分解点。



```js
//实现累加 1-100
function sum(num,count=0) { //num 参数 累加    count 求和
    if(num<=100){   //判断 1-100
        console.log(num)
        count +=num  //累加
       return sum(++num,count) //return 起到什么作用?
    }else {
        return count
    }
}
let res=sum(1)
```

##  闭包

### 概念

- 条件
  - 函数嵌套
  - 嵌套的函数可以持续访问局部变量。

概括： 闭包就是能够读取其他函数内部变量的函数。



JS的机制就是如果里面的函数还引用这外面的变量，则外面的函数在调用完后不会被销毁

```js
闭包： 当一个函数在执行完成后，由于其他地方还要继续使用这个函数
      内部的数据，导致这个函数的变量对象在销毁的时候并没有销毁。
      因此，这个函数内部的函数就形成了一个闭包。
      
```

形成条件

```js
  闭包形成的条件：
            1.  函数之间有嵌套
            2. 内部函数中使用外部函数定义的数据
            3. 内部函数在声明创建以外的作用域被调用
```

优劣势

```js
闭包优势：
   1. 延迟变量的使用时间
   2. 闭包可以让有些数据一直保存在内存中（可以当做内存缓存来使用）
   3. 避免全局变量名的污染（防止命名冲突）
闭包劣势：
   滥用闭包会造成内存溢出（闭包会占用独立的内存空间，大量使用闭包就会导致
   内存占用过多，进而影响网页性能）
```

```javascript
var n=1;
function fa(){
    var n=5;
    function son(){ //闭包
        console.log(++n); 
    }
    return son
}


 function outer() {
       var a = 1; // 闭包可以让这个a变成一个缓存数据（一直在内存中不销毁）
       function inner() {
           console.log(a++);
       }
       return inner; // 函数对象地址
    }

    let f = outer(); // 此时返回的f就是outer内部定义的inner函数
    //此时：函数inner内部引用outer函数中的变量a
    // f();
    // f();
    // f();
    // f();
    // f();






```

面试案例，建议多看20220902-08闭包

```js
  面试： 请编写一个用于不定参数求和的一个【高效】函数？
    function add() {
        let sum = 0;
        for (let i = 0; i < arguments.length; i++) {
            sum += arguments[i];
        }
        return sum;
    }
     我们将来会比较频繁的使用这个函数
    问题： 假设每次传递的参数都是一样的，无论怎么计算，它返回的结果都是一样的，这样重复操作代码区每个都计算就会浪费大量的时间
    解决方案：通过缓存机制来提高函数的性能（计算的结果保留下来，下次不用计算就可以直接获取）

   function tmp() {
        let cache = {}; // 为了缓存计算后的结果
        // 实现参数的累加求和
        function cal(){
            let key = JSON.stringify(arguments); // 将参数转换成字符串来记录
            if(cache[key]){ // 判断缓存中是否存在这个key
                return cache[key];
            }else{  // key不存在
                let sum = 0;
                for (let i = 0; i < arguments.length; i++) {
                    sum += arguments[i];
                }
                cache[key] = sum; // 缓存以前计算过的结果
                return sum;
            }
        }
        return cal;
    }
    let add = tmp();
```









- 在JS中，函数内部分的变量与函数只能局部访问，使用闭包可以进行访问局部变量。所有闭可以理解成“定义在函数内部的函数”
- 本质上，闭包是将函数内部与外部连接起来的桥梁。

### 作用

- 由于外部不能访问函数内部的变量，而且函数执行后会立即销毁（变量，函数），外部不可访问。为了有效的避免多人开发时由于全局变量过多而引起的命名冲突问题.另外基于作用链机制。局部变量的访问速度比全局变量的访问速度快。使用闭包可以提升程序的运行速度

- 闭包可以实现方法和属性的私有化；

### 劣势

- 容易导致内存泄漏。闭包会包含其函数作用域。因此他比其它函数要占用更多内存，过度使用闭包，会导致内存使用过多，出现网页与系统的性能问题。（解决方案：当退出函数之前，将不再使用的局部变量全部删除。）



## 解构赋值

### 解构数组

es6新语法

```js
let arr = [1,2,3,4]
let a = arr[0]
let b = arr[1]
let c = arr[2]
let d = arr[3]


let[a,b,c,d]=arr
```

还可以进行动态操作将10和30分别赋值给x,y

```js
let[x,,y]=arr
是可以用逗号隔开

```

特殊赋值

```js
let a = 10,
    b = 20

如果想把两个数值交换赋值E

es5是另外创建一个变量存放某一个值
let x = a
 a = b
b =x

S6的方法
let arr = [a,b];
 [b,a] = arr

简化  [b,a] = [a,b] 
```





### 解构对象

```js
const user ={id:1,username:"admin",password:"1234",age:28}
需要将各个属性值赋值给对应的变量
//es5语法获取对象的属性值
let id = user.id
let username = user.username
........

//es6 提供了对象的解构赋值
原则：对象根据属性来解构数据，赋值的时候会根据变量名来赋值
let {需要与对象里的键对应，一定是对象里的属性，可以随意选择想要的} = user;
let {id,username} = user;
约等于 username = user.username

----------------------------------------------------------

let {username:name，password:pwd} = user;
约等于 let name = user.username
输出就是name或pwd
用这个方法可以改变想要获取的值的属性名


```



### 使用场景

#### 解构字符串

```js
let str = '中国上海'
let ch1 = str.charAt(0)
let ch2 = str.charAt(1)
.......
console.log(chi1,chi2)

///////////////////////es6
let [ch1,ch2]=str
与数组结构一致，还可以空着逗号
```

#### 交换两个变量值

```js
let a =10;
let b = 20;
///////////es5/////////////
let c = 0;
c = a 
a = b 
b = c

///////////es6////////////////////
let arr = [a,b];
[b,a] = arr
不需要加let，因为之前定义过了，只是交换
简化
[b,a] = [a,b]
```

## 对象速写属性与速写属性值

```js
let id =1;
let username = 'admin';
let password = '123'

let stu{id,username,password}
如果属性名与变量一样，那么就可以直接写




sut2.age = 18
stu2['gender']='男'
stu2['sleep time'] = 12
为了防止有特殊属性名，可以直接在[]里写字符串就可以放特殊属性名



获取的时候也要
stu2['sleep time']




从对象中删除某一个属性
dele.stu2.password//删除stu2对象的password属性
当删除特殊的属性名
dele stu2['sleep time']


在对象中添加方法
let util={
    info:'xxx',
    add:function(x,y){
        return x+y
    }
}

在对象中速写方法
let util={
    info:'xxx',
    add(x,y){
        return x+y
    }
}

util.add(3,4)
```



## Set集合去重

```js
传统数组去重
let arr = [1,2,1,3,4,5,6,1]
let new = []
for (let item of arr ){
    //判断new数组中是否存在item元素，若不存在则放入数组
	if（!new.includes(item)）{
        new.push(item)
    }
}

es6为了模仿java，提供了set集合
let brr=[10,20,12,10,15,25,2]
let set = new Set(brr);//将数组元素放入set集合中,是类数组
再将set集合转换成数组
let xx = [...set]

//////现在用法
let arrNew = [...new Set(brr)]

```

### Set的其他用法

**<font color='red'>在set集合中是没有下标的</font>**

```js
1.创建set集合
let mySet = new Set();
2.添加数据
mySet.add('xx')
mySet.add('xx')
mySet.add('ax')
mySet.add('ax')
还是会去重
还能支持链式
mySet.add('xx').add('xx').add('ax').add('ax')
因为返回的还是mySet集合

3.删除集合元素
mySet.delete('xx')按照元素内容来删除数据

4.判断Set集合中是否存在某一个值
mySet.has("tom")有的话返回true

5.set集合中的元素个数
mySet.size

6.清空集合
mySet.clear()

7.遍历set集合
只能用for of 循环
for(let ele of mySet){
    
}
```

## 存储键值对的集合Map

Map模仿了java语法的用法

**<font color='red'>在今后开发中，如果需要存储key:value这种结构的数据，推荐使用js对象</font>**

```js
1.创建map集合
let map = new Map()

2.向map集合中添加键值对
map.set("id",1);
map.set('username','admin')
map.set('password','123')
map.set('password','1111')key相同的时候，value会被覆盖

3.根据key来获取value
map.get("id")

4.根据key删除键值对
map.delet("id")

5.map集合中一共多少键值对
map.size

6.判断map集合中是否存在key
map.has("id")

7.清空
map.clear()

8.遍历
for(let item of map){
    console.log(item)
}取到的是一个键值对数组


mao.forEach(function(val,key){
    console.log(val,key)
})
```



## 模板字符串

支持在${}使用三元运算符

## 数组扩展

`ler arr = newArray(10)`10个长度的数组

​	`for of 遍历数组没下标`

`数组不要使用 for in`

### for of 

```js
let arr = [1,2,3,4]
for(let item of arr){
    console.log(item);
}
	`for of 遍历数组没下标`
```



### forEach

主要就是遍历数组的元素

无返回值

```js
let crr = [1,2,3,4,5]
crr.forEach(function(val,index,self){//一个的话就是值
    consloe.log(val,index)
})
```

### map

可以将每次循环后的return的数据放入到一个新数组中

返回的是数组对象

操作加工数组的每一个元素，并返回到一个新数组中

```javascript
let arr =[1,2,3,4,5,6]
arr.map((val,index,self)=>console.log(val,index,self))
```

### filter

数组.filter(xx)

index,self可以省略



1、遍历数组中每一个元素

2、每次循环都会执行函数，当返回true时放到新数组中

3、filter返回是一个数组

```javascript
let arr = [1,2,3,4,5,6,7,8,9,10];
let x = arr.filter(function(val,index,self){
    console.log(val,index,self)
})

```

### find

**<font color='red'>查找的是满足条件的第一个元素，不存在返回undefined</font>**

**<font color='red'>返回是的数组中原对象,不是新对象，浅拷贝原对象的地址</font>**



### every()、some()

**every：如果每次循环返回的条件都是true则every是结果就是true，只要有一个为false，则every的结果就是false**

主要用来判断所有的条件是否都满足



```javascript
let socres=[67,89,56,90,78,98]
//1.判断所以成绩是否都及格了

let flag = true

//传统解法
for (let val of socres){
    if(val < 60){
        flag = false;
    	break
    }
}

socres.forEach(val=>{
    if(val < 60){
        flag = false;
        //forEach不支持break
    }
})

/////新兴解法

socres.every(val => val>=60);//返回的是true或false


```





**some：如果每次循环的条件有一个是true则some是结果就是true**

```javascript
let socres=[67,89,56,90,78,98]
//判断成绩中是否存在90分及以上的分数?

socres.some(val=>val>=90)
//只要有一个90分及以上就是true

```



### reduce

一般可以累积求和，返回新值

一般index，self都省略

```javascript
let arr=[10,20,30,40,50]
arr.reduce(function(result,val,index,self){//上次循环返回的结果
    
},result)赋了一个初始值。如果不写，那就默认是数组第一个元素，遍历会从数组第二个元素开始


///////////////////////////////////////

```

### flat

```javascript
let arr[1,2,3[4,5,[6,7[8,9]]],[10,11]]
处理这种多重嵌套的数组
let mew =  arr.flat(1)去掉一重嵌套的数组//[1,2,3,4,5[6,7[8,9]],10,11]
ler new  = arr.flat(3)
在处理数组扁平化时，深度一定要写数组中嵌套的做大深度(完全展开)
```



### 小总结

```js
 //1.数组删除元素
    let arr = [1,22,3,4,5,6,7,2,2,2,]
    //删所有的2
    /*
    for (let i =0;i<arr.length;i++){
        if (arr[i] == 2){
            arr.splice(i,1)//截取的时候数组会整体向前移动，但是索引会向后移动
            i--;
        }
    }
    */
    //但是从后向前删就不会出问题，推荐删除数组元素的时候用倒着删除就

    for (let i=arr.length-1;i>=0;i--){
        if (arr[i] == 2){
            arr.splice(i,1)//截取的时候数组会整体向前移动，但是索引会向后移动
        }
    }

    //2.数组去重
    let brr=['admin','jack','admin','luck','luck']
    /*
    let newArr =[]
    for (let name of brr){
        if (!newArr.includes(name)) {
            newArr.push(name)
        }
    }
    */
    // es6
    let newArr = [...new Set(brr)]

//3.数组求最值，求和
let nums = [-1,9,10,8,3,4,6,21,23]
    let max = nums[0]//假设第一个元素是最大值
    let min = nums[0]//假设第一个元素是最小值
    for (let i =1;i<nums.length;i++){
        let num = nums[i];
        if (num > max){
            max = num
        }
        if (num <min){
            min = num
        }
    }

    //综合，在唱歌比赛中有10个评委打分,9.7 , 9.6 , 9.5 ,9.1 ,9.2 ,9.8 , 10.0 ,9.8 , 9.9,9.4
    let chengji = [9.7 , 9.6 , 9.5 ,9.1 ,9.2 ,9.8 , 10.0 ,9.8 , 9.9,9.4]
    
    //////////////////原生/////////////////////////
    let max = chengji[0] //假设第一个分数为最高
    let min = chengji[0]//假设第一个分数为最底
    let sum = chengji[0] //所以分数总和
    for(let i =1;i<chengji.length;i++){
        let score = chengji[i]
        if(score>max){
            max = score
        }
        if(score<min){
            min = score
        }
        sum+=score
    }
	let avg = (sum-max-min)/(chengji.length-2)
    avg = avg.toFixed(2)；
    console.log(avg)
    
    
    ///////////es6//////////////
    /*
    chengji.sort((a,b)=>a-b)
    chengji.pop()
    chengji.shift()
    let allsun = chengji.reduce(function(data,value){
        return data+value;
    })
    console.log(`这位选手的成绩为${(allsun/(chengji.length)).toFixed(2)}`)
	*/

//4.数组的排序
    let stus = [{id:'wnsh1001',name:'张三',math:80,chinese:90},
        {id:'wnsh1002',name:'李四',math:70,chinese:40},
        {id:'wnsh1003',name:'王五',math:90,chinese:70}]
    //4.1按照数学成绩降序
    /*
    stus.sort(function (a,b){
        return b.math-a.math;
    })
    */
    //4.2按照总分降序排序
    stus.sort((a,b)=>(b.chinese+b.math)-(a.chinese+a.math))
```

## RegExp 构造函数正则函数

### 在 ES5 中，`RegExp`构造函数的参数有两种情况

```js
var regex = new RegExp('xyz', 'i');
// 等价于
var regex = /xyz/i;
```





# ES5面向对象

面向对象是一种程序设计的思想，是一种编程的方式，是一种编程思想



应对不同的应用场景 封装，继承，多态

## ES5创建对象

三种
1、js提供了一个构造函数Object(内置的函数，可以直接使用)
2、可以通过字面量的方式来简化对象{}
3、可以自己定义构造函数来创建对象(类型更加明确)

```js

1、通过obj函数来创建对象
let obj = new Objexct()
obj.nam='xxx'
obj['xxx']=xxx

2、简化创建对象(底层就是new Obkect（）)
let obj2 = { }
let o1 = {id:1,name:'张三',birthday:"1988-09-07"}
let o1 = {id:1,name:'老王',age:45,hobby:"打麻将"}

----------------------------------------------------------------------
问题：无法分辨o1，o2到底是什么类型的对象（学生? 员工？）


为了对象的类型明确，我们可以创建构造函数来创建对象

构造函数本质也是一个函数，只不过这个函数会配合new关键字来使用

行业规范:建议将构造函数的首字母大写(大驼峰)
funciton Student(){
}
Student()此时，这个函数就是当做普通函数来调用的

let stu = new Student()//此时这个Student就是构造函数
stu.id = 1;
stu.name = '小明'


function Product(){
    
}

let pro = new Product()
pro.id=1;
pro.name = '锤子手机'



```



## 构造函数

构造函数 ：在ES5中中一种特殊的函数，主要用来初始化对象（属性+方法），

它一般会和new关键词来配合使用

```js
 function Person(id,name) {
        // console.log(this); // 构造函数中的this就是刚刚创建出来的这个新对象
        this.id = id;
        this.name = name;
    }
```

构造函数中的this就是刚刚创建出来的这个新对象



批量化创建对象

```js
 // 构造函数中的this指向的就是刚刚创建出来的这个对象
    function Product(id,name,price,stock) {
       this.id = id;
       this.name = name;
       this.price = price;
       this.stock = stock;
       this.info = function () {
           console.log(`Product{id=${this.id},name=${this.name},price=${this.price},stock=${this.stock}}`);
       }
    }

    // 通过new创建出来的对象：实例对象
    let pro1 = new Product(1,"华为P40",4888,10000);
    let pro2 = new Product(2,"华为P50",5888,1000);
    let pro3 = new Product(3,"华为P60",6888,1000);
```



## new关键词

作用

1、在对堆空间中创建新对象

2、将this指向新创建的这个对象

3、执行构造函数内的代码(给对象添加一些属性或方法)

4、返回对象在堆中的地址（<font color='red'>构造函数中不用写return</font>）



**实例对象 (实例)** ： 通过构造函数创建出来的这个对象被称作实例对象(实例)









### **in运算符**

可检查对象中是否含有指定的属性

有返回true，没返回false

**语法："属性名"  in  对象**



## 原型对象

万物皆对象object

<font color='red'>object的原型prototype是最大的（Object.prototype）</font>



###  什么原型对象

`prototype`

通过构造函数来获取原型

每个函数都有自己独立的原型对象

但是每个函数的原型对象的原型对象（也就是object的原型对象）是一样的

object的原型是任何一个对象原型链的终点



每个构造函数都有个`prototype`属性

一个构造函数只有唯一的一个原对象，所有的实例对象共享同一个原型对象

<font color='red'>通过构造函数创建出来的所有实例对象，共享该构造函数的原型对象</font>
`__proto__`



像我们的数组Array，正常使用需要new Array



最好是在Object.prototype.想要的名字 = xxx



我们创建出来的每个数组对象它指向的原型都是构造函数`Array`的原型对象

```javascript

let arr = new Array(1,2,3,4,6)//[1,2,3,4,6]
```



![image-20220910123023752](C:\Users\TOM\AppData\Roaming\Typora\typora-user-images\image-20220910123023752.png)





**<font color='red'>console.dir(Array)</font>**

![image-20220910122847863](C:\Users\TOM\AppData\Roaming\Typora\typora-user-images\image-20220910122847863.png)





![image-20220910123545873](C:\Users\TOM\AppData\Roaming\Typora\typora-user-images\image-20220910123545873.png)

![image-20220910123658241](C:\Users\TOM\AppData\Roaming\Typora\typora-user-images\image-20220910123658241.png)



###  对象的隐式原型

在JS中，每一个对象都会自带一个属性`__proto__`, 默认指向了构造函数的 `prototype`的原型对象

![image-20220801141840405](https://woniumd.oss-cn-hangzhou.aliyuncs.com/java/panguanghua/20220801141840.png)

![image-20220801141856978](https://woniumd.oss-cn-hangzhou.aliyuncs.com/java/panguanghua/20220801141857.png)



###  `__proto__` 与 原型对象关系 

每个对象自身都有一个属性`__proto__`，它指向了构造函数的原型对象（真原型）

每个构造函数的原型对象是唯一的，我们可以在原型上添加一些共享方法

不同函数的原型对象是不一样的

对象上设计`__proto__`属性的目的，就是为了能找到构造函数的原型，这样才能访问原型上的属性和方法

重点总结 ：

- ` __proto__`**对象隐式原型** 和 **构造函数的原型对象**是等价的
- `__proto__`对象原型存在的意义就在于：为对象的查找机制提供一个方向，或者说是一条路线。但是`__proto__`是一个非标准的属性，在实际开发中，不可以使用该属性，它只是内部指向构造函数的原型对象 prototype, 所以建议直接使用函数真正的原型对象。
- ![image-20220608115026061](https://woniumd.oss-cn-hangzhou.aliyuncs.com/java/panguanghua/20220608115026.png)

![image-20220608112221462](https://woniumd.oss-cn-hangzhou.aliyuncs.com/java/panguanghua/20220608112221.png)

###  构造函数、实例、原型关系图

![image-20220801143845436](https://woniumd.oss-cn-hangzhou.aliyuncs.com/java/panguanghua/20220801143845.png)

### 原型对象应用案例



所有对象的原型（prototype）本质是      下划线下划线proto下划线下划线，这个属性它指向的是创建这个对象的构造函数原型



出现意义：在通过对象查找属性或方法时，可以沿着原型对象来查找

查找的过程: 对象.方法

​	1、先从该对象中寻找是否有这个方法

 			有:直接使用

​				没有：会继续通过proto_</u>找到原型来从原型中继续查找

​						

​					原型对象没有：



可以将所有对象共享的方法或属性绑定到改构造函数的原型上



原型本质也是对象<font color='red'>xx.prototype</font>.想要添加的函数



```javascript


```



![image-20220910125614013](C:\Users\TOM\AppData\Roaming\Typora\typora-user-images\image-20220910125614013.png)





## 原型链查找

![image-20220910125227294](C:\Users\TOM\AppData\Roaming\Typora\typora-user-images\image-20220910125227294.png)

![image-20220910125353871](C:\Users\TOM\AppData\Roaming\Typora\typora-user-images\image-20220910125353871.png)

隐式原型是供原型对象查找属性的一般查看就用原型对象查看不用隐式原型



### 函数的构造函数

Function

```javascript

new Function xx(){}
```

![image-20220910142958217](C:\Users\TOM\AppData\Roaming\Typora\typora-user-images\image-20220910142958217.png)



![image-20220910143435543](C:\Users\TOM\AppData\Roaming\Typora\typora-user-images\image-20220910143435543.png)

## 函数的调用

### call（）

### bind（）

声明式的函数不能直接使用bind

```javascript

$.ajax({
urel:xx,
success(res){
}.bind(xxx)
})

不行，会报错

要这样写，就可以
$.ajax({
urel:xx,
success：function(res){
    console.log(this)
}.bind(xxx)
})
```



### 改变this的指向

箭头函数：箭头函数中没有this，使用时指向当前作用域的父级作用域中的this



call（）、apply（）：改变this指向后就立即调用该函数，call可以直接传递参数，ally需要将参数放在一个数组中来使用



bind（）：改变this后会返回一个新的函数，bind（）经常会使用在回调函数中来改变this





## 遍历



for in 一般遍历对象

```js
for (let i in u1){
    console.log(i,u1[i])
}
```



## 对象小方法

### 删除对象的属性

**语法：delete 对象.属性名**



### 如果需要使用特殊的属性名，不能采用.的方式

需要用另一种方式：

**语法：对象["属性名"] = 属性值**

**读取时也要采用这种方式**

## 字符串扩展

字符串类型，会有内存优化，在创建的时候会看字符串常量池中是否存在这个字符串



字符串常量池是在堆中

```javascript
let s1 = 'hello'
let s2 = 'hello'

let s3 =  new String('hello')
let s4 = new String('hello')


log( s1 == s2)//true

log( s1 == s3)//特殊:经过转换后直接比较字符串的内容

log( s3 == s4)//false
```

**<font color='red'>以后在开发中，字符串的比较建议使用 = = =</font>**

 

# ES6的面向对象

ES6的面向对象语法就是在ES5面向对象语法的基础上，进行了二次优化设计，把一些复杂的代码进行了简化，首次提出了类的概念，优化了原型对象的使用。

因此ES6的面向对象语法经常被称作 ： 语法糖



- 属性 ：事物的特征， 在对象中使用属性名来表示（名词）
- 方法 ：事物的行为，在对象中使用方法来表示（动词）

## 类（class）

**<font color='red'>ES6类的本质就是ES5的构造函数</font>**

类 ： 我们可以理解为种类，分类 【物以类聚，人以群分】

类概念 ： 把具有相似属性和相似行为的一些对象放在一起，就可以形成一个抽象的概念【类】（真实是不存在的）

小类可以组成更大的类

电商的分类最复杂：最少三级分类

**<font color='red'>类这个概念本质就是ES5面向对象的一种语法糖</font>**

**<font color='red'>当在类中没有写构造函数constructor时，JS在运行时会自动提供一个构造函数</font>**

```javascript
let 类名(大驼峰命名) {
    
}


创建商品类
class Product{
    
}

创建用户类
class User{
    
}
类是创建对象的模板,语法: let 变量 = new 类名（）

let p1 = new Product();
let u1 = new User();

应用方法
ES6语法糖
class USer{
    //类的构造器
    constructor(id,name,xx){
        this.id = id
        this.name = name
        this.xx = xx
	}
}
```

### 类的解释疑问

类的本质是<font color='red'>ES5的构造函数</font>



类的原型对象跟构造函数一样

## 类的方法定义

一般在原型上添加通用方法



### ES6可以直接在类中定义方法（会直接绑定到这个类的原型上）

```javascript

class USer{
     constructor(name) {
         this.name = name
        }
    info(){
        会直接绑定到这个类的原型上
    }
    
}
```

## static 关键字

###  概念

static  :  静态的意思（主要用来给类添加属性和方法的一种方式）

static 用途 ：在ES6中可以使用在类中用来修饰变量和方法的一种修饰符

- 静态变量（类属性）
- 静态方法（类方法）
- 静态成员的访问：类名.属性  /  类名.方法()
- static可以给类定义属性和方法，在访问时<font color='red'>无需创建对象</font>，直接使用类名访问即可，在一定程度上简化了部分代码。
- 又因为对象都是通过同一个class模板创建的，所以这些实例对象都是共享类成员的

```javascript

class USer{
     constructor(name) {
         this.name = name
        }
    info(){
        会直接绑定到这个类的原型上
    }
    
    static chech(mobile){
        return xxxxx
    }
}
使用的时候直接USer.chech(xx)

```

## 继承(extends)

 子类可以继承父类的一些属性和方法。

继承是用来做架构设计的基础

继承必须满足单项is-a的关系狗是一种动物，动物不是狗

有了继承后可以设计出通用的分类。以后在创建子类的时候都可以完成继承（继承父类的属性）

同时子类还可以自己做扩展......



在子类写与父类同样的方法的时候，子类会覆盖父类的方法



```javascript
class Person{
     constructor(name，id,xx) {
         this.name = name
         this.id = id
         this.xx = xx
        }
}



class Teacher（子类） extends Person(父类){
   就可以获得父类的属性继承给子类
    再写一个 constructor() {}就会报错
    当在创建子类对象时，首先会调用父类的构造函数来完成继承(属性，方法)
	然后再初始化子类的特有的属性和方法
}
let t1 = new Teacher()
```

### super（）

**<font color='red'>在继承的时候子类不能加上空的constructor</font>**

可以不写，系统会自动填充



 当在创建子类对象时，首先会调用父类的构造函数来完成继承(属性，方法)
	然后再初始化子类的特有的属性和方法

需要加上的话需要在里面写super（）

super（）需要在里面的第一行，写完后就能再下面写自己的东西

```javascript
class Person{
     constructor(name，id,yy) {
         this.name = name
         this.id = id
         this.yy = yy
        }
}



class Teacher（子类） extends Person(父类){
 constructor(name,id,yy,xx) {前面是继承的需要的属性
     super(name,id,yy父类的几个属性)
     this.xx = xx
 }

}
let t1 = new Teacher()

```





## 多态

了解即可

多态的定义 ： 同一个操作作用在不同的对象上会出现不同的效果。

多态： 多种状态

前提是必须需要继承

## 封装



在JavaScript程序中，封装一般指的就是我们使用函数的形式将一段重复使用的代码进行包装。对于其他程序员来说，只需要调用即可，不需要知道内部的实现细节到底是什么。

公司内部会封装各种各样的工具类供我们使用，所以开发会变得更加便捷，高效

- 对于其他开发者来说，直接调用api即可
- 隐藏内部实现的细节，对源码形成保护，更加安全
- 函数和类就是封装最好的体现

  



# 面向对象扩展

## Obj的API

从本质上看，`Object` 是一个JavaScript内置的构造函数，用于创建对象。

任何自定义函数的默认原型就是Object构造函数的原型对象。所以自己创建的对象能够直接通过原型链使用Object定义的api

###  Object API

| Object 通用方法                             | 功能                                               |
| ------------------------------------------- | -------------------------------------------------- |
| Object.create(原型/null)                    | 创建对象，能够手动指定该对象的原型（了解）         |
| **Object.defineProperty(对象，属性，参数)** | 添加或修改指定对象的属性()                         |
| Object.assign(多个对象)                     | 将多个对象进行合并，一般用于对象复制               |
| 对象.toString()                             | 对象的字符串输出                                   |
| Object.freeze(对象)                         | 冻结一个对象。冻结后该对象的属性不可修改           |
| 对象.hasOwnProperty(属性名)                 | 判断某个属性是否是自身属性还是继承属性。返回布尔型 |
| Object.keys(obj)                            | 获取对象中所有的属性名                             |
| Object.values(obj)                          | 获取对象中所有的值                                 |



#### **Object.defineProperty(对象，属性，参数)**

```js
let obj{id:1,name:'admin',pwd:'123'}

Object.defineProperty(obj,"age",{
    value:18 属性的值,
    writable:true ,是否允许修改
    configurable:true,是否允许删除
   enumerable:true，是否可以被枚举出来，可以点出来，但是不能遍历出来，for in
    
});

让id不能被修改
Object.defineProperty(obj,'id',{
    writable:false,
    configurable:false
})
```

#### nObject.assign(合并多个对象)

```js
let o1 = {id:1,name:'admin'}
let o2 = {id:2,name:'xx'}

es6
let obj = {...o1,...o2}会产生一个新对象

api
Object.assign(o1,o2)在o1的基础上加上了o2，o1变了，o2没变

```

#### 对象.toString()

```js
let num = 10
let num2 = new Number(10)
let num3 = new Number(10)
num == num2 //true，因为双等的时候应用数据类型会转换为数组
num2 == num3 //false,两个引用的时候会比较地址
num+""
num.toString()


```

#### 对象.hasOwnProperty(属性名)判断是否存在这个属性

```js
let user = {username:'admin'}
user.hasOwnProperty('username') //true

或者("username" in user)

当给Object的原型对象添加一个属性

使用hasOwnProperty只会看对象自身查找

使用in的时候会查看原型链去查找
```



#### 重点Object.keys(obj)，Object.values(obj)

获取对象中所有的属性名

```js
let stu ={id；1，name:'张三',age:19}
let keys = Object.key(stu) // ['id','name','age']
let valu =  Object.values(stu)
返回数组
对象的属性名，值
可以遍历了
keys.forEach(item){
    console.log(item,stu[item])
}

for in还是会把原型链上的东西找到
for( i in stu){
    console.log(i,stu[i])
}
```

**<font color='red'>in还是会把原型链上的东西找到</font>**

  ## 1. 浅拷贝与深拷贝

深拷贝和浅拷贝主要针对的**引用数据类型**！

无论是浅拷贝或深拷贝，都是在做同一件事情：拷贝对象（对象复制）

###  深拷贝

```javascript
let o1 = {id:1, name:"admin",age: 18};
// 传统遍历拷贝
let o2 = {};
for(let field in o1){
    o2[field] = o1[field];
}
// 扩展运算符
let o3 = {...o1};只能深拷贝第一层，嵌套的话就不行

// JSON拷贝
let o4 = JSON.parse(JSON.stringify(o1));
	
```

###  递归拷贝

仅限于对象拷贝

```javascript
function deepClone(obj){
    let newObj = {}
    Object.keys(obj).forEach(key=>{
        let val = obj[key]
        if(val instance Object){
           	newObj[key] = deepClone(val)
           }else{
                newObj[key] = val
           }
    })
    return newObj
}
```







### 深拷贝问题

当对象中的某个属性的值也是一个对象时，拷贝该属性时只是把对象的地址给拷贝过去了，所以拷贝的该属性无论是新对象还是旧对象，针对该属性，都是指的同一个属性值(对象)，可能深拷贝不彻底（即深拷贝中还有可能出现浅拷贝）


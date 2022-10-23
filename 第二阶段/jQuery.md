# jQuery

## 概述：所以简化的方法都被函数封装，只要传参

一切皆函数（所有方法）

一切皆数组（DOM查找与处理）

## 入门语法

- `$`jQuery的简写

### 入口函数

- 在页面加载执行完成后，自动调用的函数(可多次调用)



````js
window.onload = function(){
    xxxxx
}
这是原生的在页面加载完成后完成函数，只能写一次。后面出现会把前面替换，缺点很大
///////////////////////////////////////////////////////////////////////////////////
$(function (){
    xxxxxx
})
这是jq里的页面加载完成后执行函数，能多次书写，很方便
````





### css样式控制

```js
相当于在里面加style
jquery元素.css("属性名","属性值")


使用对象可添加多个
jquery元素.css( {"属性名","属性值"} )



```



### JS对象与jQuery对象间的转换

#### JS对象转jQuery对象

```js
var 变量 = $("选择器")

$('#box2')
等于
$(document.getElementById("box2"))   //数组

原生写法
function $$(domStr ){
    var dom = document.querySelectorAll( domStr)
    dom.forEach(item=>{
        item.style.bacjfround="blue"
    })
    $$( ul > li )
}
```





#### jQuery对象转为JS对象

```js
var 变量 = $("选择器").get(下标)


$('#box2').get(0)   //box2 标签对象

```





## jQuery常用选择器

| 语法              | 案例 | 基本选择器       | 解释                        |
| ----------------- | ---- | ---------------- | --------------------------- |
| $('元素名称')     |      | 元素选择器 :基本 | 选择指定名称的元素          |
| $('#id属性值')    |      | id选择器         | 选择有指定id属性值的元素    |
| $('.class属性值') |      | class选择器      | 选择有指定class属性值的元素 |
|                   |      |                  |                             |







| 语法                                     | 案例                                              | 选择器           | 解释                                             |
| ---------------------------------------- | ------------------------------------------------- | ---------------- | ------------------------------------------------ |
| $('*')                                   |                                                   | 所有元素选择器   | 选择页面的所有元素                               |
| $(选择器1,选择器2,...)                   |                                                   | 并集选择器       | 选择指定选择器结果的并集                         |
| $('选择器1>选择器2')                     |                                                   | 层级选择器       | 层级选择器                                       |
| $('选择器1 选择器2')                     |                                                   | 后代选择器       | 选择选择器1下的符合选择器2的所有元素(子子孙孙)   |
| $('[属性名称]')                          | 自定义属性也能找到                                | 属性选择器       | 选择拥有指定属性的元素。                         |
| $('[属性名称="属性值"]')                 |                                                   | 属性值选择器     | 选择拥有指定属性和属性值的元素。                 |
| $('选择器:first')                        |                                                   | 首元素选择器     | 选择指定选择器结果中的第一个元素。               |
| $('选择器:last')                         |                                                   | 尾元素选择器     | 选择指定选择器结果中的最后一个元素。             |
| $('选择器1:not(选择器2)')                |                                                   | 非元素选择器     | 选择选择器1结果中除了选择器2结果以外的其它元素。 |
| $('选择器:even')                         | 下标0开始0,2,4.1,3,5                              | 偶数索引选择器   | 选择指定选择器结果中，索引为偶数的元素。         |
| $('选择器:odd')                          | 相反                                              | 奇数索引选择器   | 选择指定选择器结果中，索引为奇数的元素。         |
| $('选择器:eq(索引值)')                   |                                                   | 等于索引选择器   | 选择指定选择器结果中索引值等于指定值的元素。     |
| $('选择器:gt(索引值)')                   |                                                   | 大于索引选择器   | 选择指定选择器结果中索引值大于指定值的元素。     |
| $('选择器:lt(索引值)')                   |                                                   | 小于索引选择器   | 选择指定选择器结果中索引值小于指定索引值的元素。 |
| $('选择器:header')                       | h1-h6                                             | 标题选择器       | 选择指定选择器结果中所有标题元素。               |
|                                          |                                                   | 表单相关         |                                                  |
| $('选择器:enabled')                      | 选可用的                                          | 可用元素选择器   | 选择指定选择器结果中的可用元素。                 |
| $(选择器:disabled)                       | 选不可用的                                        | 不可用元素选择器 | 选择指定选择器结果中的不可用元素                 |
| $('选择器:checked');$('选择器:selected') | $("form select:selected"),$("form input:checked") | 选中选择器       | 选择指定选择器结果中被选中的元素。               |

##  DOM

### 内容操作

| 表单元素                          | 案例                                       | 解释 |
| --------------------------------- | ------------------------------------------ | ---- |
| jQuery元素对象.val('值')          | $("input [name=username].value( )")        | 赋值 |
| var 变量名称=jQuery元素对象.val() | var suername=$("[name=username].value( )") | 取值 |

````js
var suername=$(" input [name=username].value('xxx' )")当里面有形参就相当于赋值,当单选/多选按钮的时候就不能获取值

$("[name=username].value( )")

当单选/多选按钮的时候

````







| HTML内容                           | 案例 | 解释 |
| ---------------------------------- | ---- | ---- |
| jQuery元素对象.html('值')          |      | 赋值 |
| var 变量名称=jQuery元素对象.html() |      | 取值 |
|                                    |      |      |

**同样当里面输入值的时候就变成那个值**



| Text内容                           | 案例 | 解释 |
| ---------------------------------- | ---- | ---- |
| jQuery元素对象.text('值')          |      | 赋值 |
| var 变量名称=jQuery元素对象.text() |      | 取值 |
|                                    |      |      |

**同样当里面输入值的时候就变成那个值**



### 属性操作

| 自带属性                                     | 案例 | 解释 |
| -------------------------------------------- | ---- | ---- |
| jQuery元素对象.prop('属性名称','属性值')     |      | 赋值 |
| var 变量名称=jQuery元素对象.prop('属性名称') |      | 取值 |

**设置class、id等，不可以设置别的非系统自带的属性**





| 自定义属性                                   | 案例 | 解释 |
| -------------------------------------------- | ---- | ---- |
| jQuery元素对象.attr('属性名称','属性值')     |      | 赋值 |
| var 变量名称=jQuery元素对象.attr('属性名称') |      | 取值 |

- prop()与attr()区别

  **attr方法随便定义，但是只能获取disabled（不可选）的值，但是prop能获得true**

  

  **操作表单prop好用 ** 表单操作（checked,selected,disabled）



| 控制class属性       | 案例 | 解释                              |
| ------------------- | ---- | --------------------------------- |
| addClass('值')      |      | 追加一个class属性。(不会删原来的) |
| removeClass(['值']) |      | 移除所有class值或指定值。         |





### 元素操作

| 更新                           | 案例                                   | 解释                                       |
| ------------------------------ | -------------------------------------- | ------------------------------------------ |
| jQuery元素对象.append('内容')  | 在标签里**内容**后加点东西（支持hmtl） | 追加内容 在当前元素内容后面添加指定内容。  |
| jQuery元素对象.prepend('内容') | 同上                                   | 前置内容  在当前元素内容前面添加指定内容。 |
| jQuery元素对象.。()            | 标签在，内容无                         | 清空内容 清空当前元素内容。                |
| jQuery元素对象.before('内容')  | 在标签外的上面加点东西,支持HTML        | 前元素 在当前元素前面添加指定内容。        |
| jQuery元素对象.after('内容')   | 同上                                   | 后元素  在当前元素后面添加指定内容         |
| jQuery元素对象.remove()        | 删自己                                 | 移除元素 移除当前元素                      |









| 获取                              | 案例                             | 解释                                                  |
| --------------------------------- | -------------------------------- | ----------------------------------------------------- |
| jQuery元素对象.children()         | 包括br                           | 子元素  获取当前元素的所有直接子元素。                |
| jQuery元素对象.find('选择器')     |                                  | 后代元素 根据选择器获取当前元素的所有后代元素。       |
| jQuery元素对象.prev()             |                                  | 兄弟元素 获取当前元素的上一个兄弟元素。               |
| jQuery元素对象.next()             |                                  | 兄弟元素 获取当前元素的后一个兄弟元素。               |
| jQuery元素对象.parent()           |                                  | 父元素 获取当前元素的直接父元素。                     |
| jQuery元素对象.parents('选择器')  | 空就是所有父集，里面传参可以固定 | 祖先元素 获取当前元素的符合指定选择器结果的祖先元素。 |
| jQuery元素对象.siblings('选择器') | 回调用得多                       | 获取除了自己以外的所有兄弟元素                        |



##  jQuery遍历

方式一  $数组.each（function ( index (下标)  ,ele（元素）){}）

```js
例如
$("ul > li").each(function(index,ele){ 
//index是下标，ele是标签对象
} )
一般使用在每个元素需要不一样的东西

//颜色一致
  $(".nav li)" .css ("background" , "pink")
    
    //每个颜色都是不一样的
    var colorList =['red',"blue","green","pink","gray","yellow","silver"]
  
  $(".nav li").each(function(index,ele){
      	let randNum = parseInt(Math.radom()*(colorList.length))// （0-1} -> (0,7]
        consle.log ( index,ele,radNum)
      
      $(ele).css( {backgroundColor:colorList [ randNum] } )
      $(ele).prepend(index+1+"," )
        
  } )
```





方式二  $ .each($数组，function(index,ele){})

```js
 $ .each($数组，function(index,ele){
    	     
    })


$.each($("ul > li"),function (index,ele) {
	let randNum = parseInt(Math.radom()*(colorList.length))// （0-1} -> (0,7]
        consle.log ( index,ele,radNum)
      
      $(ele).css( {backgroundColor:colorList [ randNum] } )
      $(ele).prepend(index+1+"," )
} )
```



##  jQuery动画

**常用定时器在广告**

### 基本

三个参数:

- \- s 动画速度 (slow|normal|fast|\d)  毫秒

- \- e 切换图片的方式 swing 先快后慢, linear 匀速

- \- f 动画完成 后返回的函数

### 显示与隐藏

#### （宽、高、透明度）

- `$ele.show(s,e,f)`
  - 显示隐藏(display : none)的元素。

````js
 $('#btn1').click(function () {
        $("#box").show('1000','linear',function () {
            alert('动画完成')
        })
    })
````



- `hide(s,e,f)`

  - 隐藏显示(display:block)的元素。

  ```js
     $('#btn1').click(function () {
          $("#box").hide('1000','linear')
    })
  ```
  
  





- `toggle(s,e,f)`
  
- 根据元素当前状态实现显示和隐藏动画。
  
  - 如果当前元素是显示状态，则表现隐藏动画，如果当前元素为隐藏状态，则表现显示动画。
  
    判断display的状态

```js
 $('#btn1').click(function () {
        $("#box").toggle('1000','linear')
    })

```





### 滑入与滑出

**变化的是高度，超出隐藏**

控制的是高度超出隐藏

- `slideDown(s,e,f)`
  - 滑入隐藏元素(显示)。



```js
$('#btn1').click(function () {
        $("#box").slideDown('1000','linear')
    })
```



`slideUp(s,e,f)`

- 显示元素滑出(隐藏)。

```js
 $('#btn1').click(function () {
        $("#box").slideUp('1000','linear')
    })
```



- `slideToggle(s,e,f)`

  - 根据元素当前状态实现滑入和滑出动画。
  - 如果当前元素是显示状态，则表现滑出动画，如果当前元素为隐藏状态，则表现滑入动画。

  ````js
   $('#btn1').click(function () {
          $("#box").slideToggle('1000','linear')
    })
  ````
  
  

### 淡入淡出

**控制的是透明度（opacity）**

- `fadeIn(s,e,f)`

  - 淡入隐藏元素

  ```js
   $('#btn1').click(function () {
          $("#box").fadeIn('1000','linear')
    })
  
  ```
  
  



`fadeOut(s,e,f)`

- 淡出隐藏元素。



```js
 $('#btn1').click(function () {
        $("#box").fadeOut('1000','linear')
    })

```





- `fadeToggle(s,e,f)`
  - 根据元素当前状态实现淡入和淡出动画。
  - 如果当前元素是显示状态，则表现淡出动画，如果当前元素为隐藏状态，则表现淡入动画。

```js
 $('#btn1').click(function () {
        $("#box").fadeToggle('1000','linear')
    })

```



### 自定义

- `animate(param,s,e,f)`
- 自定义动画。
  - param参数：最终要显示的样式style

```js
$("ele").animate({
    基本只能监听到数值的变化
},"slow","liner",fuction(){
    //code
    $(this).hide();//this是ele的
 })
```

### 侧边栏隐藏练习

```js
 <style>
        .media-left {
            height: 100vh;
        }
        .media-left >ul {
            width: 200px;
            background-color: silver;
            height: 100vh;
        }

    </style>
</head>
<body>
    <div class="container-fluid">
        <div class="row media">
            <dd class="media-left" >
                <ul id="navArea">
                    <li><a href="">link1</a></li>
                    <li><a href="">link2</a></li>
                    <li><a href="">link3</a></li>
                    <li><a href="">link4</a></li>
                    <li><a href="">link5</a></li>
                    <li><a href="">link6</a></li>
                    <li><a href="">link7</a></li>
                    <li><a href="">link8</a></li>
                    <li><a href="">link9</a></li>
                    <li><a href="">link10</a></li>
                </ul>
            </dd>
            <dd class="media-body">
                    <h4 class="border-bottom padding">
                        <span class="glyphicon glyphicon-triangle-left" id="tabArea"></span>
                    </h4>
            </dd>
        </div>
    </div>
</body>
</html>
<script>
    $("#tabArea").click(function () {
        var flag = $("#navArea").css("display")


        if (flag != 'none'){

            $("#navArea").animate({
                width: "0px",
                opacity:0,
                overflow:"hidden"
            },1000,"linear",function () {
                $(this).hide();
                $('#tabArea').attr("class",'glyphicon glyphicon-play');

            })
        }else{

            $("#navArea").show().animate({
                width: "200px",
                opacity:1,
                overflow:"hidden"
            },1000,"linear",function () {
                $('#tabArea').attr("class","glyphicon glyphicon-triangle-left");
            })
        }


        //优化
        // var onOff = flag == 'block'
        // $("#navArea").show().animate({
        //     width:onOff? "200px" : 0,
        //     opacity:0 ? 0 : 1,
        //     overflow:"hidden"
        // },100,"linear",function () {
        //     onOff ? $(this).hide() : $(this).show();
        // })

    })

</script>
```





##  jQuery事件

### 绑定

第一种方法

- `on(events,fn)`

  - 给当前元素绑定指定事件和监听器函数。

    ```js
    能放多个事件
    $("button").on('click mouseover',function(){
        
    })
    ```

第二种方法

`selse,事件名(回调函数)`

````js
不能加on
$ele.事件名(回调函数)
$("button").click(function(){
    xxxx，
})

````





### 解绑

- `off(events)`

  - 给当前元素解除绑定指定事件。

    ```js
    $("button").off(click)
    
    $("button").off(colic,mouseover)
    绑定多个事件，可以只解绑一个
    ```

### 练习

```js
<div class="container">
    <dl class="bg-black">
        <dd>
            <!--小图片列表-->
            <ul id="smpicArea" class="flex">
                <li></li>
                <li></li>
                <li></li>
                <li></li>
                <li></li>
            </ul>
        </dd>
        <dd>
            <!--大图列表-->
            <ul id="bigpicArea" >
                <li></li>
                <li></li>
                <li></li>
                <li></li>
                <li></li>
            </ul>
        </dd>
        <dd>
            <button id="btn" onclick="fn()">事件</button>
        </dd>
    </dl>
</div>


</body>
</html>
<script>

    $("#btn").get(0).onclick=null
    function fn() {
        alert("hello")
    }
    var smList=[
        "https://scpic2.chinaz.net/Files/pic/pic9/202206/apic41571_s.jpg",
        "https://scpic2.chinaz.net/Files/pic/pic9/202206/apic41572_s.jpg",
        "https://scpic2.chinaz.net/Files/pic/pic9/202206/apic41573_s.jpg",
        "https://scpic2.chinaz.net/Files/pic/pic9/202206/apic41574_s.jpg",
        "https://scpic2.chinaz.net/Files/pic/pic9/202206/apic41575_s.jpg",
    ],
        bigList=[
            "https://scpic2.chinaz.net/Files/pic/pic9/202206/apic41571.jpg",
            "https://scpic2.chinaz.net/Files/pic/pic9/202206/apic41572.jpg",
            "https://scpic2.chinaz.net/Files/pic/pic9/202206/apic41573.jpg",
            "https://scpic2.chinaz.net/Files/pic/pic9/202206/apic41574.jpg",
            "https://scpic2.chinaz.net/Files/pic/pic9/202206/apic41575.jpg",
        ],
        active=0;  //默认显示大图片下标

    $("#smpicArea li").each(function (index,ele) {
        $(ele).css({
            background:`url(${smList[index]}) no-repeat   100%`,
            width:"20%",
            height:"100px"
        })

        //注册,绑定 事件 方法1
         $(ele).on("click mouseover",function(){
            //code
            console.log(index)
            active=index  //获取点击小图的下标,要激活大图的数据,改变下标
            init()
        })

       //注册,绑定 事件 方法2
        /*$(ele).click(function(){
            //code
            console.log(index)
            active=index  //获取点击小图的下标,要激活大图的数据,改变下标
            init()
        })*/
        //解绑
        $(ele).off("mouseover")
    })

    function init(){
        $("#bigpicArea li").each(function (index,ele) {
            $(ele).css({
                background:`url(${bigList[index]}) no-repeat center`,
                height: "500px",
                display: index==active?"block":"none"
            })
        })
    }
    init()




</script>
```



## jQuery链式调用

### 概念

- jQuery的函数返回的是调用函数的对象，则可利用该特点实现链式调用。

  **主要看返回值，不只是jq，只要返回值还是选中的属性的对象**
  
  ```js
  列如
  let tmp = $("#navArea").show();
  console.log(tmp)返回的还是 //#navArea的对象
  后面还可以写别方法
  ```


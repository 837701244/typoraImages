# 模拟后端服务器

## MockJs（服务器端模拟）

### 2.1什么是mockJs

生成随机数据或者模拟指定的数据，模拟后端的接口数据，拦截 Ajax 请求

参考文档：http://mockjs.com/examples.html

### 2.2 为什么使用mockJs

如果后端接口还未开发完成，我们自己手动模拟后端接口返回随机数据完成交互功能

1. 采用json数据模拟，生成数据比较繁琐，也比较有局限性，没办法达到增删改查
2. 采用mockJs进行模拟数据，可以模拟各种场景（get、post）生成接口，并且随机生成所需数据，还可以对数据进行增删改查

## mock 功能一 拦截请求

- 加载框架

```js

    <script src="../../source/js/mock.js"></script>
    <script src="server/server.js"></script>  //自己随便写的

需要按照顺序加载
```



- 

- 接口拦截

```js
//server/server.js
const baseurl="http://www.woniuxy.com"
Mock.mock(baseurl+"/frendlink/data","get",function () {
    return {
        data:[{
            "linkid": "1",
            "type": "0",
            "rank": "203",
            "sitename": "在线聊天室",
            "url": "http://www.coolneng.com/wap/rabbit/chat",
            "logo": ""
        },{
            "linkid": "2",
            "type": "2",
            "rank": "2213",
            "sitename": "baidu",
            "url": "http://www.baidu.com/",
            "logo": ""
        },{
            "linkid": "23",
            "type": "22",
            "rank": "223",
            "sitename": "360",
            "url": "http://www.360.com/",
            "logo": ""
        }]
    }
})


///////////////////////////////////////////////
或者
const cn=['舒克', '张力', '倪嘉乐', '婷婷', '李悦莱', '徐铜强', '黄文龙', '杨静', '阿狸呀', '汤诚', '孙欣欣', 'lulinjie', '冯青宇', '万润奎', '王淼', '飞洋', '邵凯渤', '杨楠楠', '杨芳芳', '杰影', '石星宇'];
const en=['shuke', 'sena', 'nijiale', 'Tammy', 'lyl', 'xutongqiang', 'huangwenlong', '条条', 'aliya', 'tom', 'sunxinxin', 'alo', 'fqy', 'wrk', 'WM', 'feiyang', 'kaiser', 'yangNanNan', 'masue', 'jieying', 'yoki']
const BASEURL="http://localhost:63342";  //服务器地址,要拦截的URL
const Random=Mock.Random;


//methods
/*
* 数据传递参数时的格式化
* post数据 max=55&auther=shuke&page=2
* 返回数据 {max:55,auther:"shuke",page:2}
* */
function fmtParm(str) {
    var arr=str.split("&")  //字符中截取为数组
    var obj={}              //定义一个空对象
    for(item of arr){
        var subArr=item.split("=")  //[max,55] ["auther","shuke"]
        obj[subArr[0]]=subArr[1]  //obj[max]=55 obj["auther"]="shuke"
    }
    return obj
}


//随机获取会员信息
function getMembers(num=21) {
   return Mock.mock({
       ["data|"+num]:[
           {
               "name|+1":en,
               "nickname|+1":cn,
               "age|18-30":1,
               "pwd":/\w{6}/,
               "pic":/img\/(\d|[1-9]\d|1\d{2})\.jpg/,
               "card":Random.id(),
               "gender|1-2":1,
               "email":Random.email(),
               "state|0-4":1

           }
       ]
   })
}

//数据持久化
function initStorage(){
    if(!localStorage.getItem("members")){
        console.log("用户数据加载完成")
        window.localStorage.setItem("members",JSON.stringify(getMembers().data))
    }
}
initStorage();


Mock.mock(baseurl+"/frendlink/data","get",function () {
    return {
        data:JSON.parse(localStorage.getItem("members")),
        status:ture
    }
}）
          
          /////////////////////
          post方法
 Mock.mock(BASEURL+"/api/getusers","post",function (req) {

    let obj=_fmtParam(req.body)  //{num: '2', numSize: '10'}

    let allArr=JSON.parse(localStorage.getItem("serverUsers"));  //21
    console.log(obj,allArr)

    return _Page(allArr,obj.page*1,obj.pageSize*1)
})
```

- 前端使用

  ```js
  /*<ul id="frendlink">
      <li>
      </li>
  </ul> 
  */
  const URL="http://www.woniuxy.com/frendlink/data"
   $.ajax({
          url:URL,
          type:"GET",
          dataType:"json",
          success:function (res) {
              console.log(res.data)
              let str=res.data.map(item=>`<li><a href="${item.url}">${item.sitename}</a></li>`).join("")
            $("#frendlink").html(str)
          }
      })
  ```

## mock 功能二 随机数据

- 字符串
  - Mock.mock({'key|min-max': value})

- 数字
  - Mock.mock({  "key|+1": number })  累加随机数据
  - Mock.mock({  "key|1-100": 1})  随机范围
- 布尔
  - Mock.mock({  "key|1": true })  
- 对象
  - Mock.mock({  "object|2": {    "310000": "上海市",    "320000": "江苏省",    "330000": "浙江省",    "340000": "安徽省"  } })
- 数组
  - Mock.mock({  "array|2": [    "AMD",    "CMD",    "UMD"  ] })  数组拼接为二次
  - Mock.mock({  "array|+1": [    "AMD",    "CMD",    "UMD"  ] }) 顺序随机
  - Mock.mock({  "array|1-10": [    {      "name|+1": [        "Hello",        "Mock.js",        "!"      ]    }  ] })
  - Mock.mock({  "array|3": [    "Mock.js"  ] })   随机出来数组中的3个数据
- 函数
  - Mock.mock({  'city': **function**() { return Mock.mock('@county(true)') } })  解决数据一致的情况
- 正则
  - `Mock.mock({'tel': /1[356789]\d{9}/ })`

```js
//默认所有Mock模拟出的都是对象 {key:value}
字符串: {string:"★"}
Mock.mock({
  "string|1-10": "★"
})
Mock.mock({
   ["data|"+num]:[
       {
           "name|+1":en,
           "nickname|+1":cn,
           "age|18-30":1,
           "pwd":/\w{6}/,
           "pic":/img\/(\d|[1-9]\d|1\d{2})\.jpg/,
           "card":Random.id(),
           "gender|1-2":1,
           "email":Random.email(),
           "state|0-4":1
       }
   ]
})
```



## 接口数据JSON

JSON 是序列化的对象或数组，它是 JS 对象的字符串表示方法，也就是说，JSON本质上是一个字符串。JSON以键值对 (key, value) 的形式存在。

与JS对象相比，不同点为：

-  js对象是一种数据类型，JSON是一种数据文件。
-  JSON的 key 必须用 "" (双引号)包起来
-  JSON的 value 不可以为 function/undefined/NaN
-  数据结尾不允许出现无意义的 `,`
-  JSON文件里不允许注释。

```js
js object
var obj={name:"shuke",age:undefinded,}
json files
{"name":"shuke","age":33}
```



### JSON 与 JS 对象的转换

- 从 JSON 转为 JS 对象：使用 `JSON.parse()` 方法
- 从 JS 对象转为 JSON：使用 `JSON.stringify()` 方法

# 关于MOCKJS中文转码问题

- 解码

```js
window.decodeURIComponent(中文参数)
```

- 中文编码

```js
window.encodeURIComponent(参数)
```

| 函数 window          | 描述                      |
| -------------------- | ------------------------- |
| decodeURI()          | 解码某个编码的 URI。      |
| decodeURIComponent() | 解码一个编码的 URI 组件。 |
| encodeURI()          | 把字符串编码为 URI。      |
| encodeURIComponent() | 把字符串编码为 URI 组件。 |

- encodeURI()不会对本身属于URI的特殊字符进行编码，例如冒号、正斜杠、问号和井字号；
- encodeURIComponent()则会对它发现的任何非标准字符进行编码。
- decodeURI()编码后的结果是除了空格之外的其他字符都原封不动，只有空格被替换成了%20。
- decodeURIComponent()方法则会使用对应的编码替换所有非字母数字字符。

## 关于mockjs 在服务器端接口问题

- 接口参数 “post”,”get” 一定要小写
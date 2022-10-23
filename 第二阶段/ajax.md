

# AJAX

## 现代前后端交互（前后端分离）

后端造个接口渲染到网页

前端用AJAX方法访问接口，获取数据，处理数据，渲染到页面中

同域直接可以获取数据,跨域不能直接获取数据,必须经过服务器同意



## 什么是 AJAX？

*Ajax*即Asynchronous Javascript And XML（异步JavaScript和XML）

AJAX 并非编程语言。使用Ajax技术网页应用能够快速地将增量更新呈现在用户界面上，而不需要重载（刷新）整个页面，这使得程序能够更快地回应用户的操作.







## jQuery 实现AJAX

### 语法 $.ajax(); 

```js
$.ajax(
	里面输入参数
)

$.ajax({
	url:'', //接口地址
    success:function(result){
        				//接口获取成功后回调函数。result：接口数据
    }
})

```







| ajax对象参数 | 解释                                                         |
| ------------ | ------------------------------------------------------------ |
| async        | 布尔值，表示请求是否异步处理，默认是true                     |
| url          | 服务器接口url  `必填项`                                      |
| data         | url参数 对象                                                 |
| dataType     | 返回的数据解析方式：json,text,html 默认text                  |
| type         | 提交给服务器的方式 get post， 默认get                        |
| contentType  | 发送到服务器的数据的内容类型   默认 "application/x-www-form-urlencoded", |
| success      | 表示当前请求成功，会执行匿名函数，并将实参传入. result 表示返回的接口数据 `必填项` |
| error        | 表示当前请求失败，会执行匿名函数，并将实参传入. err 表示失败返回的接口数据 |
| complete     | 无论成功失败都会执行此处代码，这里表示AJAX执行完毕           |



- URL (统一资源定位符,网址)

  ```js
  URL:  https://woniuxy.com/video?page=3&pagesize=10    http://localhost:63342/
  协议:  http,https
  域名:  www.woniuxy.com
  端口:  80,443
  文件地址:video
  参数:?page=3&pagesize=10 
      ---------------------------------------------------------------------------------------------    
        前提条件 (两个域名)
  同域:  "协议 域名 端口"  都必须一致,就是同域
  同域一定能获取数据跨域:  "协议 域名 端口"  只要一个不同,就是跨域, 跨域要服务器配置白名单才可以访问
  ```

- type
  - GET 表示从浏览器的 URL 传参及获取页面
  - POST 表示 从浏览器 headers中加密传参,及获取页面
- JS 异步与同步 (定时器,AJAX)
  - 同步 代码逐行解释,排队等待
  - 异步 在后面的代码无需等待,直接执行 (定时器,AJAX)
  - 同步优点：提高HTML渲染速度



### readyState 表示后端的处理过程

 2：请求已经接收，send()方法完成;
 3: 处理中
 4：请求处理完成。
 status 状态码
 200 从服务器正常获取
 404 没有找文件
 304 从缓存加载
 500 服务错误



## xhr 实现ajax

### 创建一个 XMLHttpRequest 对象

```js
var xhr=new XMLHttpRequest();
```

### 打开链接： 

客户端 http 与服务器 http 建立连接

```js
xhr.open(type,url,isAsync);
type 请求类型  get post
url  接口地址
isAsync 是否同步 true 异步 false同步
```

###  发送请求

```js
xhr.send();
```

###  处理过程

```js
xhr.onreadystatechange=function(){
    //todo
}
 readyState 表示后端的处理过程
 2：请求已经接收，send()方法完成;
 3: 处理中
 4：请求处理完成。
 status 状态码
  200 从服务器正常获取
  404 没有找文件
  304 从缓存加载
  500 服务错误
//eg
xhr.onreadystatechange=function () {
    console.log("过程",xhr.readyState,xhr.status)  //进度,状态码
    if(xhr.readyState==4 && xhr.status==200){
       // console.log(xhr.responseText)
        //list=JSON.parse(xhr.responseText)
    }
}
```

###    请求成功的监听

```js
xhr.onload=function(){}
```

### 请求失败的监听

```js
xhr.onerror=function(){}
```

### xhr 案例

```js
 var list=null
//创建一个XHR对象
var xhr=new XMLHttpRequest();
//设置请求参数
/*xhr.open(type,url,async)
* */
xhr.open("get","./member.json",true)
//发送请求
xhr.send();
//监听过程
/*
* readyState 表示后端的处理过程
     2：请求已经接收，send()方法完成;
     3: 处理中
     4：请求处理完成。
     status 状态码
      200 从服务器正常获取
      404 没有找文件
      304 从缓存加载
      500 服务错误
      xhr.responseText 接口数据
* */
xhr.onreadystatechange=function () {
    console.log("过程",xhr.readyState,xhr.status)  //进度,状态码
    if(xhr.readyState==4 && xhr.status==200){
       // console.log(xhr.responseText)
        //list=JSON.parse(xhr.responseText)
    }
}
//最终 success
xhr.onload=function () {
    console.log("success",xhr.responseText)
    list=JSON.parse(xhr.responseText)
}
//错误 error
xhr.onerror=function () {
    console.log("err")
}
```


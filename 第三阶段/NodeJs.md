# Node.js

## 概括

Node.js 是一个基于 Chrome V8 引擎的 **JavaScript 运行时（运行环境）**。

优势参考 ： http://nodejs.cn/learn

不支持BOM

**应用场景**：

- **服务端开发** （模拟一些后端的语言搭建服务器 Java PHP）
- **底层平台** (社区在 Node.js 上构建了数千个库，开箱即用)
- **周边生态** （提供了包管理工具 npm , 开发者可以上传自己的程序包，供社区成员使用）

**特点** ： 

- Node.js完全是JS语法，我们只需要学习JS基础就可以学会 Node.js后端开发
- Node.js 有超强的高并发能力，可以实现高性能的服务器
- 开发周期短，开发成本低，学习成本低

##  什么是包

Node.js 中的第三方的模块又称作 ： 包

（这个包本质：其他人已经开发完成项目，传到了网络上，供我们前端开发者使用的模块，我们把这个模块就称作一个包）



###  包的来源

Node.js中的我们有内置模块和自定义模块，包是由**第三方开发出来的**，免费供所有人使用。

Node.js中的所有包都是免费开源的，不需要付费，下载就可以正常使用了

###  包的用途

Node.js 为我们提供了一些内置的模块 api, 导致在使用内置模块开发时，有可能会涉及到一些非常底层的逻辑操作，这样就会显得非常麻烦

包是基于内置模块封装出来的，提供了更高级，更便捷的强大API，极大提高了程序开发的效率

包和内置模块的关系，就类似于 jQuery 和 浏览器内置的API(原生JS)

###  包的下载

（1）从哪里下载包

在国外有一家公司，叫做 npm, Inc.这家公司旗下有一个非常著名的网站： https://www.npmjs.com, 它是全球最大的包共享平台，这个网站可以搜索到你想要的所有包。

另外 npm, Inc公司提供了一个地址 ： https://registry.npmjs.org 服务器，用来对外共享所有的包。我们可以通过服务器来下载自己想要的包。

总结 ：

- 从https://www.npmjs.com 搜索并学习自己需要的包（记住这个网址）
- 从 https://registry.npmjs.org  服务器下载需要的包（不需要我们来管）

（2）如何下载包

npm, Inc 公司提供了一个包管理工具 npm (Node.js Package Manager的缩写)，即Node.js的包管理工具， 它会默认从https://registry.npmjs.org 服务器上去帮我们下载需要的包。

这个npm工具我们在安装Node.js环



## npm

打开终端：npm init -y



下载安装：nmp install 包名 简化:nmp i 包名  -y  -y是全选yes



卸载 ：npm uninstall包名，无简化

## 快速搭建node环境的项目

### 

创建一个项目文件夹

打开终端输入**<font color='red'>npm init -y</font>**



### 

项目名：name

版本号:version

项目的描述：description

项目的启动入口文件:main

脚本文件：scripts

项目查找的关键字：keywords

作者：author

![1.node项目搭建流程](E:\webClass65\code\第三阶段\20220908\老师的\2022.09.08\图解\1.node项目搭建流程.png)





### 通过npm指令在终端上下载安装相关的模块或卸载模块

下载安装：nmp install 包名 简化:nmp i 包名

卸载 ：npm uninstall包名，无简化



dependencies：依赖

里面放依赖的模块的版本



下载的包都存在 node_modules



安装多个包 npm install 包1空格包2

不能删除多个包



安装的时候可以把包的那个对象复制下来description

装到另一个文件的时候可以在终端数目nmp i

可以一次性将package,json中依赖的包全部安装



指定版本安装npm i  包名@版本

## nrm

为了方便切换我们下包的镜像源，我们可以安装一个工具 nrm ，可以使用这个小工具快速切换包的镜像源

```javascript
-- 1. 安装nrm
npm i nrm -g    全局安装（只要安装一次，就可以在计算机的任何位置使用例如）

-- 2.可以查看可以使用的所有的镜像源
nrm ls


-- 3. 切换需要的镜像源
nrm use taobao

```

##  切换npm 下载包地址(切换镜像地址)

将外网的下载镜像源地址改为国内淘宝的镜像源地址，极大的提高的npm下载包的速度

- 下载淘宝镜像

  ```javascript
  npm install -g cnpm --registry=https://registry.npmmirror.com
  ```

- 切换到淘宝地址(一次切换，永久使用)

  ```
  npm config set registry https://registry.npm.taobao.org
  ```

  - 命令成功没有输出

- 测试镜像是否修改成功

  ```
  npm config get registry
  ```

![image-20220104141240577](https://woniumd.oss-cn-hangzhou.aliyuncs.com/java/cuijin/20220104141242.png)

```javascript
cnpm install 包名
npm install 包名
```



##  npm 全局安装和局部安装

- 项目在使用某个包的时候会优先使用局部安装的包(即当前项目 package.json里面下载的包)，如果项目中没有该包，那么就会去全局下载包中看是否有对应包。

- 全局安装

  - 是指将包下载到 npm安装目录中，这样每个项目可以直接使用。

  ```
  npm  i 包名称  -g
  ```

  - -g:global，指全局安装。下载的包会直接下载到npm的安装目录下

- 局部安装(默认)

  - 跟着某个package.json走。下载 的包直接发放在当前目录下的`node_modules`文件夹下





## npm 开发依赖和生产依赖

- 概念：npm将下载的包分为两类：开发依赖和生产依赖所需的包

- 开发依赖：是指`package.json`中`devDependecies`里指定的包，这里的包主要是为了加快开发效率，实际项目启动是不需要的，到时候我们会项目完成后会忽略开发依赖的包。比如`babel`、`webpack`等

- 生产依赖：是指项目启动必须要用的包，会在`package.json`中`dependecies`里指定。也就是说生产依赖的包，项目整个过程都在，哪怕项目上线了也在。比如jQuery、vue等

- 利用npm来指定下载的包是开发依赖或生产依赖

  ```
  npm i 包名称 -D
  ```

  - `-D或--save-dev`:指的是下载的包为开发依赖
  - `默认或-S或--save`：指的是下载的包为生产依赖



```javascript
全局安装：npi 包名-g   
安装工具的：(nrm切换镜像,webpack项目打包)只要安装一次在任何位置任何项目都可以使用这个工具命令


局部安装 npm i 包名 这个包只能为当前的项目来服务，如果换了一个项目就需要重新来下载包
	开发依赖：在开发过程中使用的包，在项目运行时，这个包就没有用了webpack
    生产依赖：在开发和生产运行环境中都需要使用的包md5 moment expressI
    
   生产依赖 npm i 包名 --save  -->   npm i 包名—S  --> npm i 包名
	开发依赖 npm i 包名 --save-dev  -->  npm i 包名-D

依赖会放在devDependencies是，打包后这个包就不在了


```



## 模块化

Node.js环境下的CommonJs规范下的

### 在html中在外部映引入的js文件的type为Model

```javascript
<script>src="js/a.js" type="module" </script>
```

**<font color='red'>模块的作用域就是当前的这个js内部</font>**

一个js文件就可以看成一个独立的模块，各个模块的数据时互不影响的

```javascript
 在编程过程中的模块化，本质就是遵守一个固定的规则，把一个大的文件拆分成一个个独立且互相依赖的小模块

为什么要拆分这个模块：

- 提高了代码的复用性
- 提高了代码后期的可维护性
- 可以根据自己的需要完成对应模块的加载
```



**<font color='red'>在服务器中</font>**只会加载一次，第二次就会在缓存中获取



需要。创建模块给外界来暴露数据



需要。模块又如何使用另一个模块的数据

Node.js中模块化语法遵循CommonJS规范

### 加载 / 接收模块

require：加载模块执行内部的js代码，接收这个模块中model.emports,默认是{ }

在需要的js文件中

require("模块名")

```javascript
require("模块名")返回的是暴露的对象
所以需要接收
```



### 模块暴露数据

在Node.js中的每一个模块中都有一个内置对象module



module中有个属性emports，它是个对象

暴露的数据就要放在module.exports内部

```javascript
正常的
是需要在module.exports.属性值=需要暴露的值

这样写也可以model.exports = 对象（基本类型的值或对象，函数，类，）

```



在nodejs的每一个模块中，都有一个

### 一些使用

因为暴露模块是对象，所以在接收的时候可以解构对象

```js
 在 b .js 中
 class xxxx{
	add(){
        console.log( 111)
    }
     delet(){
        console.log( 222)
    }
     update(){
        console.log( 333)
    }
     find(){
        console.log( 444)
    }
 }

module.exports = xxxx



在index.js  中

let aaa = require('./js/b.js')
let model = new aaa()
model.add().....
```

## 内置模块

### 异步读取文件（fs）

nodejs提供了内置的fs模块（file style）





读取文件读到的数据默认是Buffer类型(字节类型 10101011)

所以要转换，用toString（）方法就可以正常读取

PDF以及word都是可插入图片的，所以都不能用这个







异步执行

```js
1、加载内置模块
const fs = require('fs');

2.异步读取文件内容
console.log(fs.readFile )//返回的是一个函数

fs.readFile("地址",function(err,data){
    if（err）{//如果没错误应该是null
        console.log('文件读取失败${err.message}')
        return
    }
    console.log(data.toString())//单独的data是0101的机器码,又因为data是对象又原型链可以使用方法
   )
//假设读取的是一个纯文本数据,
   
   fs.readFile("地址" , UTF-8,function(err,data){
    if（err）{//如果没错误应该是null
       return  console.log('文件读取失败${err.message}')
        
    }
    console.log(data.toString())//单独的data是0101的机器码,又因为data是对象又原型链可以使用方法
   )

```

使用Promise封装

```js
文件名：fileUtil.js
const fs = require('fs');

function readTextFile(path){
    return new Promis((resolve,reject)=>{
         fs.readFile("地址" , UTF-8,function(err,data){
    	if（err）{
            reject('文件读取失败${err.message}')
  	  }
             resolve(data.toString() )
   
   		)
    })
     
}
                      
module.exports = {
                      readTextFile
 }



/////别的文件使用
const req =   require("./util/fileUtil.js")//
解构
const {readTextFile} =   require("./util/fileUtil.js")

readTextFile(需要读取的文件地址).then(item=>{
    console.log(data);
})

```

### 同步读取文件（fs）

```js
const fs = require('fs')
console.log(fs.readFileSync())
fs.readFileSync(“地址”,"编码")编码可省略
```

### 读文件总结

因为是异步所以要回调函数才能获取

```javascript
const fs = require('fs')

fs.readFileSync(“地址”,"编码")

fs.readFile("地址","编码",回调函数)
```



### 写数据会(异步)

**<font color='red'>覆盖上一次的结果</font>**

```javascript

const fs = require("fs")

fs.writeFile("文件路径","数据",回调函数)

如果没这个文件会创建文件
不会自动新建文件夹




写工具
fs.writeFile("./data/b.txt","xxxx"，function(err){
    if(err){
        return console.log({status:0,msg:'写入失败${err.message}'})
    }
    console.log({status:1,msg:'写入成功'}
})
    
    
    
  封装
  function writeFile(filePath,data){
      return new Promise((resolve,reject)=>{
			 fs.writeFile(filePath,data，function(err){
    if(err){
                return reject({status:0,msg:'写入失败${err.message}')
        //因为不调用的时候还是同步的，所以要return
    }
   resolve({status:1,msg:'写入成功'})
})
      })
     
  }
  module.exports = {
		writeFile
  }


使用
const util = require('./util/fileUtil').js模块的后缀名可以省略不写

util.writeFile("./data/b.txt","xxxx").then(item=>{
    consolt.log(msg)
}).catch(err=>{
    console.log(err)
})

使用async的时候不能接收错误信息所以要使用这两个

(async function(){
    try{
        let msg = await util.writeFile("./data/b.txt","xxxx")
    }catch(e){
        console.log(e)//这里的e就是reject中的内容
    }
})

```



### 写数据(同步)

会覆盖写

```javascript
const fs = require("fs")

let a = fs.writefileSync("路径","数据")
console.log(a);


try{
    fs.writefileSync("路径","数据")
    console.log("文件写入成功")
}catch(e){
    console.log(e.message)
}
```



**<font color='red'>追加写</font>**

write换成append

```javascript
let a = fs.appendfileSync("路径","数据")
console.log()
console.log()

```



### 文件复制

```javascript

const fs = require("fs");
//1.读取源文件数据
//2.将数据写入到目标文件中

let source = "源文件的路径"
let target = '目标文件'

就是读完后写
异步
fs.readFile(source,function(err,data){
    if(err){
        return console.log({status:0,msg:"源文件不存在"})
    }
    fs.writeFile(target,data,function(e){
        if(e){
             return console.log({status:0,msg:"文件复制失败"})
        }
        console.log({status:0,msg:"文件复制成功"}）
    })
})


封装
function copy(source,target){
    return new Promise((resolve,reject)=>{
        fs.readFile(source,function(err,data){
    if(err){
        return reject({status:0,msg:"源文件不存在"})
    }
    fs.writeFile(target,data,function(e){
        if(e){
             return reject({status:0,msg:"文件复制失败"})
        }
        resolve({status:0,msg:"文件复制成功"}）
    })
})
    })
}

 module.exports = {
		copy
  }


---------------------------使用------------------------------


```



### 向CSV写数据

#### CSV是一个类似于Excel表格的格式

```javascript
id,name,age回车
1，admin，18
2，Jack，19
```



专门用于数据分析

![image-20220910221319616](C:\Users\TOM\AppData\Roaming\Typora\typora-user-images\image-20220910221319616.png)





```javascript
const fs = require('fs')

let users = [
    		{id:1,name:'admin1',age:18},
            {id:2,name:'admin2',age:28},
    		{id:3,name:'admin3',age:38}
            ]
let csv = Object.keys(user[0]).join(',')+'\n'

//要换行不行
users.forEach(item=>{
   csv += Object.values(item).join(',')
})

users.map(item=> Object.values(item).join(',')).join("\n")
fs.writeFile("E:/company.csv",)


fs.writeFile("E:/student.csv",csv,function(){
	

})
```



使用第三方模块来读写

```javascript
json2csv

npm i json2csv


const { Parser } = require('json2csv');//加载第三方模块

const fields = ['field1', 'field2', 'field3'];//csv的标题
const opts = { fields };

try {
  const parser = new Parser(opts);
  const csv = parser.parse(myData);
    写到一个csv格式的文件中
    fs.writeFile("xxx",csv,function(err){
        if(err){
            return console.log({status:0,msg:''})
        }
    })
  console.log(csv);
} catch (err) {
  console.error(err);
}
```

封装第三方模块

```javascript
function writeCSV(filePath,data) {
    return new Promise((resolve, reject) => {
        const  fields = Object.keys(data[0])
        const opts = { fields };
        try {
            const parser = new Parser(opts);
            const csv = parser.parse(data);
            // 写到一个csv格式的文件中
            fs.writeFile(filePath,csv,function(err){
                if(err){
                    return reject({status:0,msg:'失败'})
                }
            })
            resolve({status:1,msg:"成功",data:csv});
        } catch (err) {
            reject(err);
        }
    })
}

```



### 向CSV读数据

转换为js对象

使用模块

```javascript

const csv = require("csvtojson");

csv().fromFile("E:/a.csv").then(i =>{
    console.log(i)
})



封装

function readCSV(filePath) {
  return  csv().fromFile(filePath)
    因为作者里面用的就是Promise就是异步的所以直接return就行了接受还得.then()
}
```





### path

（简化路径）

```javascript
const path = require('path')
path.join('a','b')
就是 a/b
```



从一个路径中获取到文件名

```javascript
原生写法
let str4 = "E:/data/xxx.csv"
let a = str4.lastIndexOf('/')
let name = str4.substring(a+1);



const path = require('path')
let str4 = "E:/data/app.csv"
path.basename(str4)//app.csv
```

从一个路径中获取到文件扩展名（后缀名）

```javascript
原生写法
let str4 = "E:/data/xxx.csv"
let a = str4.lastIndexOf('.')
let name = str4.substring(a);





const path = require('path')
let str4 = "E:/data/app.csv"
let suffix = path.extname(str4)//csv

```





在node.js中提供了一个变量__driname

```javascript
__driname:当前这个文件所在目录 的绝对路径

```







## express

可以当做一个静态资源服务器

也可以处理接

![image-20220911092821190](C:\Users\TOM\AppData\Roaming\Typora\typora-user-images\image-20220911092821190.png)

![image-20220911104002998](C:\Users\TOM\AppData\Roaming\Typora\typora-user-images\image-20220911104002998.png)

服务器使用

### 路由Get请求

**<font color='red'>req.query</font>**

```javascript
const express = require("express");

const app = express();

//静态资源托管（让express当成一个静态资源的服务器使用）
app.use(express.static("public"))




//配置路由,get请求
app.get("/xx",function (req, res) {
    let param = req.query 是ajax传过来的data , 服务器收到的参数会自动转换为对象
     console.log(param); 
    res.send('成功')
})



//创建端口
app.listen(3000,function () {
    console.log("服务器启动")
})
```

### 路由Post请求

express 默认只会处理get请求的参数 req.query

但是并没有提供处理POST请求的方法

在post请求中是收不到req.body的也就说收不到前端传过来的数据，需要依靠模块





解决方案:使用第三方模块<font color='red'>body-parser</font>来帮助我们在req对象上添加一个body属性

下载并安装body-parser

```javascript
const express = require("express");
const bodyParser = require("body-parser");

const app = express();

app.use(bodyParser.urlencoded({extended:false}))
将post请求的url参数绑定到req.body上

```

在高版本中

```javascript
const express = require("express");

const app = express();

app.use(express.urlencoded({extended:false}))
将post请求的url参数绑定到req.body上

```



![image-20220911115641301](C:\Users\TOM\AppData\Roaming\Typora\typora-user-images\image-20220911115641301.png)

```javascript
  $("#post").click(function () {
        $.ajax({
            url:"http://localhost:3000/appType/listPost",
            type:"post",
            dataType:'json',
            data:{id:1,name:'admin'},
            success(res){
                console.log(res)
            }
        })
    })




app.post("/appType/listPost",function (req, res) {

    let param = req.body;
    console.log(param);
    res.send({status:1,msg:'成功'})
})

```









### 动态参数

不支持数组，对象都不行

**<font color='red'>req.params</font>**

```javascript
  $("#Dyn").click(function () {
        $.ajax({
            url:"http://localhost:3000/list/python,1",
            type:"get",
            dataType:'json',
            success(res){
                console.log(res)
            }
        })
    })




//动态
app.get("/list/:keyword,:page",(req, res) => {
    let param = req.params;//获取动态参数
    console.log(param);
    
    res.send({status:1,msg:'成功'})
})
```



## 路由模块(router)

看起来清爽、简洁，防止路由路径冲突，接口查找效率低，后期维护不方便



路由模块：按照接口的业务功能来将不同的路由封装成一个个独立的模块

alt+enter自动补全const

```javascript
创建步骤
1、创建一个routes文件

2、创建路由模块文件
xxxRouter.js

3、创建一个路由对象 
let router = express.Router();
router.xxx("/路径",function(req,res){})


4、暴露路由对象
module.exports = router






在app.js中
1、加载路由模块
2、注册路由





```

具体操作

```javascript
具体
//用户路由模块（处理用户相关模块）
const express = require("express");//同一个模块只会加载一次就放在缓存中


//1.创建路由对象
const  router = express.Router();


//2.配置具体的路由
router.get("/user/add",function (req, res) {
    console.log("执行了")
    res.send('ok')
})


module.exports = router;

-------------------------------------------------------------------
    
    
在app.js中，汇集总的路由模块

//1、加载模块
const express = require("express");
let userRouter = require("./routes/userRouter");

//2、获取express实例
const app = express();


//3.配置路由模块(加载、注册)
app.use(express.static("public"));//资源静态托管(默认加载index)
app.use(express.urlencoded({extended:false}));//出来req.body
app.use("/user",userRouter);//注册路由模块












//4、监听端口
app.listen(3000,function () {
    console.log('成功启动服务器')
})

```



### 优化

```javascript

app.use("/user",userRouter);
可以在调用的时候再前面写路径，节约时间


router.get("/add",function (req, res) {
    console.log("执行了")
    res.send('ok')
})

```



![image-20220914091303474](C:\Users\TOM\AppData\Roaming\Typora\typora-user-images\image-20220914091303474.png)



## 图片预览

```js
<input type="file" name="avatar" class="form-control" onchange="showAvatar(this,想渲染的ID)">
    
    function showAvatar(fileDom,imgDom){
    1.验证文件的类型是否是图片类型(image/xxx)
    let file = fileDom.files[0]
    if(!/^image\/[a-zA-Z]+$/.test(file.type) ){
        alert("请选择正确的图片文件");
        fileDom.value="";
    }
    2.创建文件预览器来完成图片的预览
    let fr = new FileReader();
    fr.readAsDataURL(file);//读取的是一个二进制文件对象
    fr.onland = function(){
        imDom.src = this.result//将图片预览的结果与img的src绑定
    }
}
  
   $("#addAvatar").change(function(){
       showAvatar(this,$('#imgBox'[0]))//第二个参数是把jq转换为原生对象
   })
```



## 文件上传

将客服端本地的文件上传到服务器



**<font color='red'>请求方式必须得是POST</font>**

![image-20220914091409246](C:\Users\TOM\AppData\Roaming\Typora\typora-user-images\image-20220914091409246.png)



![image-20220914091420320](C:\Users\TOM\AppData\Roaming\Typora\typora-user-images\image-20220914091420320.png)



### 1、通过表单同步

初级用法

**<font color='red'>请求方式必须得是POST</font>**



action：需要将表单的参数提交到那个服务器接口

method:请求方式 get,post

enctype:表单参数的编码形式

​        form默认参数 application/ x-www-form-urlencoded(url编码格式)不能识别中文，

​			地址栏的URL编码是基于IOS-8859-1的国际编码



​        文件上传专用：multipart/form-data

​				相当于转换成  机械码010101编码

```js
app.use(express.urlencoded({extended:false}))只能解析表单是 application/ x-www-form-urlencoded的
```



```javascript
action:需要将表单的参数提交到哪个服务器接口
<form action="http://localhost:3000/upload" method="get" entype="表单参数的编码方式">
	<input type="text" name="username">
     <input type="file" name="myFile">
     <input type="submit">
    
</form>
```



**<font color="red">需要安装模块才能上传</font>**

​	<font color='red'>multer中间件</font>

1. 将客户端的文件上传到服务器
2. 将上传够的文件信息放在req.file中
3. 将其他参数放在req.body中

```js
const express = require('express')

const multer  = require('multer')
const upload = multer({ dest: 'public/uploads/' })想要放的文件夹

const app = express()
app.use(express.static("public"))
app.use(express.urlencoded({extended:false}))

//form中上传那个name是谁single里就是什么
app.post("/upload",upload.single('myFile'),function((req,res)=>{
         let param = req.query;
         res.send()
         }))
```

放到文件里的是压缩过的文件

```js
upload.single('myFile')是中间件

multer可以将multipart/form-data格式的数据解析出来


1.内部封装了很多文件的读写操作，帮助我们将客户端的数据保持成一个文件

2.将普通的表单参数全部封装到了 req.body中

3.将已经上传的文件信息保存在 req.file 或 req.files中
```





### 2、根据ajax异步上传

```js
<form id="addForm">
	<input type="text" name="username">
     <input type="file" name="myFile">
     <button type="button" id="btnSend"></button>
   
</form>


 <script>
        $("#btnSend").click(function () {
            $.ajax({
                url : "http://localhost:3000/upload",
                type:"post",
                data: new FormData($('#addForm')[0]),//表单的参数，高级类型，能获取到上传文件的地址
                contentType : false,//不会按照表单默认上传编码
                processData : false,//processData: false, 时参数将会变成 [object object]后台将无法获取参数
                dataType:"json",
                success({path}){
                    $('#show').prop("src", path);
                }
            })
        })
 </script>




---------------------服务器--------------------------------
const express = require('express')

const multer  = require('multer')
const upload = multer({ dest: 'public/uploads/' })想要放的文件夹

const app = express()
app.use(express.static("public"))
app.use(express.urlencoded({extended:false}))

//form中上传那个name是谁single里就是什么
app.post("/upload",upload.single('myFile'),function((req,res)=>{
         let param = req.body;
         console.log(param)
 	console.log(req.file)//打印出上传后文件的信息

	let {filename} = req.file;
	let path = `http://localhost:3000/uploads/${filename}`;
	
         res.send({msg:"上传成功",path})
         }))
        
    app.listen(3000)
```



```js
console.log(req.file)
会打印出
{
    fieldname:     input中的name
    originalname:   上传前源文件名
    encoding:
    mimetype:    文件类型
    destination:   上传到的目录
    filename:    	上传后文件的名字
    path:	
    size:
}
```







### 3、高级用法及封装

```js
const express = require("express");
const multer = require("multer"); // 加载multer模块

const path = require("path");
const { v4: uuidv4 } = require('uuid');//会产生32位不重复的字符

// 配置磁盘文件上传的规则
const storage = multer.diskStorage({
    destination: function (req, file, cb) {
        cb(null, 'public/uploads'); //文件需要上传到哪
    },
    filename: function (req, file, cb) {
        let filename = uuidv4().replaceAll("-","");//将-变成空
        let suffix = path.extname(file.originalname);//获取到上传文件的后缀名
        cb(null, filename+suffix);//上传后的文件名
    }
})
const upload = multer({ storage: storage })//规定磁盘文件上传的规定


const app = express();
app.use(express.static("public"));
app.use(express.urlencoded({extended: false})); // 只能解析表单是application/x-www-form-urlencoded格式的参数

// 文件上传
app.post("/upload",upload.single('myFile'),function (req,res) {
    let param = req.body;
    console.log(param);
    let {filename} = req.file; // 获取到上传的文件名
    let path = `http://localhost:3000/uploads/${filename}`;
    res.send({msg:"上传成功",path});
})

app.listen(3000);
```

​	

封装

```js
// 文件上传配置
const multer = require("multer");
const path = require("path");
const { v4: uuidv4 } = require('uuid');

const storage = multer.diskStorage({
    destination: function (req, file, cb) {
        cb(null, 'public/uploads');
    },
    filename: function (req, file, cb) {
        let filename = uuidv4().replaceAll("-","");
        let suffix = path.extname(file.originalname);
        cb(null, filename+suffix);
    }
})
const upload = multer({ storage: storage })

//获取到文件上传后服务器真实的访问路径
function fileServerPath({filename}){
    return `http://localhost:3000/uploads/${filename}`;
}
相当于
function fileServerPath(req){
    let {filename} = req.file;//获取到上传成功的文件信息
    let path =  `http://localhost:3000/uploads/${filename}`
    return path
}


module.exports = {
    upload,fileServerPath
}
```



在修改框的时候是用New Formadate（）是获取不到当前图片的信息的，因为图片没显示在form表单里，需要手动判断添加

由于express对象是有问题的，所以换数据的时候可以...深拷贝下







### 上传多文件

在需要的input上加个multiple就可以多选了

upload.arry

req.files

```js
<form if="testForm">
    <p><input type="text" name="username"> </p>
	 <p><input type="file" name="myFile" multiple> </p>
<button type="button" id="btnBatcjSend"></button>
</form>


app.post("/upload",upload.arry('myFile'),function (req,res) {
    let param = req.body;
    console.log(param);
    let {filename} = req.files; // 获取到上传的文件名
    let path = `http://localhost:3000/uploads/${filename}`;
    res.send({msg:"上传成功",path});
})


另一种可以限制上传文件的数量
多余的话会报错
app.post("/upload",upload.arry('myFile'，3),function (req,res) {
    let param = req.body;
    console.log(param);
    
    let {filename} = req.files; // 获取到上传的文件名
    
    let path = `http://localhost:3000/uploads/${filename}`;
    res.send({msg:"上传成功",path});
})

```



上传身份证正反面类似

```js
<form if="testForm">
    <p><input type="text" name="username"> </p>
	 <p>身份证正面<input type="file" name="fornt" > </p>
 	<p>身份证反面<input type="file" name="reverse"> </p>
<button type="button" id="btnBatcjSend"></button>
</form>

上传正面各一张
app.post("/upload",upload.fields([{name:"fornt",maxCount:1},{name:"reverse",maxCount:1}]),function (req,res) {
  let frontPath = fileServerPath(req.files['front'][0]);
    let reversePath = fileServerPath(req.files['reverse'][0]);
    
    res.send({msg:"上传成功",path});
})

```

![image-20220915000210733](C:\Users\TOM\AppData\Roaming\Typora\typora-user-images\image-20220915000210733.png)

## 文件下载



# Express-API接口

## 1. 浏览器的跨域

### 1.1 域（源）

一个域，它由三部分组成

- **协议**： http://   https://
- **IP** :  每台计算机都应该有一个唯一的IP地址： localhost  127.0.0.1  192.168.13.15
- **端口号** ：计算机中安装或启动的每一个应用程序，都占用着一个独立的端口号

### 1.2 同源策略

**浏览器中**，处于安全考虑，要求只能在**相同的域之间访问**，这就是浏览器的同源策略

同源 ： 指的就是当前页面所在的**协议、IP、端口**，和在页面中发送请求路径的 **协议、IP、端口**必须一致，只要有一个不一样，就是跨域访问。

默认情况下，浏览器是不允许跨域访问的。

![image-20220621153821143](https://woniumd.oss-cn-hangzhou.aliyuncs.com/java/panguanghua/20220621153821.png)

### 1.3 跨域

在请求中，只要协议 、IP、端口三者之中有一个不一样，就是跨域

>特殊 ： 在浏览器中 img, script， link 支持跨域访问的

```html
<img src="http://localhost:3000/images/0.jpg" width="100" alt="">
<script></script>
<link>
```

![image-20220921082623540](C:\Users\TOM\AppData\Roaming\Typora\typora-user-images\image-20220921082623540.png)

### 1.4  跨域的解决方案

- 通过webpack来配置开发服务器中的代理 proxy (在前端工程化中讲解) **一般不用**
- jsonp (只针对于GET请求，不支持post请求)
- 由后端开发人员来通过 CORS 解决接口访问跨域问题



## 2. Express 普通API接口

### 1.1 创建API 路由模块

```js
router.get("/list",(req,res) =>{
    let userList = [{id:1,username:"admin",password:"123"},
                    {id:2,username:"jack",password:"111"},
                    {id:3,username:"tom",password:"222"}]
    res.send(userList);
})
```

以上GET、POST接口，存在一个很严重的问题： 不支持跨域访问。

解决跨域访问的方案主要有两种：

- **CORS** (主流解决方案，推荐大家使用)
- **JSONP**(有缺陷的方案; **只能支持GET请求**)



## 3. CORS跨域API接口

### 3.1 接口的跨域问题

express 中定义的接口默认是不跨域访问的，如果要想让这些接口跨域可以访问，需要使用**cors**这个第三方的中间件。通过安装和配置这个中间件，就可以很方便的解决跨域问题

配置cors 跨域一共三步：

1. 安装cors中间件 【**npm i cors**】
2. 引入中间件 【**const cors = require("cors")**】
3. 在所有路由前配置中间件 **app.use(cors());**

```js
// 配置接口的跨域访问策略
let cors = require("cors");
app.use(cors())
```



### 2.3 cors中间件解决跨域问题

#### 2.3.1 自定义cors中间件

```js
const allowCrossDomain = function(req, res, next){
    // 设置允许跨域访问的请求源
    res.setHeader("Access-Control-Allow-Origin","*"); // 可以直接指定访问的ip(* 任意IP都可以访问)
    //设置允许跨域访问的请求头
    res.setHeader("Access-Control-Allow-Headers","X-Requested-With,Origin,Content-Type,Accept,Authorization");
    // 设置允许跨域访问的请求类型
    res.setHeader("Access-Control-Allow-Methods","GET,POST,PUT,DELETE,OPTIONS");
    // 允许cookie跨域请求发送到服务器（如果要发送cookie，Access-Control-Allow-Origin不能设置为 *）
    res.setHeader("Access-Control-Allow-Credentials","true");
    next();
}
app.use(allowCrossDomain);
```

优化: 可以定义一些允许跨域访问的白名单

![image-20220622165702372](https://woniumd.oss-cn-hangzhou.aliyuncs.com/java/panguanghua/20220622165702.png)

```js
const allowCrossDomain = function(req, res, next){
    let whiteList = ["http://127.0.0.1:3000","http://localhost:3000","http://192.168.3.49:3000","http://localhost:8888"]; // 白名单
    if(whiteList.includes(req.headers.origin)){
        // 设置允许跨域访问的请求源
        res.setHeader("Access-Control-Allow-Origin", req.headers.origin); // 可以直接指定访问的ip(* 任意IP都可以访问)
        //设置允许跨域访问的请求头
        res.setHeader("Access-Control-Allow-Headers","X-Requested-With,Origin,Content-Type,Accept,Authorization");
        // 设置允许跨域访问的请求类型
        res.setHeader("Access-Control-Allow-Methods","GET,POST,PUT,DELETE,OPTIONS");
        // 允许cookie跨域请求发送到服务器（如果要发送cookie，Access-Control-Allow-Origin不能设置为 *）
        res.setHeader("Access-Control-Allow-Credentials","true");
    }
    next();
}
app.use(allowCrossDomain);
```



#### 2.3.2 第三方cors中间件

使用网址 ：https://www.npmjs.com/package/cors#configuring-cors



![image-20220921085020769](C:\Users\TOM\AppData\Roaming\Typora\typora-user-images\image-20220921085020769.png)









### 2.4 什么是 CORS

CORS (Cross- Origin Resource Sharing  跨域资源共享)，由一系列 HTTP 响应头组成，这些 HTTP 响应头决定了浏览器是否阻止 JS 代码跨域来获取数据。

浏览器的**同源安全策略**默认会阻止网页“跨域”获取资源。但是如果接口服务器配置了 CORS 相关的 HTTP 响应头，这样就可以解除浏览器端的跨域访问限制。



### 2.5 CORS 的注意事项

**CORS 主要是在服务器端来配置**， 客户端浏览器无需做任何额外的配置，即可以请求开启了CORS 的接口

CORS 在浏览器中有兼容性，只有支持 XMLHttpRequest Level2的浏览器，才能正常访问开启了CORS的服务器接口 （IE10+、Chrome4+、FireFox 3.5+）



### 2.6 CORS 响应头参数解读

**（1）Access-Control-Allow-<font color=red>Origin</font>**

```js
Access-Control-Allow-Origin : origin | *
```

- `origin`:  **允许访问该资源的外域URL**

  ```js
  res.setHeader("Access-Control-Allow-Origin", "http://woniuxy.com")
  
  res.setHeader("Access-Control-Allow-Origin", "192.168.15.18")
  ```

- 通配符`*` :  允许任何域请求（不做任何限制）

  ```js
  res.setHeader("Access-Control-Allow-Origin", "*")
  ```

**（2）Access-Control-Allow-<font color=red>Headers</font>**

默认情况下， CORS 仅支持客户端服务器发送如下的9个请求头:

Accept、Accept-Language、Content-Language、DPR、Downlink、Save-Data、Viewport-Width、Width、Content-Type（值仅限于 text/plain 、multipart/form-data、application/x-www-form-urlencoded三者之一）。

如果客户端向服务器发送了**额外的请求头信息**，则需要在服务端，通过 **Access-Control-Allow-<font color=red>Headers</font>** 对额外的请求头进行声明，否则这次请求会失败。

```js
// 允许客户端向服务器额外发送 ：X-Requested-With,Origin,Content-Type,Accept,Authorization 请求头
// 注意 ：多个请求头之间使用英文的逗号隔开

res.header("Access-Control-Allow-Headers","X-Requested-With,Origin,Content-Type,Accept,Authorization");
```

**（3）Access-Control-Allow-<font color=red>Methods</font>**

默认情况下， CORS 仅仅支客户端发起的 ： GET 、POST 、HEAD 请求

如果客户端希望通过 PUT、DELETE 等方式请求服务器的资源，则需要在服务器端，通过**Access-Control-Allow-<font color=red>Methods</font>**来指明实际请求所有允许使用的HTTP方式。

```js
// 只允许GET,POST,PUT,DELETE,OPTIONS 请求方式
res.setHeader("Access-Control-Allow-Methods", "GET,POST,PUT, 	 DELETE,OPTIONS");

// 允许所有的HTTP请求方法
res.setHeader("Access-Control-Allow-Methods", "*");
```

![image-20220621164937273](https://woniumd.oss-cn-hangzhou.aliyuncs.com/java/panguanghua/20220621164937.png)

## 2.7 CORS 请求分类

客户端在请求 CORS 接口时， 根据**请求方式** 和 **请求头** 的不同，可以将CORS的请求分为两大类

- 简单请求
- 预检请求

### 2.7.1 简单请求

同时满足下面两大条件的请求，就是简单请求

- 请求方式 ： GET、POST、HEAD三者之一
- HTTP 头部信息不超过以下的几种字段 ： **无自定义头部字段**、Accept、Accept-Language、Content-Language、DPR、Downlink、Save-Data、Viewport-Width、Width、Content-Type（值仅限于 text/plain 、multipart/form-data、application/x-www-form-urlencoded）

### 2.7.2 预检请求

只要符合以下任何一个条件的请求，就是预检请求

- 请求方式为 ： GET、POST、HEAD 之外的请求
- 请求头中**包含自定义的头部字段**(身份认证)
- 向服务器发送了 **application/json** 格式数据的请求

在浏览器与服务器正式通信前，浏览器会**先发送一个 OPTION 请求进行预检，以获知服务器是否允许该实际请求**。所以这一次的 OPTION 请求称之为"预检请求"。

服务器成功响应预检请求后，才会发送真正的请求，并且携带真实的数据。

本质 ：  发送了两次请求（第一次验证能否正常访问，第二次才会发送真正的请求）

### 2.7.3 对比

- 简单请求
  - 客户端与服务器间只会发生一次请求
- 预检请求
  - 客户端与服务器间只会发生两次请求
    - OPTION 预检请求成功后，成功后才会发送真正的请求



## 3. JSONP 接口

### 3.1 jsonp简介

jsonp 的本质就是 ： 浏览器可以通过 script 标签的src 属性，请求服务器上的数据。同时，服务器返回一个函数的调用。这种请求数据的方式叫做: jsonp

- JSONP 不属于真正的AJAX请求，因为它没有使用 XMLHttpRequest 这个对象
- JSONP 仅仅支持 GET 请求，不支持其他类型的请求（post、put、delete）

### 3.2 实现jsonp接口步骤

- 获取客户端发送过来的**回调函数的名字**  callback
- 获取服务端数据
- **拼接出一个函数调用的字符串**
- 把这个字符串响应给客户端的script 标签，当标签一旦解析，就会执行回调函数获取到服务器中的数据

### 3.3 jsonp接口代码

```js
// 演示JSOP的处理
router.get("/list",(req,res) =>{
    let callback = req.query.callback; //获取前端发送JSONP的回调函数
    let userList = [{id:1,username:"admin",password:"123"},
        {id:2,username:"jack",password:"111"},
        {id:3,username:"tom",password:"222"}]
    res.send(`${callback}(${JSON.stringify(userList)})`);
})
```

### 3.4 前端发送jsonp请求

#### 3.4.1 script脚本发送jsonp请求

```js
<span id="testJsonp">使用JSONP的方式来请求数据</span>
<script>
// 验证JSONP原理
        $('#testJsonp').click(function () {
            let myScript = `<script src="http://localhost:3000/user/list?callback=test"><\/script>`;
            $('body').append(myScript)
        })

        function test(data){
            console.log(data);
        }
</script>
```

#### 3.4.2 $.ajax发送jsonp请求

推荐大家使用 $.ajax  发送请求

```html
<span id="testAjaxJsonp">使用ajax发送jsonp数据</span>
<script>
    // ajax发送jsonp请求
    $('#testAjaxJsonp').click(function () {
        $.ajax({
            url :"http://localhost:3000/user/list",
            type:"get",
            dataType: "jsonp", // 接收服务端的数据格式 jsonp
            success(res){
                console.log(res);
            }
        })
    })
</script>
```



### 3.5 注意事项	

如果项目中已经配置了CORS 跨域资源共享， 为了防止冲突，必须在配置CORS 中间件之前声明 JSONP接口，否则 JSONP接口就会被处理成开启了CORS的接口

```js
// 演示JSOP的处理
app.get("/list",(req,res) =>{
    let callback = req.query.callback; // 获取到前端发送JSONP的回调函数
    let userList = [{id:1,username:"admin",password:"123"},
        {id:2,username:"jack",password:"111"},
        {id:3,username:"tom",password:"222"}]
    res.send(`${callback}(${JSON.stringify(userList)})`);
})

// 配置服务器的跨域访问策略
let cors = require("cors");
app.use(cors());
```

总结： 以后的跨域访问配置可以使用 CORS（跨域资源共享） 来解决



## 4. RESTful 架构 

RESTful是一种后端接口的开发架构规范。

RESTFUL是一种网络应用程序的设计风格和开发方式，基于**HTTP**，可以使用XML格式定义或JSON格式定义。RESTFUL适用于移动互联网厂商作为业务接口的场景，实现第三方[OTT](https://baike.baidu.com/item/OTT/9960940)调用移动网络资源的功能，动作类型为新增、变更、删除所调用资源。

简单来说 ： 就是 url地址中只包含名词表示资源，使用 http 动词表示动作进行资源的操作

接口命名的规范

在RESTFul之前，我们的接口都由两部分组成

- 一级接口 ：表示请求资源（数据）名称
- 二级接口：资源的操作（增删改查）

RESTFul中，要求接口只有一个资源名称，用来表示要请求的资源（数据）名称 

例如：关于电影的请求，接口都是/movies。

但是，我们为了区别对同一个集合数据的不同操作，RESTFul中有引入了两种新的请求类型： PUT  DELETE

```js
POST /movies/add
GET /movies/delete?id=1
POST /movies/update
GET /movies?id=1
```

RESTful 重构接口后的效果（ 使用请求类型来表示不同的资源动作）

```js
POST       /movies        新增
DELETE     /movies/:id    删除    /movies/1
PUT		   /movies        修改
GET        /movies/:id    查询    /movies/1
```



### 4.1 请求类型

RESTful中，常用的请求类型主要有一下这四个：

- GET    :  获取数据
- POST ：新增数据
- PUT ： 修改数据
- DELETE ：删除数据

例如，我们要对电影数据进行增删改查 CRUD操作: 接口参考如下

- 获取电影数据 ： GET         /movies
- 新增电影数据 ： POST      /movies
- 修改电影数据 ： PUT        /movies
- 删除电影数据 ： DELETE  /movies

```js
$.ajax({
    url : "/路由",
    type : "GET/POST/PUT/DELETE"
    success(res){
        
	}
})
```



### 4.2 请求参数处理

在RESTFul中，如果请求的参数中需要传递参数，我们可以将参数通过url来进行发送

例如： 我们要根据电影的id来获取电影数据

```js
$.ajax({
    url : "/movies/1",
    type : "GET"
    success(res){   
	}
})
```

```js
router.get("/movies/:id", function (req,res,next) {
    console.log("GET  /movies 执行了");
    console.log(req.params.id);
})

router.post("/movies", function (req,res,next) {
    console.log("POST  /movies 执行了");
    console.log(req.body);
})


router.put("/movies", function (req,res,next) {
    console.log("PUT  /movies 执行了");
    console.log(req.body);
})


router.delete("/movies/:id", function (req,res,next) {
    console.log("DELETE  /movies 执行了");
    console.log(req.body);
})
```

### 4.3 RESTful过滤参数

```js
users/list?limit=10      返回指定条数的数据
users/list?offset=10     返回返回记录开始的位置的数据（skip）
users/list?page=2&per_page=10  指定第几页，每页显示的记录数
users/list?sortby=name&order=asc  指定排序的列及排序的类型（升序降序）
```













# ES6模块化

​		默认情况下，若果多个js文件在同一个HTML 页面引入，他们是共享同一个全局作用域（这样就可能会导致很多问题【重复变量名的覆盖、冲突】，引发代码报错，非常不利用多人协作的开发）

​		从ES6开始， js中支持原生的模块化开发。可以把前端的每一个js 文件都看作是一个独立的模块，每一个js文件都有自己独立的作用域（模块化作用域）。js与 js之间，默认情况下时不能互相访问数据的

![image-20220623100118907](https://woniumd.oss-cn-hangzhou.aliyuncs.com/java/panguanghua/20220623100119.png)







## 2.1 设置模块

将script标签中的type属性设置成 module ,则这个js就作为一个模块来使用

```html
<script scr="" type="module">
```

一旦将js变成模块后，则这个模块只能独立运行，若我们想要在HTML引入它，只能通过 script 标签来引入，但是虽然引入成功了，也能执行模块中的逻辑，但是HTML中是无法直接去使用这个模块暴露出来的内容

## 2.2  引入模块

在模块化开发过程中，我们可以在一个JS文件中通过`import` 引入另一个 JS 文件

通俗  ： 一旦将js变成模块，就必须在模块中才能使用其他的模块， html中不能直接访问到某个模块的数据

```js
import "./js文件的路径"

注意事项： 同级之间必须加 ./  ,  上一级需要通过 ../
```

通过这种方式引入的模块，只能运行这个模块中的代码，并不能获取到该模块内部的额数据



## 2.3 模块的暴露与引入

默认情况下。每一个模块之间都是相互独立的，数据都是私有的。但是，我们可以通过暴露的方式，将模块内的数据共享出来

另外，模块可以通过 `import` 方式，获取到其他模块暴露出来的数据。



#### 1） 暴露

暴露的语法分为两种：

- 只暴露一条数据：<font color=red> **export default  数据**</font>





暴露多条数据 ： <font color=red> **export  数据**</font>


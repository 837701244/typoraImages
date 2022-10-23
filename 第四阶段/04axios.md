#  axios 

## axios 基本使用

axios 是基于 Promise 实现的对 AJAX 技术的一种封装。

axios 除了支持浏览器外，还支持 Nodejs。也就是说，我们可以在浏览器中通过 axios 向服务器发送请求，也可以在 Nodejs 服务器中向其他服务器发送请求。

#### 下载 axios

在项目根目录执行以下命令，下载 axios：

```bash
npm install axios
or
yarn add axios
```

#### 引入

在需要使用 axios 的组件中，引入 axios：

```js
import axios form "axios"
```

#### 基本用法

axios 发送请求时，GET 类型的请求，参数需要通过 `params` 进行发送。其他类型的请求，都通过 `data` 进行发送。

```js
this.axios({
    url:"http://localhost:6600/api/getmovie",
    method:"GET",
    params:this.pageInfo
}).then(res=>{
    console.log(this,res.data)
}).catch(err=>{
    console.log(err)
})
```

axios 请求成功后，返回的是一个 Promise 对象，可以通过 `then` 方法或 `await` 来接收响应结果。

```js
axios({...}).then(res=>{
       //code ...
})

async fn(){
	const res=await axios({...})    
}
```

####  GET 方法二

```JS
 this.axios.get(url,{params:{参数}})
```

#### POST 方法二

```JS
this.axios({
      url:"http://localhost:6600/api/adduserdata",
      method: "POST",
      data:this.userInfo,
  }).then(res=>{
      console.log(res)
      if(res.data.status){
          alert("用户数据成功录入")
          console.log(res.data.data)
      }
  }).catch(err=>{
      console.log(err)
  }) 
```

```js
  this.axios.post(url,{参数}})
```

post还能这样简写，get就不能这样简写	



## 全局挂载

考虑到多个组件中都要使用 axios，所以我们还可以将 axios 挂载到 Vue 实例上。

在 main.js 中设置以下代码：

```js
import axios from "axios"
Vue.prototype.axios=axios; //把axiso挂载到Vue实例的原型上.
```

配置完成后，在任何组件范围内，就都可以直接通过 `this.axios` 来使用 axios。



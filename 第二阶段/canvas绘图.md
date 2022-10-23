## canvas 概念

### 绘图技术(canvas)

- HTML5 新增了`<canvas></canvas>`,再配合JavaScript配套的api。能够实现在页面上进行绘制几何图形。一般会借助JavaScript的定时器可以实现各种各样的动画。
- JavaScript本身支持canvas 和webGL 两种绘图技术.Canvas面向的是2d绘制。webgl是3d绘制.

### JavaScript中的”画画”:基础概念

- `<canvas><canvas>`:画布

  - 指的就是HTML5中的 canvas标签，它在JavaScript的绘制技术中充当”画布”的角色。一个页面可以有多个画布。

- 画笔

  - 是JavaScript提供的一个对象。每个画布都有一个专属的”画笔”。画笔里包含了大量的绘制相关api。开发人员利用api来在`<canvas>`中进行绘制

- 如何获取画笔和画布

  - 画布：通过原生dom 函数获取。
  - 画笔：通过画布调用`getContext('2d')`来获取

  ```js
  var canvasArea=document.getElementById("canvasArea");//获取标签 画布1
  //配置画笔
  var ctx=canvasArea2.getContext("2d")
  ```

### 画布中的 坐标系

- 以画布的左上角为原点`(0,0)`.x轴向右为正。y轴向下为正。

### 路径&子路径

- 路径：画布会把一段闭合的线条称为一个完整路径。一个完整路径包含了多个子路径。
  - 画布的 一个图形就是一个完整的路径
- 子路径：是绘图当中的一个线条。多个子路径可以构成一个闭合的完整的路径

## canvas API

### 几何图形

- `moveTo()`:确定”落笔”的位置。将画笔移动到指定坐标。

  ```js
   //画笔移动到开始坐标位置
  ctx.moveTo(0,0)
  ```

- `lineTo()`:从画笔位置到指定位置勾勒出一条子路径

  ```js
   //画直线
  ctx.lineTo(400,400)
  //勾勒路径 (线路填充)
  ctx.strokeStyle="red";
  ctx.stroke()
  ```

- `stroke()`：绘制已经勾勒出的所有子路径

  ```js
   ctx.stroke()
  ```

- `lineWidth`:设置线条的粗细程度

  ```js
  ctx.lineWidth=1;
  ```

- `strokeStyle`:设置线条的颜色

  ```js
   ctx.strokeStyle="red";
  ```

## 填充

- fill():对图形进行填充

  ```js
  ctx.fill()
  ```

- fillStyle:设置填充的颜色

  ```js
  ctx.fillStyle="rgba(0,255,0,.6)"
  ```

## 绘制文字

```js
//绘制文字轮廓
ctx.font="42px Arial"; //文字大小,字体
ctx.strokeStyle="yellow";
ctx.strokeText(str,128,198)
// 绘制文字
ctx.font="40px Arial"; //文字大小,字体
ctx.fillStyle="black"
ctx.fillText(str,130,200)
```

## 总结

- 绘制矩形 strokeRect(x,y,width,height)

  ```js
  //画一个矩形
  ctx.moveTo(20,20) //x,y
  ctx.strokeRect(100,20,200,100) //x,y,w,h
  ```
  
- 绘制线段 lineTo(x,y)

  ```js
  //画直线
  ctx.lineTo(400,400)
  ```
  
- 绘制圆(弧形) arc(x,y,半径,开始角度,结束角度,是否是逆时针)

  ```js
  
   //画一个弧形
  ctx.moveTo(300,200)
  ctx.arc(200,200,100,0,Math.PI*2,false)  //x,y,半径,开始角度 false 顺时针
  ctx.stroke()
  ```
  
- 绘制文字

  ```js
  //绘制文字轮廓
  ctx.font="42px Arial"; //文字大小,字体
  ctx.strokeStyle="yellow";
  ctx.strokeText(str,128,198)
  // 绘制文字
  ctx.font="40px Arial"; //文字大小,字体
  ctx.fillStyle="black"
  ctx.fillText(str,130,200)
  ```
  
- 打开路径（重复绘制时有效果）,例如点击更换文字

  ```js
  ctx.beginPath()
  ```

- 关闭路径（重复绘制时有效果）

  ```js
  ctx.closePath()
  ```

- 清除画布区域（重复绘制时有效果）

  ```js
  ctx.clearRect()
  ```

  

## 实战验证码

```js
<div class="container">
    <form>
        <ul>
            <li>
                <input type="text" class="form-control" placeholder="用户名" required>
            </li>
            <li>
                <input type="text" class="form-control" placeholder="密码" required>
            </li>
            <li>
                <canvas height="400" width="400" style="background-color: #efefef" id="canvasArea"></canvas>
            </li>
            <li>
                <input type="text" class="form-control" placeholder="验证码" onchange="checkFn()">
            </li>
            <li>
                <button id="btnEle" disabled="true">登录</button>
            </li>
        </ul>
    </form>
</div>
<script>
    var words=Mock.mock('@word')
    function initYZM(str) {
        //获取标签 画布1
        var canvasArea=document.getElementById("canvasArea");
        //配置画笔
        var ctx=canvasArea.getContext("2d")
        // console.log(ctx)
        //画笔移动到开始坐标位置
        ctx.moveTo(0,0)
        //画直线
        ctx.lineTo(400,400)
        //勾勒路径 (线路填充)
        ctx.strokeStyle="red";
        ctx.stroke()
        //画一个矩形
        ctx.moveTo(20,20) //x,y
        ctx.strokeRect(100,20,200,100) //x,y,w,h
        //画一个弧形
        ctx.moveTo(300,200)
        ctx.arc(200,200,100,0,Math.PI*2,false)  //x,y,半径,开始角度 false 顺时针
        ctx.stroke()
        //填充
        ctx.fillStyle="rgba(0,255,0,.6)"
        ctx.fill()
        //绘制文字轮廓
        ctx.font="42px Arial"; //文字大小,字体
        ctx.strokeStyle="yellow";
        ctx.strokeText(str,128,198)
        // 绘制文字
        ctx.font="40px Arial"; //文字大小,字体
        ctx.fillStyle="black"
        ctx.fillText(str,130,200)
    }
    initYZM(words)
function checkFn() {
    let userStr=$(event.target).val()
    if(words==userStr){
        $("#btnEle").prop("disabled",false)
    }else {
        $("#btnEle").prop("disabled",true)
    }
}
</script>
```








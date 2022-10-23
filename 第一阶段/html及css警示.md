# html及css警示

## 1.容器划分，2.写代码

### 1.容器划分（1.框架，2.定位，3.内容）

### 2写代码（1.通配符，2.框架-宽高背景-离其他框架的位置，3.定位-宽高-距离(盒子模型和浮动)，4内容-辅助配置【字体大小、水平居中、垂直居中、鼠标效果，颜色、宽高】）



## 当宽高是百分比的时候一定要加min-宽高



## opcity是透明度



## flex做输入框设置

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        *{
            padding: 0;
            margin: 0;
        }
        .div0 {
            width: 250px;
            margin: 20px auto;
            border: 1px solid #dcdcdc;
            /* background-color: #dcdcdc; */
            display: flex;
        }
        .div0 label {
            font-size: 14px;
            text-align: center;
            flex: 1;
            background-color: #f5f5f5;
        }
        /*想要具体多宽都可以设置*/
        .div0 label:last-child {
            flex: 0  90px;
        }
        .div0 input {
            border: 0;
        }
    </style>
</head>
<body>
    <div class="div0">
        <label for="">姓名</label>
        <input type="text" name="" id="">
        <label for="">go</label>
    </div>
</body>
</html>
```




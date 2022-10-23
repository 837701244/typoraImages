08.CSS背景

# 1.CSS背景

`background-color`:设置背景颜色

- 英文单词
- 十六进制#000000-#FFFFFF
- RGB（0-255,0-255,0-255）

`background-image`:设置背景图片

```html
background-image:url(图片路径)
```

`background-repeat`：设置背景图片是否平铺

- `repeat`默认值，水平和垂直方向都平铺
- `repeat-x`：水平方向平铺（X轴方向）
- `repeat-y`：垂直方向平铺（Y轴方向）
- `no-repeat`：不平铺

**课堂案例**

利用1px完成一个长条的平铺效果

![image-20220701143334268](https://woniumd.oss-cn-hangzhou.aliyuncs.com/web/caoshengjie/20220701143334.png)

注意：在不平铺的状态下。背景图片时默认对齐与标签元素的左上角点

![image-20220701143608650](https://woniumd.oss-cn-hangzhou.aliyuncs.com/web/caoshengjie/20220701143608.png)

`background-position`：设定背景图片的位置

- 单词：left/right/center/top/bottom 可以两两搭配使用
- x值，y值
  - 像素：如10px，是以容器的左上角点为00原点
  - 百分比：比如 50% 50%

`background-size`：设置背景图片的大小

- `contain`图像一边铺满。另一边等比自动剪裁

- `cover`两边都铺满，超出部分才隐藏

- ```
  X轴和Y轴
  ```

  - 像素
  - 百分数

`background-attachment`：设置背景图片是否固定

- `scoll`:默认值，背景会随着页面的滚动而滚动

- `fixed`：固定在页面上

  

`background`复合属性

```css
background:颜色 背景url 平铺 定位 / 大小
background pink url(img/1.jpg) no-repeat 100px 50px / 100px 100px
```

## 雪碧图

- 将多张图片组合在一张图片上的图片格式，这样做可以减少网络的流量，同时优化代码
- 原理：通过css样式`background-image`和`background-position`来实现在容器中显示一个图标的效果

![image-20220701153919952](https://woniumd.oss-cn-hangzhou.aliyuncs.com/web/caoshengjie/20220701153920.png)

说明：给出一个只能显示1个图案的容器大小。根据css背景定位属性来设置显示的部分背景图像。以此做到雪碧图的不同位置图像的呈现



# 2.CSS文本样式

- ```css
  text-algin
  ```

  ：设置文本的水平对齐方式

  - left
  - center
  - right

**注意：**只能针对于文本类型操作，无法对盒子容器类型进行设定（table,div）

文本系（超链接，普通文本，图片）



- ```css
  text-decoration
  ```

  ：设置文本的修饰符

  - `none`：无
  - `underline`：下划线
  - `line-through`：给文本添加一个删除线
  - `overline`：上划线





- ```css
  line-height
  ```

  ：设置行的高度

  - 像素
  - 数字
  - 百分数

**说明：**浏览器大部分会默认文本为16px大小

- `letter-spacing`：设置字符间距，一个字符就是一个中文（中文字的间隔大小）
- `word-spacing`：设置字间距，以空格来区分（两个英文单词之间的半角空格的大小）
- `text-transform`：设置字母文本的大小写
  - `Capitalize`首字母大写
  - `uppercase`全大写
  - `lowercase`全小写
  - `none`无
- `direction`设置文本的方向 ltr rtl



# 3.CSS行块转换

在html中的所有标签都存在是否独占行的行为

- 独占行：块级标签
- 不独占行：行级标签

### 块级标签

- 每个标签都独占一行
- 可以设置高和宽

### 行级标签

- 每个标签不独占行，可以连续放置行级标签
- 不可以设置高和宽，行级标签的高和宽是有内容自行决定的

## 行和块级的相互转换

可以将行级元素直接转换为块级元素（转换后的标签便具有了块级元素的所有特点）

说明：当一个行级元素直接转换为块级元素后，就会有高宽设置，同时有独占行的特点



## 块级转换为行级

将一个块级元素直接转换为行级元素，并取消块级元素的所有特性



## 行内块元素

````css
display:inline-block
````

说明：inline-block是可以让块级元素横向排列，同时也可以设置高和宽。

转换后的标签还是算**行级**



# 4.CSS字体

`font-size`

设置字体大小



`font-family`

设置字体库

注意：微软雅黑不可以使用在商业页面，但可以在个人网站或非商业网站的使用。有版权问题



`font-weight`

设置字体粗细



`font-style`

设置字体风格

- normal：正常
- italic：斜体
- oblique：倾斜

## 字体引用技术

**作用：**为了保证一个网站使用特殊字体显示文本，而其他浏览器都能正常显示，我们就可以使用“字体引用技术”

步骤：

- 在网上找一种合适的字体
- 放在网站目录里
- 加载引入
- 使用

````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        /* 加载引入字体 */
        @font-face{
            /* 给字体库中的字体自选一个名字 */
            font-family: myfont;
            /* 引入字体的路径 */
            src: url(./fonts/徐静蕾字体.ttf),
            url(./fonts/徐静蕾字体.woff)
        }

        p{
            font-size:30px;
            /* 使用 */
            font-family: myfont;
        }
    </style>
</head>
<body>
    <p>
        这里是有新加载的字体
    </p>
</body>
</html>
````

## 字体图标

是一种以字体的定义存在，而显示的却是图像的一种字体形式，这是是可以在网络上进行配置和使用的，而非自己设置

Font Awecome官网

首先需要下载css和font文件夹，并且放置到网站目录中

在需要的html引入

````html
    <link rel="stylesheet" href="./css/font-awesome.min.css">

 <i class="fa fa-camera-retro"></i>
````

说明：`min.css`和普通`css`在功能上是一样的。只是min是被压缩过的文件。而普通css是没有压缩过。便于学习，如果开发练习都可以选择，单需要正式发布到公网需要使用min文件，因为小，所以下载或打开网页的速度快



# 5.CSS超链接

## 超链接的四种伪操作

一个超链接存在四种状态，我们可以在超链接定义选择器的时候对齐进行设置

- 未点击状态
- 鼠标悬停在超链接上
- 鼠标点击一次超链接
- 点击过后的超链接

````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        /* 未被访问 */
        a:link{
            color:rgb(47, 119, 228);
            text-decoration: none;
            font-size: 15px;
        }
        /* 访问过 */
        a:visited{
            color:rgb(149, 184, 236);
            font-size: 15px;
        }
        /* 悬停 */
        a:hover{
            color:orange;
            text-decoration: underline;
            font-size: 15px;
        }
        /* 点击 */
        a:active{
            /* color:blue; */
        }
        li{
            line-height: 30px;
        }
    </style>
</head>
<body>
    <h2>热点新闻</h2>
    <ul>
        <li>
            <a href="#">今天天气很热</a>
        </li>
        <li>
            <a href="#2">明天依然很热</a>
        </li>
        <li>
            <a href="#3">后天还是很热</a>
        </li>
    </ul>
</body>
</html>
````

说明：四种状态表明鼠标的四个动作。可以分别对进行设置，如果在一个样式文件中。一定要设置4个值，则需要按照 “L-V-H-A”的顺序书写，不然会有冲突

````css
   /* 单写一个a(link+visited) */
        a{
            color:black;
            text-decoration: none;
        }
````

说明：在现实开发中，我们经常会设置2个超链接值，a（代表以点击和未点击的状态），和a：hover，就可以实现大部分的效果

由于用于对于超链接的需求是跳转，所以一般不会设置点击状态

# 6.CSS列表

在html中

- 无序列表 ul...li
- 有序列表 ol...li

## 列表形式

`list-style-type`:设置列表项的标记点

去除列表前的点设置为`none`就可以

`list-style-image`:设置小图片在标记点位置，特别注意此图片不能通过css改变大小的



`list-style-position`：设置背景与标记点的关系

- outside:外部
- inside:内部

说明：标记点可以是背景内部显示，也可以是背景外部显示（默认），这样就可以很方便查看整个li的大小（如果去除了标记点，或者没有背景颜色则这个功能无效）

`list-type`复合属性

在生活中经常可以使用此属性来省略打法（`list-type:none`）

# 7.CSS盒子模型

## 盒子模型结构

是指所有HTML标签之间的距离和关系

![1591280993127](https://woniumd.oss-cn-hangzhou.aliyuncs.com/web/zhangrui/20210713102603.png)

盒子：html容器，典型div

- content：容器（盒子）内部的内容
- padding：内容和容器（盒子）的边距
- border：当前盒子的边框
- margin：盒子与盒子之间的距离（关系：兄弟关系，父子关系）

## border

设置语法

```css
标准边框三要素：宽度（width）、颜色(color)、样式(style)
border-方向-width:宽度像素值
border-方向-style：solid(实线) | dashed（虚线）| dotted(点线) | double(双线)
border-方向-color:颜色值
```

### 边框的复合属性

```css
border-方向：宽度  类型  颜色；
综合设置
border:宽度  类型  颜色
```

特别说明：加入border后，盒子的宽度会变大



## padding

设置盒子中内容和盒子边线的距离

````css
padding-top
padding-right
padding-left
padding-bottom
复合属性
padding: 一个值|两个值|三个值|四个值
一个值：四个边同时设置
两个值：上下  左右
三个值：上  左右   下
四个值：上  右   下   左 
````

说明：可以采用浏览器提供的检查工具，里面有盒子模型的具体参考图

注意：加入padding后，页面会呈现出继续加大占据网页空间的数值

如：占据空间 = width + padding + border

说明：padding是作为一个分隔盒子与内部元素之间距离，内部元素可以是文本也可以是其他盒子



## margin

盒子与盒子间距

- 兄弟关系
- 父子关系



## margin两大特性（填坑）

- **margin重叠性**
  - 如果盒子与盒子之间是**兄弟关系**，则正在垂直方向上的相互margin会发生重叠效应，大的数值作为最终的间隙距离（小的被层叠在里面了）
- **margin传递性**
  - 如何盒子与盒子之间是**父子关系**，对于子盒子的`margin-top`设置会直接传递给父盒子执行，即看到的效果是父盒子做了边距设定，而非子盒子

**解决方案：**

导致如此2个现象的出现是CSS中一个重要特性"FC特性"导致的。当前只要学会进行问题解决就可以"overflow:hidden"和"添加一个div边框"

````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .outer-div1{
            width: 400px;
            height: 400px;
            background-color:aquamarine;
            margin-bottom: 50px;
            /* 可以修改当前父子传递性的代码：BFC容器 */
            overflow: hidden;
            /* padding-top: 20px; */
        }
        .outer-div2{
            width: 400px;
            height: 400px;
            background-color:tomato;
            margin-top: 30px;
        }
        .inner-div{
            width: 200px;
            height: 200px;
            background-color:yellowgreen;
            margin-left: 20px;
            margin-top: 20px;
            
        }
        .abc{
            /*transpaent:透明色*/
            border: 1px solid transparent;
        }
    </style>
</head>
<body>
    <div class="abc">
        <div class="outer-div1">
            <div class="inner-div"></div>
        </div>
    </div>
    <div class="outer-div2"></div>
</body>
</html>
````

## 盒子的标准宽和高

盒子的大小计算是：

- 宽度：width + padding  * 2 + border * 2
- 高度：height + padding *2 + border * 2

占据页面的空间大小：

- 宽度：width + padding * 2 + border * 2 + margin * 2
- 高度：height + padding * 2 + border * 2 + margin * 2



## 怪异盒子结构（IE盒子）

![1591281021692](https://woniumd.oss-cn-hangzhou.aliyuncs.com/web/zhangrui/20210713144504.png)

怪异盒子的width是“**content+padding+border**”

目前主流的浏览器都可以使用怪异盒子

转换代码：

- `box-sizing:border-box` 普通盒子转换为怪异盒子
- `box-sizing:content-box`怪异盒子转回普通盒子（默认）

使用点：

- 如果在页面有盒子是以百分数为高和宽进行这是的。则在加边框时，最好使用怪异盒子（普通盒子需要执行可以采用calc计算）



**拓展**

- width设置为100%和不设置宽度有区别吗
- min-width|min-height是什么意思，怎么设置使用

- css的引入文件的两种方式
  - link
    - 对于网页完成一个css导入操作
  - import
    - 只为当前css进行导入操作

````html
<link rel="stylesheet" href="css文件路径">

<style>
    @import url(css文件路径)
</style>
````

区别：

- link是一个html标签，而import 只是一个css语法
- link不仅仅可以引入css，还可以引入其他文件，而import只能引入css
- 加载时间上，link优于import.
  - link加载时间是和网页同步加载
  - import是需要所有网页完成之后才做的css加载
- 兼容性：link比import好
- 扩展：后期link可以和javascript配合使用，而import不能被js操作

### width100%和不写

在css中如果不写width，则得出的结果是系统自动会按`width:auto`来执行

- 100%值：标准盒子
- auto值：怪异盒子（默认）

1. ### min-width|min-height

   ```css
   .inner{
       width: 50%;
       /* 最小宽度值 */
       min-width: 400px;
       height: 100px;
       background-color: aquamarine;
   }
   ```

   说明：在css中设置min-weight就可以设定当前元素的最小宽度值，一般作用在width为百分数。其目的是为了防止由于浏览器的缩放而破话页面的结构



### 居中

- 文本系元素居中（图片，超链接，纯文本）
  - 水平居中：text-algin:center
  - 垂直居中：line-height:高度值
- 容器系元素居中（table，div）
  - html中：table有一个属性algin，而div（center，table）
  - 水平居中：margin 自动边距设定

说明：原先块级元素会有同一行自动设置margin，使同行没有能放其他元素。现在利用margin完成左右平分，自然会把内容标签挤压到中间。形成居中

块级元素都可以使用margin auto的方式完成居中



15.选择器

# 8.CSS选择器

### 后代选择器

在当前标签（盒子）（html元素）的**所有**子元素都可以称为“后代”

语法

`选择器 子元素{}`

`选择器 子选择器{}`

### 子元素选择器

只寻找**第一级**子元素标签，其他后代不寻找

`父选择器 > 子选择器{}`

### 兄弟选择器

寻找满足条件的标签**后续相邻**的**第一个**标签，用 +

1. `选择器 + 兄弟选择器{}`

2. 寻找当前满足标签的**所有后续**兄弟标签

   ```html
   选择器 ~ 兄弟选择器{}
   ```

## 分组选择器

如果有多个选择器是采用同一组样式的，可以把多组演示合并到一个选择器

1. `选择器1,选择器2,....{}`

## 属性选择器

属性：是指对于html开始标签中的“名称(key)=值(value)”的称呼(key-value)（键值对）

```html
<div class="abc"></div>
<input type="text" value="">
```

| 选择器           | 描述                                                         |
| ---------------- | ------------------------------------------------------------ |
| [属性名]         | 寻找带有此属性的标签                                         |
| [属性名=属性值]  | 寻找带有此属性名=属性值的标签（精确匹配）                    |
| [属性名*=属性值] | 寻找属性值中带有（包含）后面这个内容的完整属性格式（模糊匹配） |
| [属性名~=属性值] | 用于选择器包含指定词汇（必须是单独的一个单词）               |
| [属性名^=属性值] | 寻找指定开头的词汇                                           |
| [属性名$=属性值] | 寻找指定结尾的词汇                                           |

## 伪选择器

### 伪类

- :link
- :visited
- :hover
- :active
- :focus：向键盘进行输入是的标签样式

### 伪元素选择器

- ::first-letter 在找到标签第一个字符完成样式设置
- ::first-line 在找到标签第一行完成样式设置
- ::before 在标签内完成第一个字符前插入内容，并完成样式设置
- ::after 在最后一个字符后插入内容，并完成样式设置

## css继承

在开发语言中CSS可以有继承的概念，是作为父标签的设定直接作用在子标签身上

在css中有自动继承和手动继承两种写法

### 自动继承

- 文本类样式 color.text-algin,line-height
- 字体系：font-size,font…..
- 列表系：list-style,list-style-type….
- 鼠标系：pointer

### 手动继承

使用`inherit`来完成物理上的数值继承

```css
   background-color: inherit;
```

16.浮动

# 9.CSS浮动

## 元素同行显示

块级元素水平放置

- display:inline-block：5像素问题
- table布局
- 浮动

## 浮动

浮动可以让元素在同一行进行显示

语法

```
float: left | right | none
```

left：左漂浮

right：右漂浮

none：不漂浮（默认）

## 文档流

文档流是指HTML在浏览器中的排列形式，默认情况下文档流是指所有元素从上向下，从左向右的进行排列

## 脱离文档流

浮动是把原有的内容从标准文档流中脱离出来，自己形成一个新的排列

![image-20220706112625044](https://woniumd.oss-cn-hangzhou.aliyuncs.com/web/caoshengjie/20220706112625.png)

浮动目的就是为了让我们指定的盒子从标准文档流中脱离开，重新建立的文档流层

说明：

**浮动对于非浮动元素的影响**

浮动元素是脱离文档流的。导致文档流中的后面元素会依次填充脱离后的空位置，如果需要改变或不填充。则可以有多个写法

- 单独写的空白盒子，让其填充
- 设置后面的盒子margion-top来顶开距离

**特殊情况**

如果在文档流中出现文本，则文本是不会重叠到脱离文档流盒子的下面。

![image-20220706115823259](https://woniumd.oss-cn-hangzhou.aliyuncs.com/web/caoshengjie/20220706115823.png)

这种图文混排效果 = 文本不会重叠在浮动元素后 + 文档流中的块级元素会填充脱离文档流元素的位置

## 父元素高度塌陷问题

是指在一个父盒子标签内所有的子元素都漂浮起来了。而父元素又没有设定高度，那么父元素会直接变成一个没有高度的box

## 清除浮动

清除浮动是对非浮动元素因为浮动元素而产生的影响

```css
clear: left | right | both;
```

left左清除

right右清除

both左右清除

17.定位

# 10.CSS定位

position定位

早期定位网页中的各个部分：table

## 元素按照指定位置移动

### margin负值

当margin-top设置负值时，当前的盒子会形成一个特别的状态。状态为“可以悬浮在兄弟元素上，并且还不脱离文档流”，我们称为**“破坏文档流”**

**破坏文档流：**在页面布局过程中，元素在移动过程中不遵循标准文档流的规范，移动完成之后仍然在标准文档流中，只是在移动过程中破坏规则而已。

**破坏文档流是一种特殊的定位形式**

## 标准定位

四种定位方式：

- 静态定位
- 相对定位
- 决定定位
- 固定定位

### 静态定位

标准文档流就是静态定位，按照所有元素的书写顺序，从上向下，从左往右进行排列

```css
position:static
```

### 相对定位

元素参考移动之前的位置，按照指定的方向进行移动

```css
position:relative
```

设定偏移量（运动的方向和长度）

- top：参考原来的位置上边缘进行移动
- left：参考原来的位置左边缘进行移动
- right：参考原来的位置右边缘进行移动
- bottom：参考原来的位置下边缘进行移动

### 相对定位特点

- 设置相对定位的元素，不会脱离文档流，但是会破坏文档流，即可}{以在页面的任何位置显示，但是原始位置依然被保留，后续元素不能占据或填充原始位。
- position设置的相对定位只能完成告知浏览器可以破败文档流，但是还是需要有其他偏移量来支持移动
- 兄弟元素和父子元素都可以完成相对定位的设置。设置为相对定位的元素是可以移动到父元素的外面去的，但是父元素在没有高度的情况下不会坍塌，这就是一个和浮动子元素的最大的区别

### 绝对定位

绝对定位不用与相对定位在于：绝对定位是**脱离文档流**

```css
position:absolute;
```

和相对定位一致，有四个偏移量：top,left,right,bottom

#### 特点

决定定位是按浏览器的左上角点为原点进行显示（相对定位是按原始位置左上角点进行显示）

和相对定位一致，有四个偏移量：top,left,right,bottom

#### 特点

决定定位是按浏览器的左上角点为原点进行显示（相对定位是按原始位置左上角点进行显示）

### 经典设置方式

 在出现父子关系的元素中。我们改变子元素的参考坐标点为父元素的位置。需要执行一下2步操作

1. 设置父元素的定位方式为相对定位
2. 设置子元素的定位方式为绝对定位

完成以上两部后，子元素就会自动完成对应原点为父元素左上角点，我们通常把这种写法称为**“父相子绝”**

父相子绝是改变了当前页面中定位偏移量（left，top，bottom，right）值的参照点，父相子绝的参照点是**父元素的边界。**

- 纯相对定位：参照点是自身位置
- 纯绝对定位：参照点是浏览器边界

父相子绝的子元素依然是脱离文档流的



说明：

使用父相子绝可以给出浮动不能完成的精确定位，同时定位后的元素依然可以根据页面的大小和调整完成动态额变化

### 固定定位



将一个容器固定在浏览器的一个边缘，固定后的容器不会随着滚抽而滚动

```css
position:fixed;
```

偏移量：top、left、right、bottom

#### 特点

固定定位的容器会脱离文档流，所以原来的空间位置不再占据

#### 应用场景

- 头部导航，类似QQ官网
- 左右门神
- 网页底部小广告

说明：设置为固定定位的容器会在浏览器的指定位置固定停留，不会滚动。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        body{
            border: 1px solid red;
            height: 1000px;
        }
        .box1{
            width: 100px;
            height: 100px;
            background-color: pink;
            position: fixed;
            right: 0;
            bottom: 0;
        }
        .box2{
            width: 200px;
            height: 200px;
            background-color: tomato;
        }
    </style>
</head>
<body>
    <div class="box1">box1</div>
    <div class="box2">box2</div>
</body>
</html>
```

![image-20220707151149878](https://woniumd.oss-cn-hangzhou.aliyuncs.com/web/caoshengjie/20220707151150.png)

#### 固定导航

说明：`margin-top: 80px;`此句代码设置的目的是，固定定位会脱离文档流导致会有部分后续内容的遮挡

18.FC

# 11.FC

## 概念

Formating Context 格式化上下文，它是CSS2.x规范中提出一个**视觉渲染概念**

它页面中一块渲染区域，并且有一套渲染规则，它可以决定其子元素如何排列以及和其他元素之间的关系

## FC的分类

- BFC
- IFC

## BFC

Block Formating Context(块级格式上下文)，它是页面的一个块级区域，可以决定元素的排列

翻译成中文：

- 标准文档流就是一个标准的BFC容器
- 盒子垂直方向的距离由margin决定，如果有两个盒子在一个BFC容器中，他两的垂直方向会产生重叠
  - 只要让上下两个div不在一个BFC容器中就可以
- BFC区域不会与float重叠
- BFC容器是独立的，不会和其他容器重叠
- 计算BFC区域的高度时，浮动元素有参与计算

如何成为BFC容器

- 根元素就是一个BFC
- flot不为none
- position为absolute和fixed
- display为inline-block或flex
- overflow不为visible 经常用:hidden

## BFC应用场景

### 左右放置，中间div自由宽度设置

````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        body{
            margin: 0;
        }
        .container{
            height: 200px;
            border: 1px solid red;
        }
        .left{
            width: 200px;
            height: 100%;
            background-color: pink;
            float: left;
        }
        .right{
            width: 200px;
            height: 100%;
            background-color: yellowgreen;
            float: right;
        }
        .center{
            /* width: calc(100% - 400px); */
            height: 100%;
            background-color: tomato;
            /* float: left; */
            /* BFC容器转换 */
            overflow: hidden;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="left"></div>
        <div class="right"></div>
        <div class="center"></div>
    </div>
</body>
</html>
````

![image-20220708104127443](https://woniumd.oss-cn-hangzhou.aliyuncs.com/web/caoshengjie/20220708104127.png)

### 父元素塌陷效果的处理

````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .container{
            border: 1px solid red;
            /* 转bfc */
            overflow: hidden;
        }
        .item{
            width: 200px;
            height: 200px;
            border: 1px solid green;
            float: left;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="item"></div>
        <div class="item"></div>
        <div class="item"></div>
        <div class="item"></div>
    </div>
</body>
</html>

````

![image-20220708104516163](https://woniumd.oss-cn-hangzhou.aliyuncs.com/web/caoshengjie/20220708104516.png)

将没有高度的父元素，设置overflow:hidden就可以转变为BFC容器，就可以计算高度时带上浮动元素

### 元素重叠性处理

````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .box1{
            width: 200px;
            height: 200px;
            background-color: pink;
            margin-bottom: 50px;
        }
        .box2{
            width: 200px;
            height: 200px;
            background-color: tomato;
            margin-top: 100px;
        }
        .container{
            overflow: hidden;
        }
    </style>
</head>
<body>
    <div class="box1"></div>
    <div class="container">
        <div class="box2"></div>
    </div>
</body>
</html>
````

![，](https://woniumd.oss-cn-hangzhou.aliyuncs.com/web/caoshengjie/20220708105349.png)

说明，只要在两个div中间增加一个div，使他们不在一个BFC容器中，并把增加的div设置为BFC容器就可以解决重叠问题

## IFC

Inline Formating Context（行内格式化上下文），所有行级元素的操作

**前期复习**

块级元素

- 独占行
- 可以设高宽
- 盒子模型都可以设置

行级元素

- 不独占行
- 不可以设置高宽
- 可以设置margin和padding的水平方向

![image-20210719112922692](https://woniumd.oss-cn-hangzhou.aliyuncs.com/web/zhangrui/20210719112922.png)

绿色：顶线

蓝色：中心

红色：基线（默认）

紫色：底线

## 影响IFC布局高低因素

- font-size

- font-family

- height | line-height

  line-height是指底线到底线之间的距离，顶线到底线之间距离

![image-20210719114155031](https://woniumd.oss-cn-hangzhou.aliyuncs.com/web/zhangrui/20210719114155.png)

- **vertical-align**

设置行级元素的垂直高度，可以通过此值改变当前元素的对齐线

## 案例

文本和文本之间的对齐方式

````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .container{
            border: 1px solid red;
        }
        span{
            font-size:40px;
        }
        .span1{
            vertical-align: middle;
        }
        .span2{
            font-size: 80px;
            vertical-align: bottom;
        }
    </style>
</head>
<body>
    <div class="container">
        <span class="span1">40px</span>
        <span class="span2">80px</span>
    </div>
</body>
</html>
````

![image-20220708113417181](https://woniumd.oss-cn-hangzhou.aliyuncs.com/web/caoshengjie/20220708113417.png)

**图片和文本同行显示**

````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .container{
            border: 1px solid red;
        }
        span{
            font-size: 80px;
            vertical-align: middle;
        }
        .container img{
            vertical-align: middle;
        }
    </style>
</head>
<body>
    <div class="container">
        <img src="./img/img-4.jpg" alt="">
        <span>80px</span>
    </div>
</body>
</html>
````

![image-20220708114514804](https://woniumd.oss-cn-hangzhou.aliyuncs.com/web/caoshengjie/20220708114514.png)

说明：图片和文本一样，都是可以通过设置vertical-align来改变对齐方式



# 12.overflow补充

````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .outer{
            width: 300px;
            height: 200px;
            background-color: pink;
            overflow:visible;
        }
        .inner{
            width: 200px;
            height: 400px;
            background-color: tomato;
        }
    </style>
</head>
<body>
    <div class="outer">
        <div class="inner"></div>
    </div>
</body>
</html>
````

overflow是作为父元素的一个溢出设置，代表当子元素的宽高超过父元素时，父元素的处理方式

- visible 可见（默认）
- hidden 隐藏
- scroll 滚动

21.CSS兼容

# (历史的眼泪)CSS兼容

## 兼容性问题来源

浏览器中最核心的东西是“内核”，决定浏览器解决代码的能力和识别度（网页如何加载）

不同浏览器会有“略微”不同的内核，每个浏览器对代码都会有不同的解析，导致最终的结果会不一样，这样就出现了兼容性的解决。

统一相同网页在不同浏览器上呈现一样的效果。我们称为兼容

## 浏览器内核

目前主流自主研发内核的浏览器：chrome,firefox,opera,360

经常使用：ie,safira

国产浏览器：猎豹、360、qq、搜狗、UC

内核做的事情

- HTML解析
- css解析翻译
- javascript解析翻译

**内核的具体操作步骤**

1. 内核会先对html代码进行拆分，并组成一个HTML文档树，每个树的树枝（节点）会是html对应标签
2. 将css标签都直接挂载到对应的html节点位置
3. 渲染页面

![image-20220708165934705](https://woniumd.oss-cn-hangzhou.aliyuncs.com/web/caoshengjie/20220708165934.png)

## 兼容性问题处理

针对IE浏览器

CSS hack代码操作

我们需要使用特点软件来完成ie调试，IETest

### 调试方式

**属性前缀法**

在所有css属性名追加一个特殊符号，来完成不同浏览器的操作

|    hack    |                写法                 | 实例 | IE6 (S) | IE6 (Q) | IE7 (S) | IE7 (Q) | IE8 (S) | IE8 (Q) | IE9 (S) | IE9 (Q) | IE10 (S) | IE10 (Q) |
| :--------: | :---------------------------------: | :--: | :-----: | :-----: | :-----: | :-----: | :-----: | :-----: | :-----: | :-----: | :------: | :------: |
|     *      |               *color                | 青色 |    Y    |    Y    |    Y    |    Y    |    N    |    Y    |    N    |    Y    |    N     |    Y     |
|     +      |               +color                | 绿色 |    Y    |    Y    |    Y    |    Y    |    N    |    Y    |    N    |    Y    |    N     |    Y     |
|     -      |               -color                | 黄色 |    Y    |    Y    |    N    |    N    |    N    |    N    |    N    |    N    |    N     |    N     |
|     _      |               _color                | 蓝色 |    Y    |    Y    |    N    |    Y    |    N    |    Y    |    N    |    Y    |    N     |    N     |
|     #      |               #color                | 紫色 |    Y    |    Y    |    Y    |    Y    |    N    |    Y    |    N    |    Y    |    N     |    Y     |
|     \0     |             color:red\0             | 红色 |    N    |    N    |    N    |    N    |    Y    |    N    |    Y    |    N    |    Y     |    N     |
|    \9\0    |            color:red\9\0            | 粉色 |    N    |    N    |    N    |    N    |    N    |    N    |    Y    |    N    |    Y     |    N     |
| !important | color:blue !important; color:green; | 棕色 |    N    |    N    |    Y    |    N    |    Y    |    N    |    Y    |    N    |    Y     |    Y     |

**选择器前缀法**

|                      语法                      | IE6  | IE7  | IE8  | IE9  | IE10 |
| :--------------------------------------------: | :--: | :--: | :--: | :--: | :--: |
|                     *html*                     |  √   |  ×   |  ×   |  ×   |  ×   |
|                    *+html*+                    |  ×   |  √   |  ×   |  ×   |  ×   |
| [@media](https://github.com/media) screen\9{…} |  √   |  √   |  ×   |  ×   |  ×   |
| [@media](https://github.com/media) \0screen{…} |  ×   |  ×   |  √   |  ×   |  ×   |

**条件注释法**

通过HTML注释的写法来完成样式的版本切换

- gte 大于等于
- gt 大于
- lte 小于等于
- lt 小于
- ！ 否

````html
只在IE下生效
<!--[if IE]>
这段文字只在IE浏览器显示
<![endif]-->
只在IE6下生效
<!--[if IE 6]>
这段文字只在IE6浏览器显示
<![endif]-->
只在IE6以上版本生效
<!--[if gte IE 6]>
这段文字只在IE6以上(包括)版本IE浏览器显示
<![endif]-->
只在IE8上不生效
<!--[if ! IE 8]>
这段文字在非IE8浏览器显示
<![endif]-->
非IE浏览器生效
<!--[if !IE]>
这段文字只在非IE浏览器显示
<![endif]-->
````

## 当今浏览器的兼容设置

- 1、-moz代表firefox浏览器私有属性
- 2、-ms代表ie浏览器私有属性
- 3、-webkit代表safari、chrome私有属性

当年IE调试

````css

*div*{
    width:798px;
    height:100px;
    border:1px solid red;
}
*+div*+{
    width:800px;
    height:100px;
    border:1px solid red;
}
IE6  标准盒子
IE7  怪异盒子
无论哪个浏览器都保证div  width:800
````


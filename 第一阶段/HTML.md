# HTML

````html
  <meta name="description" content="这是我的web页面，web前端">
  <meta name="keywords" content="蜗牛学院，web前端">
````

说明：keywords:关键字，利用给到搜索引擎

Description：网页描述

单标签在当今的浏览器下都可以不打最后/，因为浏览器会自动识别

### 添加注释

用来给开发者做编写记录的内容。但是不会给浏览器进行解析

<!--  -->

全文解释

````html
<!-- 兼容模式 -->
<!DOCTYPE html>
<!-- lang告知浏览器，以下的代码使用en书写 -->
<html lang="en">
<head>
    <!-- 统一浏览器的解码字符集 -->
    <meta charset="UTF-8">
    <!-- IE浏览器兼容模式 -->
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <!-- 移动端时，移动设备优先 -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
</body>
</html>
````

### 换行符

```
<br/>
```

注意：如果在vscode中打回车，则会在浏览器中显示为半角的一个空格

### 加粗设置

```
<strong></storng>
<b></b>
```

### 斜体字

```
<em></em>
<i></i>
```

### 分割线

```
<hr/>
```



### 超链接

**超链接的跳转位置**

`target`增加这个属性

_blank:跳转到新网页

_self:在本页面跳转

**补充**

在超链接href中有时会输出路径的寻找写法

在寻址的时候，会有路径选择符（. 和 ..）

. 代表当前文档路径

.. 代表上一级文档路径

### 网页空格

默认网页连续输入多个半角空格只认一个

如果需要多个空格连续出现，则需要输入*转义符

其他的转义符

```html
&nbsp;空格
> &gt;
< &lt;
```

### 锚点

超链接在跳转的时候，指定位置的跳转，如返回顶部

```
<a href="#">返回顶部</a>
```

**注意：**页面需要有滚轴，即一屏无法直接呈现所有内容

定义描点`#+id文本`

```
 <a href="#shanghaiNews">上海新闻</a>&nbsp;<a href="#guojiNews">国际新闻</a>
```

在跳转的位置写上id

```
<h1 id="shanghaiNews">上海新闻</h1>.....<h2 id="guojiNews">国际信息</h2>
```

完成，之后在点击超链接（锚点）时，可以完成跳转到id位置



锚点还可以指定不同页面之间的位置跳转

```
<a href="./热门电视剧/西游记.html#3" target="_blank">西游记第3集</a>
```

说明：在跳转时带上#锚点，并且在新页面完成id的指定

```
<p id="3">        <h3>第3集</h3>        1982年—1985年拍完前十一集。1984年2月3日播出了《计收猪八戒》、《三打白骨精》两集。1986年春节期间播出前十一集。    </p>
```

当点击超链接时，会调整到指定页面的指定id位置。



### 表格

**表格的属性**

表格是可以在table,tr,td上分别设置不同的属性

table:

- border:设置表格的边框
- width：设置表格的宽度
- height：设置表格的高度
- align：设置表格的页面对齐模式（left center right）
- bgcolor：设置表格的背景颜色



### 合并单元格

表格的合并有两种方式

- 合并行：rowspan 跨行合并单元格，垂直方向上的合并
- 合并列：colspan 跨列合并单元格，水平方向进行合并

**总结：**

1. 在代码中找到需要操作的td
2. 在最早/最前的代码开始标签内添加rowspan/colspan，并设置需要合并的行/列数值
3. 从本身出发
   1. rowspan删除临近的tr中的td
   2. colspan删除当前本身的tr中的td



## 表单

网络上的用户交互动作都可以通过表单的形式完成，如，登录、注册、投票，提问，留言

### 表单控件

```
<form></form>
```

### 输入框

```
<input type="text" placeholder="请输入用户名" value="tom">
```

说明：

- type：类型，说明输入框的填写内容 text表示文本
- placeholder：灰色提示文本，不占据页面空间
- value：初始化的文本，会占据空间位

### 密码框

```
<input type="password" placeholder="请输入密码" value="">
```

说明：密码框是在呈现的时候自动会把填写的内容改变成一个点

![image-20220630121801519](https://woniumd.oss-cn-hangzhou.aliyuncs.com/web/caoshengjie/20220630121801.png)

### 单选框

只能在一组选项中选择一个值

```
<input type="radio">
```

注意：单选框需要做唯一性选择时，需要起相同的名字代表一个组

```
<input type="radio" name="gender">男&nbsp;<input type="radio" name="gender">女
```

name没有限制起什么内容。只是需要对应当前的选项

如果我们需要鼠标点击提示文本就可以选择单选按钮，则就要添加标签`label`

```
<input type="radio" name="gender" id="female"><label for="female">女</label>
```

说明：在提示文本单击时，html编译器寻找符合for定义内容的id标签，然后传递单击操作

如果需要默认值的选择，可以使用`checked`属性

```
<input type="radio" name="gender" id="male" checked="checked"><label for="male">男</label>
```

注意：可以省略只写一个`checked`

### 复选框

和单选框不同的区别是：可以在一个组中多项选择

```
<input type="checkbox" name="hobby" id="" checked>打游戏
```

其他设置和单选框一致

### 下拉列表框

```
<select name="" id="">    <option value="">上海</option>    <option value="" selected>北京</option>    <option value="">深圳</option></select>
```

![image-20220630143548298](https://woniumd.oss-cn-hangzhou.aliyuncs.com/web/caoshengjie/20220630143548.png)

说明：默认选中项为selected=”selected”

### 列表框

```
<select name="" id="" multiple>            <option value="">上海</option>            <option value="">北京</option>            <option value="">深圳</option></select>
```

![image-20220630143952653](https://woniumd.oss-cn-hangzhou.aliyuncs.com/web/caoshengjie/20220630143952.png)

说明：在下拉列表框的开始标签上添加属性`multiple`可以让所有选项全部显示出来，可以多选

### 文本域

可以在网页中多行输入的输入框

```
<textarea name="" id="" cols="30" rows="2"></textarea>
```

### 按钮

```
<input type="submit" value="注册">&nbsp;<input type="reset"
```

说明：在表单内部有两个基本按钮

submit：提交按钮，把所有表单填写数据进行向服务器的提交

reset：重置按钮，是把所有表单回滚到未填写状态

**submit提交操作**

```
<form action="">
```

action是submit提交按钮的服务器地址，要填写后端提供的服务器表单接受网址

所有表单元素都需要添加一个name属性

```
<input type="password" placeholder="请输入密码" value="" name="pass"><select name="city" id="">    <option value="">上海</option>    <option value="" selected>北京</option>    <option value="">深圳</option></select>
```

只有将有name属性的表单元素才能进行提交

**提交模式**

```
<form actoin="服务器提交地址" method="get/post">
```

get/post二选一

get：明文提交。内容会在地址栏后拼接

post：安全提交。不会显示

**说明：**这个提交会在后期详细讲解，需要和服务器结合



**html其他按钮**

```
<input type="button"><input type="button" value="普通按钮" onclick="alert('hello')">
```

说明：input-button就是一个普通按钮，是可以给到js脚本语句进行操作。本身没有任何的功能

**注意：**如果把input-button放在form表单标签中间。则这个按钮会自动变成submit按钮

## 其他标签

### iframe

网页嵌套标签，可以在一个网页中嵌套另一个网页

```
<iframe src="./01.table布局.html" frameborder="0" width="1500" height="2500"></iframe>
```

可以在当前页面完成另一个页面的显示，可以设定width和height来完成具体嵌套位置大小，也可以通过frameborder来完成是否需要边框，0是无边框

![image-20220630160457195](https://woniumd.oss-cn-hangzhou.aliyuncs.com/web/caoshengjie/20220630160457.png)

说明：嵌套在iframe网页中的另一个页面

**嵌套页面的跳转**

- 如果嵌套页面只想在iframe内部进行跳转。则直接写入target=”_self”或者不写
- 如果希望通过父页面进行跳转，则超链接需要写target=”_parent”

**外部显示在iframe中**

```html
 <a href="./01.table布局.html" target="content">table布局学习</a>
    <a href="./03.table合并.html" target="content">table合并</a>
    <iframe src="" name="content" frameborder="0" width="1500" height="850"></iframe>
```

说明：在超链接a后面添加一个target指向iframe的name，则超链接的跳转页面会显示在iframe中



### fieldset

带边框的容器container，独占一行

```html
<table width="500">
        <tr>
            <td>1</td>
            <td>
                <fieldset>
                    <legend>用户注册</legend>
                    <form action="">
                        用户名：<input type="text">
                        密码：<input type="password">
                    </form>
                </fieldset>
            </td>
        </tr>
    </table>
```

![image-20220630170942331](https://woniumd.oss-cn-hangzhou.aliyuncs.com/web/caoshengjie/20220630170942.png)

**html标签分类**

- **块级标签** 独占行：h1-h6,div,ul-li,ol-li,marquee,table
- **行级标签** 不独占行：img,a,font,input,select,button,span,

HTML5

# HTML5

## 简介

HTML5.0版本，2015年发布后是增加或迭代了部分HTML4.0功能

### 发展源

- 移动互联网的飞速发展
- 对之前HTML的革新

HTML5增加一些特别针对移动端的标签

### 邮箱输入框

提供用户完成邮箱格式的验证输入

````html
<input type="email">
````

### 其他表单元素的新增控件

````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <h3>邮箱输入框（移动端有效）</h3>
    <input type="email" name="email" disabled value="123@153.com"/>
    <h3>数字输入框</h3>
    <input type="number">
    <h3>颜色颜色</h3>
    <input type="color">
    <h3>网址(统一资源定位符)输入框</h3>
    <input type="url">
    <h3>取值范围</h3>
    <input type="range">
    <h3>搜索框</h3>
    <!-- 输入内容后，提供清空输入框的控件 -->
    <input type="search">
    <h3>文件上传(获取内容)</h3>
    <input type="file">
    <h2>日期控件</h2>
    <h3>选择年月日</h3>
    <input type="date">
    <h3>选择某年某月</h3>
    <input type="month">
    <h3>选择某年的第几周</h3>
    <input type="week">
    <h3>选择时间</h3>
    <input type="time">
    <h3>选取列表</h3>
    <input type="text" list="lists">
    <datalist id="lists">
        <option value="小猪">小猪</option>
        <option value="小猪佩奇">小猪佩奇</option>
        <option value="小猪乔治">小猪乔治</option>
        <option value="小米手机">小米手机</option>
    </datalist>
</body>
</html>
````

注意：HTML5是否可以在PC端的浏览器呈现效果。全看浏览器的内核

### 音频

原始在HTML4.0的时候加载一个音频需要比较复杂

HTML5.0进行了新标签的出现

````html
    <!-- 
        src：音频源
        controls：音频控件
        muted：静音播放
        autoplay：自动播放
        loop: 循环播放
     -->
    <audio src="./file/music.mp3" controls muted autoplay loop></audio>
````

### 视频

````html
<video src="./file/play.mp4" controls></video>
````

### 多文件的播放

在视频和音频过过程中是可以作为开始和结束标签中间元素方式播放

````html
<audio controls>
    <!-- 用于连接多媒体资源 -->
    <source src="file/music.mp3">
    <source src="file/music.ogg">
</audio>
<video controls loop autoplay>
    <source src="file/test.MP4" > 
</video>
````

注意：网络播放器的视频播放是需要视频流技术，而这个技术是需要服务器支持。我们的html5播放器在显示生活中可以完成一些小工艺片或公司宣传片的在线播放



## 语义化标签

见标签，知其意

### 语义化标签好处

1. 方便我们阅读代码，即使没有样式我们都可以非常清晰的知道页面的排版布局
2. 有利于SEO（搜索引擎优化）的操作
3. 语义化标签更有利于特殊浏览器的解析，盲人浏览器
4. 有利于后期代码的维护和二次开发

### 语义化标签

| 标签名      | 描述                                             |
| ----------- | ------------------------------------------------ |
| `<header>`  | 代表网页的头部                                   |
| `<main>`    | 网页的主体部分，内容区域，页面上有且仅有一个标签 |
| `<nav>`     | 代表导航                                         |
| `<footer>`  | 代表网页的尾部                                   |
| `<aside>`   | 代表侧边栏                                       |
| `<article>` | 代表网页中一个独立区域，一般方内容               |
| `<section>` | 代表网页中一个模块，理解为平时的div              |
| `<audio>`   | 音频                                             |
| `<video>`   | 视频                                             |
| `<source>`  | 资源标签，用于连接多媒体资源                     |
| `<thead>`   | 表格的头部                                       |
| `<tbody>`   | 表格的内容                                       |
| `<tfoot>`   | 表格的尾部                                       |
| `<canvas>`  | 定义图形                                         |

注意：语义化标签只是在识别上更容易判断和理解页面结构，同时也更方便搜索引擎的收录，但是在书写排版上还是需要样式css来进行布局。
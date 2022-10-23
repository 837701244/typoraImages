# Javascript

## Javascript(JS)发展史

1995-JS1.0 网景javscript1.1 ECMA 发布全球JS规范标准 ECMAScript

1999 ECMAscript 3.0发布，互联网第一个JS版本

2009 ECMAscript5.0，中国第一个普及版本-js版本

2015 ECMAscript2015（ES5）

从2015开始后续每年发布一个新版本，统称（ES6）

**兼容问题**

ES5，全系兼容

ES6，谷歌和火狐版本>2015，同时IE全系不支持ES6（IE6-IE11）,只有IE革新版（edge-IE12）才支持

03.Javascript数据类型

## 1.1 JS数据类型

不同的数据会有不同的数据类型

在JS中数据类型统称分为两种

- 基本数据类型
- 引用数据类型

### 基本数据类型

#### number

数字类型：123，-123，12.345，-12.456

typeof()：是用来查看变量类型的操作

浏览器返回的是number

所有数值都是包括整数与浮点数

Infinity：正无穷

NaN：not a number 不是 一个数字

小数运算不能保证精确

#### String

字符串，用来表示文本：”张三” , “123” , ‘abc’

\是转义\后的就无意义

\n是换行

\t是制表符

两\是一个\

字符串在书写时是需要引号，单引号和双引号都可以

![image-20220725144817510](https://woniumd.oss-cn-hangzhou.aliyuncs.com/web/caoshengjie/20220725144817.png)

如果没有打引号，JS会自主进行代码理解

![image-20220725145019244](https://woniumd.oss-cn-hangzhou.aliyuncs.com/web/caoshengjie/20220725145019.png)

如果19没有打引号，则会理解为数字。

如果“zhangsan”没有打引号，则JS会把zhangsan作为变量处理，同时在赋值号= 右边的变量是直接使用的，而非会进行隐式定义。所以系统会报zhangsan没有定义的错误

#### Boolean（bool）

布尔值，逻辑值（是非值）

数据只有两种形式（真，假）

- true(真)，false（假）
- 对、错
- 1，0
- yes，no

NULL：无变量（这个变量没有定义）

undefined：有变量，无内容（这个变量定义了，但没有存放数据）



#### **Null:空值**

表示一个空对象

只有null

用typeof检查null时会显示object



#### **Undefind：未定义**

当声明一个变量，但不给赋值时就是这个

只有一个undefined



### 引用数据类型

- 数组
- 对象

## 1.2数据类型的转换

数据类型转换分为

- 自动转换
- 手动转换

**自动转换**

- 字符串在做 - * / 时，字符串会自动转换为数字类型number

**手动转换**

#### **字符串转为数字**

`Number（）`

```js
var 变量名 = Number(要转换的变量);
var num1 = Number("10");
console.log(num1);//10
console.log(typeof(num1));//number
```

````js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script>
        // var num1 = 10;
        // var num2 = 12.45;
        // var pi = 3.141592654;
        // console.log(typeof(num1));
        // var 张三 = 'tom';
        // var user_name = 张三;
        // var user_age = "19";
        // console.log(user_name,user_age);
        // var str = "100";
        // console.log(typeof(str));//String字符串
        // // 转换
        // var num = Number(str);
        // console.log(num,typeof(num));
        //boolean
        var bool1 = true;//真
        var new_bool = Number(bool1);
        console.log(new_bool ,typeof(new_bool));//1 number
        var bool2 = false;//假
        var new_bool2 = Number(bool2);
        console.log(new_bool2 ,typeof(new_bool2));//0 number
        var new_bool3 = Number("我们");
        console.log(new_bool3 ,typeof(new_bool3));//NaN number  不是数字
    </script>
</head>
<body>
</body>
</html>
````

说明：

数字字符直接转换。

布尔值真转1，假转0。

非数字字符串：NaN 不是数字



`parseInt（）`

整数转换，将一个字符串转换为整数，不保留小数，如果不是数字会输出NaN

**保留整数是截取整数，而非四舍五入**



`parseFloat()`

转换为浮点数

特别注意：bool类型无法转换为小数的

````js
var 变量名 = parseFloat(需要转换的字符串)
var num1 = parseFloat("123");//123
var num2 = parseFloat("-45.67");//-45.67
var num3 = parseFloat('abc');//NaN

var bool1 = false;//假
var new_bool = parseFloat(bool1);
console.log(new_bool);//NaN
````

#### 数字转字符串

`toString`

````js
var 变量 = 数字.toString();
var num = 100;
var str = num.toString(); // "100"
````



**指定小数的保留位数**

`toFixed`会四舍五入

````js
var 变量 = 数字.toFixed(小数的位数);
var num = 1.689;
var new_num = num.toFixed(1);
document.write(new_num);//1.7
````

#### 另一种转换方式

**转String**

方法一：调用被转换数据类型的.toString()方法

不会影响到原变量

null、undefined不能转换



方法二：调用String()函数

将被转换的数据作为参数传递给函数



方法三：直接加“”



**转Nubmer**

方法一：使用Number()函数

字符串将  非数字转换成NaN,空字符串为0

true是1，false是0

null是0

undefined是NaN



方法二：专门对付字符串

parseInt()：转换成整数

用逗号隔开第二个可以放想要转换进制的数字

可以将一个字符串中有效的整数取出来

parseFloat()：转换成小数(浮点数)



16进制0x开头

8进制是0开头

2进制是0b开头（但不是所有浏览器生效）



**转Boolean**

使用Boolean（）函数

数字转除了0与Nan都是true

字符串 除了空串其余都是true

null与underfined都是false

对象也会true

## 1.3 运算符（操作符）

### 分类

- 算术运算符
- 赋值运算符
- 关系运算符（比较运算符）
- 逻辑运算符
- 位运算符

### 算术运算符

- +
- \-
- *
- /
- %

`+`和`-`处理

### 赋值运算符

= 将右边的值存入左边的变量

**+=，-=，\*= ，/=** 自增符



**++在前和++在后的区别**

当++参与算术运算时。

- ++在前，先累加再运算
- ++在后，先运算再累加

### 关系运算符

也称比较运算符

```js
> < >= <= == === != !==
```

说明：返回的结果是一个boolean类型，true为真，false为假



`==` 与`===`相等

==：比较两个数字的值是否相等，相等返回true，不相等返回false

===：比较两个数字的值以及两个变量的类型，如果值和类型都相等返回true，否则返回false

说明：`==`和`===`是不相等的

同理





!= 和!==区别 都是不相等

!-=:**只比较值**

!==:**比较值和类型**

字母、数字都可以进行比较。其原理是所有在计算机中的比较并不是按照现实生活中的人为认知来比较。而是根据每个数字和字母在计算机中的编码顺序来进行比较（ASCII）

| 字母 | 数字 |
| ---- | ---- |
| a    | 97   |
| A    | 65   |
| 0    | 48   |

**特别说明：**我们不做汉字的比较

### 逻辑运算符

当有多条件判断时的（并且、或者、否），在英文（and,or,not）

#### 并且（and与）

&&**全真则真**



#### 或（or）

`||`:**有真则真**

#### 取反（非not）

`!`:**真亦假来，假亦真**

#### 位运算

位运算是指内存的二进制运算，即二进制的（与或非）

#### **总结**

所有运算符都是可以混合在一起在表达式中使用

优先级为，算术>比较>逻辑(小括号除外)>赋值

算术：乘除大于加减

逻辑：非>与>或

## 1.4模板字符串

### 模板字符串（ES6）

语法：反引号+$

### 模板字符串中的表达式

````js
//可以在模板字符串中写表达式
document.write(`您好，您的名字是：${studentName}，明年的年龄是：${studentAge + 1}，性别为：${studentGender}`);
````

## 1.5.控制结构

### 概念

程序的执行时从上往下的直序运行，我们希望程序在运行过程中有一定的代码运行控制，我们就需要有控制结构语句

**控制语句的分类**

- 分支语句
- 循环语句

### if（如果）

````js
if(判断条件){
   条件判断后的执行脚本
}
````

判断条件一定的返回值是一个bool类型

if语句判断条件为true，则执行{}里的代码

if语句判断条件为false，则不执行{}里的代码



说明：isNaN是用来判断变量是否为NaN，如果是则返回true，不是返回假false



### **if…else…**如果…..否则…..

````js
if(判断条件){
    条件为ture
    执行的代码
}else{
    条件为false
    执行的代码
}
````

### **if…else…嵌套**

可以在页面中完成if…else…语句的嵌套

### **if…else if ….else….**

说明：if…else if….在大部分情况下可以代替if嵌套，而两种的区别在于if嵌套可以自定义在else语句中完成代码，而不用考虑if结构。

### switch

如果判断不是区间，或者判读的是字符串，可以使用switch

````js
switch(判断变量){
    case 判断值1:
        执行语句1
        break;
    case 判断值2:
        执行语句2
        break;
    case 判断值3:
        执行语句3
        break;
    default:
        默认执行语句
        break;
}
````

说明：switch只能判断固定值，而非区间，比如：变量等于张三，分数等于60，而不能是分数在60至70分之间的范围

break：终止当前switch的使用，并跳出switch然后执行后续代码，如果没有break则在执行完成case语句后会继续向下执行

### 三目运算写法

主要能够缩减if…else的格式

`条件判断? true的代码 : false代码`

三目运算时if..else的简写形式

注意：三目运算时只能简化代码的书写。如果在if语句有很多复杂逻辑。则还是需要用if



## 1.6随机操作

让JS代码自动完成一个随机数的显示

```js
var num = Math.random();
```

Math.random()会生成一个随机数，随机数的范围在0-1之间，含0不到1

````js
Math.random()会生成一个随机数，随机数的范围在0-1之间，含0不到1

 var num = Math.random();//[0-1)
//取1-10之间的随机数
// 方法1
// var result1 = parseInt(num * 10) + 1;  //0-0.9999
// 方法2
//var result1 = parseInt(num * 10 + 1);
//获取0-10的数字
var result1 = (num * 10).toFixed(0);
document.write(result1);

````

就是 Math.random()*（最大值-最小值）+最小值;



## 1.7循环

### 概念

循环就是对一定可重复的代码进行反复执行

### 分类

- for
- while
- do…while

### for

是指多数运用于有知道循环次数的操作

````js
for(初始值;结束条件;循环自增/自减值){
    循环体
}
````

### 终止循环和跳过循环

break：终止当前循环的后续运行

continue：跳过本次循环，继续后续循环

### for循环嵌套

**纯嵌套**

说明：纯嵌套是完成两个独立循环的嵌套写法。内循环执行的次数和循环没有关联

**关联嵌套循环**

说明：关联循环的循环中的条件会出现外循环的循环变量

### While(当)

while循环和for循环是在语义上相同，只是while更多的是用在位置循环次数的情况下

```js
while(循环判断条件){
    循环体
}
```

说明：当循环条件为true，继续进行循环体执行，当循环条件为false时，终止while循环体执行，同时继续执行while后续代码

### do…while

do…while和while都可以解释当，只是两者在书写结构上和条件判断值上有一些区别

```js
do{
   循环体 
}while(循环判断条件)
```

和while的区别

- while的最少执行次数为：0次，即由于判断语句为false，导致一次都不做
- do…while最少执行1次

### 说明点

**break**

1.终止循环，如果在嵌套循环的内循环，break只能跳出（终止当前循环语句）-内循环

2.break只完成对循环的终止，与分支条件没有任何关联



## 1.8数组

### 概念

数组是一种引用数据类型，可以利用数组在程序运行内存中连续存储多个变量



变量在数组中有一个唯一的编号代表其位置：编号称为（**数组下标/数组索引**）



**数组下标：从0开始的**



普通变量是完成单个存储值的获取和存储

数组是一个连续空间的数据存储，并且在取数组内容时，需要数组名和下标同时写上

### 定义数组

````js
//定义变量
var name;
//定义空数组
var 数组名 = [];//方式一
var 数组名 = new Array();//方式二
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <script>
        //定义数组
        var rujia = [];
        var jingjiang = new Array();
        //给数组赋值
        rujia[0] = 'tom';
        //从数组中取值
        document.write(rujia[0]);
        rujia[1] = "mary";
        document.write("<br>");
        document.write(rujia[1]);
    </script>
</body>
</html>
````

说明：数组取值和存储（赋值）都是需要通过下标（索引）来完成，每个索引所代表为位置中的数据是相互独立的，不会相互影响

### **数组的长度**

数组名.length

### 创建数组和赋值同时完成

````js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <script>
        /*
            数组练习：实现简易的物流管理
        */
       //设定快读公司
       var bag1 = '顺丰';
       var bag2 = '圆通';
       var bag3 = '中通';
       var bag4 = '申通';
       var bag5 = '韵达';
       //存储到系统数组中
       var bagsArray = [bag1,bag2];
       //查看系统中快递公司的数量
       console.log('快递公司的总数：' + bagsArray.length);
       //显示当前在系统中的所有快递公司
       console.log(`快递公司有：${bagsArray[0]},${bagsArray[1]}`);
       //循环显示
       for(var i=0;i<bagsArray.length;i++){
            console.log(bagsArray[i]);
       }
       //提问：显示数组的最后一个元素值?
       console.log('最后一项：'+bagsArray[bagsArray.length - 1]);
       //向数组中进行添加
       bagsArray[2] = bag3;
       //如果直接书写了以及存在的下标，则为覆盖
       //bagsArray[1] = bag3;
       //数组的长度未知,可以使用长度来录入
       bagsArray[bagsArray.length] = bag4;
       for(var i=0;i<bagsArray.length;i++){
            console.log(bagsArray[i]);
       }
       //思考：如果直接获取数组中部存在的下标？？
       console.log(bagsArray[10]);//undefined 有开辟数组空间。但未存储内容
       //思考：数组在赋值的时候没有连续书写下标。那么length是如何判断的？
       var students = [];
       students[0] = "tom";
       students[1] = "mary";
       students[3] = "jack";
       console.log(students.length);
       for(var i=0;i<students.length;i++){
            console.log(students[i]);
       }
    </script>
</body>
</html>
````



### **删除数组中的最后一个元素**

``students.length--;`

### 数组赋值

数组对于另一个数组的赋值操作

需要解释：为什么变量赋值修改后原值没变，而数组在赋值后原值修改了？？？

### 重新分析数据类型

- 基本类型：在创建后内存中是**以值的方式进行传递**的数据格式
- 引用类型：在创建后内存中是**以地址的方式进行专递**的数据格式

值方式：在赋值操作时直接完成copy动作，赋值完成后的结果和原数据是相互独立的

引用方式：在内存中数据赋值时所传递的是**内存的地址**，而非正值的值

````js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <script>
        //变量赋值
        var num1 = 10;
        var num2 = num1; //把num1变量中的值存储到num2变量中,即把num1中的值copy一份给了num2
        console.log(num2); //10
        num2 = 20;
        console.log(num1);//10
        //数组赋值
        var students = ["tom","mary","jack"];
        var new_students = students;
        for(var i =0;i<new_students.length;i++){
            console.log(new_students[i]); //tom mary jack
        }
        //修改新数组的数据
        new_students[0] = "rose";
        for(var i =0;i<new_students.length;i++){
            console.log(new_students[i]);//rose mary jack
        }
        //提问：此时在已经修改了new_students后，原数组students中的值是否被修改了
        console.log("以下为元原数据");
        for(var i =0;i<students.length;i++){
            console.log(students[i]);
        }
    </script>
</body>
</html>
````

说明：示例中对新数据的修改，是否影响原数据，主要参考当前数据的类型。

思考：怎么样把数据中的每一个值复制给新数组

```js
for(var i=0;i<students.length;i++){
  new_students[i] = students[i];
}
```

说明：数组的copy是值的拷贝，而不能是数组名的操作





### forEach(遍历。IE8以上才能用) 

数组名.forEach();	

````js
var arr = [1,2,3,4,5];
//froEach()方法需要一个函数作为参数
arr.forEach(function(value,index,obj){
    	
});
//像这种函数，由我们创建但是不由我们调用的，我们称为回调函数
//数组有几个元素函数就会执行几次，每次执行时，浏览器会将遍历到的元素以实参的形式传递进来，我们可以定义形参来读取这些内容
//浏览器会在回调函数中传递三个参数
//第一个参数，就是当前正在遍历的元素(value)
//第二个参数，就是当前正在遍历的元素的索引(index)
//第三个参数,就是正在遍历的数组(obj)
````

### for of(遍历)

````js
var a = [1,2,3,4];
for(var str of a ){
    
}
for(var 变量 of 数组名或集合名) //变量中存放的是数组或集合中的元素
         {
             console.log(变量);
         }
````



### **小总结**

- 数组创建
- 数组循环查找
- 数组单值查找
- 数组替换
- 数组删除
- 数组复制

### 多维数组

数组可以在存储变量数据的同时也可以存储数组，这种称为多维数组



## 1.8.2进阶数组及箭头函数

### 箭头函数

在ES5中函数的格式为

````js
function 函数名(函数参数){
    函数体
}

函数名()
````

函数名的作业是能够书写函数的调用名称`函数名()`

还有一种声明函数

````js
var 变量名 = function (函数参数){
    函数体
}

变量名()
````

箭头函数是简化了函数的声明方式

示例

````js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <script>
        function add(num1,num2){
            return num1+num2;
        }

        console.log(add(10,20));

        var add2 = function(num1,num2){
            return num1 + num2;
        }

        console.log(add2(20,30));

        //箭头函数
        var add3 = (num1,num2)=>{
            return num1+num2
        }

        console.log(add3(30,40));
    </script>
</body>
</html>
````

![image-20220804141653240](https://woniumd.oss-cn-hangzhou.aliyuncs.com/web/caoshengjie/20220804141653.png)

说明：从形式上可以看出，箭头函数是一种简便写法



### 箭头函数的特点

参数如果只有一个，可以省略小括号

````js
var add4 = num1=>{
     return num1 +10;
 }

 console.log(add4(60));
````

函数体如果只有一句话，则可以省略大括号

````js
//单句函数体 省略大括号和return
var add5 = num1 => num1+20;
console.log(add5(70));
````

函数如果没有参数，则必须需要有空小括号

````js
// 没有参数 空小括号必须要
var add6 = ()=> {
    //...
}
````



#### 总结

````js
function () {} 这三部分都是固定格式

省略function 在 （） 和 {} 之间使用 => 称为箭头

变为：
var 函数返回变量 = (函数参数)=>{
    函数体
}
````





### 箭头函数

````js
finction add ( num1,num2){
    return num1+num2;
}
//1
var add = finction  ( num1,num2){
    return num1+num2;
}
var add =   ( num1,num2) => {
     var num1 =10;
    return  num1+num2;
}
var add =   ( num1,num2) =>   num1+num2;

//2
(num1,num2) => num1+num2;
//当只输出时，不用return
//3
(num1,num2) =>{
   var num1 =10;
   return  num1+num2;
} 
````



### 数组遍历

数组在之前的操作我们是用for完成循环遍历，在ES6后又提供更多的遍历方法



#### foreach

用于快速遍历数组中每一个值，可以代替for循环



````js
var arr =[11,22,33,44];
arr.forEach((item,index)=>{
    console.log(index,item);
})
````

说明：forEach中item是直接读取数组arr中的每一个值，index读取的是每一个索引，这里无需自定义循环变量，也无需书写step，这里的item是直接获取值



**遍历：**有程序**逐一自动**的完成整个**多值存储对象**的读取，遍历的结束条件是JS

自行判断



**循环：**自定义循环条件和每次**增长步长**的数据读取，循环的结束条件是需要人为设定



forEach标准有三个参数

````js
arr.forEach((遍历相,遍历索引,数组本身))
````

![image-20220804145043854](https://woniumd.oss-cn-hangzhou.aliyuncs.com/web/caoshengjie/20220804145043.png)

可以在遍历过程中直接使用array数组本身结构，如果不需要则可以不写





注意点：关于break

![image-20220804145426187](https://woniumd.oss-cn-hangzhou.aliyuncs.com/web/caoshengjie/20220804145426.png)

**说明：在foreach遍历过程中，是无法使用break来终止遍历的（for循环可以）**



#### map

遍历数组，map有返回，可以在遍历过程中对每一个值做操作，返回依然是一个数组

不会改变原数组

会返回新计算后的数组

````js
//map(延迟赋值)
var newArr = arr.map((item)=>{
    return item
    //[11,22,33,44]
})

newArr[0] = "aa";
console.log(newArr);
console.log(arr);
````

![image-20220804150916312](https://woniumd.oss-cn-hangzhou.aliyuncs.com/web/caoshengjie/20220804150916.png)

**说明：map是把数组的值拷贝一份出来，再组成一个新数组，最后赋值给newArr，即没有任何的地址拷贝的痕迹，两个数组独立**



**可以在return前进行部分item值的修改**

````js
var newArr = arr.map((item)=>{
    return item + "欢迎到来";
    //[11,22,33,44]
})
````

![image-20220804151222646](https://woniumd.oss-cn-hangzhou.aliyuncs.com/web/caoshengjie/20220804151222.png)

![image-20220804151356164](https://woniumd.oss-cn-hangzhou.aliyuncs.com/web/caoshengjie/20220804151356.png)



**说明：不能在map遍历时使用if选择性的返回数据，一旦没有在if语句中return的操作，就会以undefined的形式返回保存**





````js
var arr = [23,43,12,90,79 ];

var newArr arr.map（（value）=> value+5）;

var newArr arr.map（（value）=> {
    	var xxxx；
    return value+5//输出的还是全部加好后的数组
}）;

````

#### filter

**不会改变原数组**

遍历数组，在遍历的同时可以筛选满足条件的结果，并作为一个数组返回

从数组中返回大于xx的数字，并组成一个新数组

````js
var newArr2 = arr.filter((item)=>{
    if(item >= 20){
        return true;//当前item遍历值需要写入内存数组
    }else{
        return false;//当前item遍历值不写入内存数组
    }
    //[22,33,44]
})
console.log(newArr2);
````

**说明：**filter返回的true和false是控制是否将当前item写入数组的判断，true则返回写入，false则不写入

**注意：**filter的返回不像map可以对数值进行计算和修改



遍历数组，在遍历的同时可以筛选满足条件的结果，并作为一个数组返回

从数组中返回大于xx的数字，并组成一个新数组

````js
var arr = [23,43,12,90,79 ];
var NewArr = arr.filter（function（value,index）{
    if (value >=50){
        return true;
    }else {
        return false;
    }
}）;
````



#### some

遍历数组，如果数组中有一个数组满足条件，那么some就会返回true，否则返回false

````js
var arr = [23,25,74,12,79,90];
var result = arr.some((item,index,array)=>{
    return item < 60;//查看（查询）arr数组中有没有小于60的数值，有返回true，没有返回false
    //var temp = return 
})
console.log(result);//false，表示数组中没有小于10的数值
````

说明：return会每次都判断是否有存在的值，return会在运行前在内存中预先设定一个boolean变量。设置为false，如果每次比较都没有返回true，则最终结果为false





#### every

遍历数组，如果数组中所有数据都满足条件，返回true，否则返回false

````js
result = arr.every(function(value,i,arr){
    return value >=10;//判读是否在数组中是否全部数据都大于等于60，如果都大于（满足）true，只要有一个不大于则返回false
})
console.log(result);//true
````



#### reduce

是一种数组的累计快捷方式，累加、累乘

````js
data是上一次遍历之后的累计值，当处理完单签数据之后需要return个新数据出来，给到下一次数据data参数，最终reduce函数返回的是一个遍历完所有数据累计值

数组名.reduce(function(data,value,index,array){
    return data+value;
})
````

![image-20220804163519632](https://woniumd.oss-cn-hangzhou.aliyuncs.com/web/caoshengjie/20220804163519.png)

说明：reduce的使用是需要在数组业务逻辑上索引前后有关联，就可以使用reduce





## 1.9数组常用函数

### API

application programeming interface应用程序编程接口，在软件层已经定义好的代码书写方式，我们可以直接使用。这些代码我们称为API

`Number(),parseInt(),parseFloat,Math.random()`

Javascript中也内置很多api，这里说明数组api

### 数组API

#### push()

可以向数组的末尾添加一个或多个元素，并返回数组新的长度

#### pop

:删除数组的最后一个元素，并将被删除的元素作为返回值返回调用一次删除一次

#### unshift

向数组开头添加一个或多个元素，并返回新的数组长度

向前插入元素后，其他元素索引会依次调整

#### shift

可以删除数组的第一个元素，并将被删除的元素作为返回值返回

````js
//push pop unshift shift
var arr = ['aa','bb','cc'];
var result = arr.push('dd');//在数组的最后添加元素，返回一个当前追加完成后的数组长度
console.log(arr,result);
result = arr.pop();
console.log(arr,result);//在数组最后一个元素删除,并返回元素
result = arr.unshift('ee');
console.log(arr,result);//在数组最前面添加一个元素,并返回长度
result = arr.shift();
console.log(arr,result);//在数组最前（第一个）元素删除，返回删除的元素
````

#### join

可以将数组转换成字符串，可以指定一个字符串作为参数作为连接符默认是逗号

**不会改变原数组**

````js
// join(数组转字符串)
// 数组名.join(连接字符)
var new_str = arr.join('');//不打会默认放置逗号
console.log(new_str,typeof(new_str));
````

说明：在join括号中可以写上连接字符串的字符，如果不写则默认为逗号，如果写空字符串则没有任何连接符号。

#### **<font color='red'>concat()</font>**:可以连接两个或多个数组，并将新的数组返回

**不会改变原数组**



#### splice

删除数组中的指定元素或替换

**会影响到原数组，会将指定元素从原数组中删除，并将被删除的元素作为返回值返回**

参数1.表示开始位置的索引

参数2.表示删除的数量，也可以说是<font color='red'>截取</font>



参数1.表示开始位置的索引

参数2.表示替换的数量，<font color='red'>可以为0</font>。

参数3:想要替换的内容

在原数组中截取一组数组出来，并创建一个新数组，原数组将这些数组删除

（数组的剪切）（分离数组）

````js
var new_arr = arr.splice(0,2);
console.log(new_arr);//新数组有2个数据
console.log(arr);//原数组只有1个数据
````

#### splice替换

````js
var arr = ['aa','bb','cc'];
var new_arr2 = arr.splice(1,2,'zz');//删除索引下标位2的1个元素，并在此位置追加zz新元素
console.log(arr,new_arr2);//返回的是删除的元素
````

#### splice插入

````js
var new_arr3 = arr.splice(2,0,'ww','yy');//在索引为2的位置不删除任何元素，同时追加2个新元素
console.log(arr);
console.log(new_arr3);//返回删除的元素，但是由于是0，所以空数组
````

#### slice切片[begin,end)

说明：slice和splice一样都是可以从原数组中获取数据，但是slice不会删除原数组的数据

参数1.截取开始的位置的<font color='red'>索引</font>，包含开始索引

参数2.截取结束的位置的<font color='red'>索引</font>，不包含结束索引。第二个参数可以省略不写

**索引可以传递一个负值，负值从后往前计算。-1是倒数第一个**

**一个数值的时候会从这个数值开始截取到末尾**

**不会改变原数组，而是将截取到的元素封装到一个新数组中返回**

````js
var newArr = arr.slice(0);//从索引0开始复制元素，不到索引2
console.log(newArr);//aa bb cc
newArr[0] = "ee";
console.log(newArr);//ee bb cc
console.log(arr);// aa bb cc
````

**注意：可以理解为数组的值拷贝操作**

#### sort

排序：默认对一个数组排序是按字母或数字的顺利

默认按照Unicode编码进行修改，数字会错误

可以自己来指定排序的规则，添加一个回调函数来制定排序规则

回调函数需要定义两个形参，浏览器会分别用数组中的元素作为实参去调用回调函数

浏览器会根据回调函数的返回值来决定元素的顺序。如果返回一个大于0的值，则元素会交换位置。返回下于0的值，则元素位置不变，等于0，则元素相等也不会换位置。

如果需要升序则返回a-b

降序返回b-a

**会修改原数组**

````js
var arr = [110,26,13,40,289,3];
var newArr = ['b','f','e','a','d'];
newArr.sort();//默认状态下 字母对对应ascii顺序从小到大排序
console.log(newArr);
//排序从小到大（升序）sort((a,b)=>a-b)
//排序从大到小（降序）sort((a,b)=>b-a)
arr.sort((a,b)=>a-b);//数值升序排序，按照二叉树进行排序的
console.log(arr);
arr.sort((a,b)=>b-a);//数值降序排序
console.log(arr);
//随机排序
arr.sort((a,b)=>Math.random()-0.5);
console.log(arr);
````

#### reverse

该方法会改变原数组

反转-倒序

1. `arr.reverse();`

2. `console.log(arr);`

   

#### indexOf

当前数组里寻找对应的下标

可以检索一个字符串中是否含有指定内容，有的话返回第一次出现的索引，没的话返回-1，第二个参数指定开始查找的位置

1. `var index = newArr.indexOf('d');`

2. `console.log(index);`

   

说明：根据给出的数组字符寻找，如果找不到，则返回-1

#### includes

包含:指定字符是否在数组中存在，存在返回true，不存在返回false

## 1.10函数

### 概念

函数是一段代码容器，在函数中可以包含一段js代码，用来完成一定的功能，并且函数可以多次使用。

````js
定义一个函数
function 函数名(){
    //函数体
}

使用函数
函数名()
````

说明：函数中可以定义多条语句，只有在使用（调用）函数时才会有函数代码执行，而只有等待函数代码执行完毕后才会继续向后运行代码



### 函数命名

函数的名字是可以有字母，数字，下划线，$组成

不能以数字开头

建议使用小驼峰命名格式





### 函数参数

函数参数是可以提供函数体变量的运行值。而变量的来源是通过函数调用位置获取

````js
function 函数名(参数变量名1，参数变量名2){
    //使用参数变量名
}

//使用函数
函数名(变量值1，变量值2)



//定义函数
function sayHello(aa,bb){
    console.log(`${aa}考试分数为${bb}`);
}

//使用函数
var name = 'mary';
var age = 98;
sayHello(name,age);

student_name = 'tom';
student_age = 85;
sayHello(name,age); 
````

在使用函数时设定的变量（name,age）,语法上称为**“实参”**-形式参数

在定义函数function后变量（aa,bb），语法上称为**“形参”**-实际参数

形参和实参时一一对应关系。不能随意换位，但是形参和实参的变量名可以相同，也可以不同



### 函数返回值

函数是为了完成一个可重复并且一定逻辑的代码运行，是整个逻辑程序的一部分。并不能完全掌握整个程序的执行顺序，所以应该将函数的执行结果返回给调用函数的代码位置，由调用位置来决定如何使用函数的结果

函数的返回值`return`

在函数中return后的语句都不会执行，直接退出函数

````js
function 函数名(实参){
    函数体
    return 返回变量
}

var 接受返回变量 = 函数名(形参);
````

说明：根据上述代码反映，所有和显示有关的代码全部从函数中抽离出来（不写在函数中），而是在调用函数的位置完成接受函数return返回给你的变量值，当接受到函数返回值后具体在编写后续输出或其他代码



**小总结**

函数在具体函数体代码时，是需要脱离业务场景的。不能在函数中出现任何和业务有关的代码。这样就可以把函数编写在外部JS文件中。任何需要使用这个函数功能的页面都可以引入



注意：函数的返回值return 只能返回一个数据类型，如果函数有多值返回，则需要创建数组

**特别注意：**

如果以数组的形式传参数给函数，在这种情况下，不能在函数内去改变原数组的任何数值。因为数组是以地址的方式进行传递。所以在函数中的改变，影响了函数外的源值

**说明：**在数组内部复制一份完整的数组数据出来，这样就可以避免和外部数组使用同一个数组操作

复制数组的方式

- 循环逐个数据复制
- slice(0)

**注意：**如果数组作为参数传递给函数时，在函数中是否需要改变数组，需要则复制一份，不需要则不同去复制数组

比如：求数组中每个数据的和，不用复制

求最大值：循环写法，不用复制，但先排序再操作，就需要复制





### arguments

在函数中存在一个特殊的关键词`arguments`，这个本质上是一个函数自带的数组，我们并不需要创建，而可以直接使用。`arguments`是用来接受所有作为参数传递到函数的所有值

类似数组的结果，用数组的方法没用

````js
function demo(){
    var sum=0;
    for(var  i=0;i<arguments.length;i++){
        sum+=Number(arguments[i]);
    }
    return sum;
}

var add_sum = demo(1,2,3);
console.log(add_sum);

add_sum = demo(2,3);
console.log(add_sum);

//练习：有一个数组[3,4,1,9,7]，需要你把数组中最大的数字放到数组最后，要做成函数
var arr = [4,1,9,6,5,2,7,3];
for(var i=0;i<arr.length-1;i++){
    if(arr[i] > arr[i+1]){
        //交换
        var temp = arr[i];
        arr[i] = arr[i+1];
        arr[i+1] = temp;
    }
}
console.log(arr);
````

### 数组-冒泡排序

数组两两对比，大的数据直接和小的进行交换。最后形成大数据一直向后移动，排列完成从小到大

````js
 //冒泡排序
var arr = [4,1,9,6,5,2,7,3];
for(var j=0;j<arr.length-1;j++){
    for(var i=0;i<arr.length-j-1;i++){
        if(arr[i] > arr[i+1]){
            //交换
            var temp = arr[i];
            arr[i] = arr[i+1];
            arr[i+1] = temp;
        }
    }
}
console.log(arr);
````







## 1.11Javascript内置API函数

JS提供一批可供常用的api函数，分为不同的几个大类

- String
- Math
- Date

### String

字符串，在内存中开辟空间后的存储形式其实是数组，就可以按数组的所有操作来进行，如下标，长度

在底层字符串是以字符数组的形式保存的 空格也是

````js
var str = 'hello';

//console.log(str.length,str[0]);
for(var i=0;i<str.length;i++){
    console.log(str[i]);
}
````

字符串的常用API

#### charAt

可以返回字符串中指定位置的字符，根据索引获取指定的字符

通过下标获取字符串里的某个字符

#### concat

连接多个字符串

#### substr

获取字符串的一部分（截取子字符串）

#### substring

获取字符串的一部分（截取子字符串）

#### indexOf

在字符串中根据字符串查找索引位置，没有找到返回-1

#### lastIndexOf

从后往前查找对应的字符位置，给出字符串，寻找下标索引

#### split

将字符串转换为数组

#### replace/replaceAll

替换字符串中的某个/全部字符

第一个参数是替换内容，第二个参数是想要替换的内容

#### for...of（ES6）

遍历字符串

#### startsWith

判断字符串的开头字符

判断字符串是否已参数为开头，返回布尔值

#### endsWith

判断字符串的结尾字符

判断字符串是否已参数为结尾，返回布尔值

#### trim

取消字符串左右两边的空格,不负责中间空格

#### **slice()**:可以从字符串中截取指定的内容，

<font color='red'>第一个参数</font>，开始位置的索引(包括开始位置)。

<font color='red'>第二个参数</font>，结束位置的索引(不包括结束位置)。

<font color='red'>只写一个参数</font>，从参数后全要。负数作为参数从后开始计算



**toUpperCase()**:将字符串转换成大写并返回

**toLowerCase()**:将一个字符串转换为小写并返回

````js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <script>
        var str = 'hello';
        //console.log(str.length,str[0]);
        for(var i=0;i<str.length;i++){
            //console.log(str[i]);
        }

        //charAt
        var str1 = 'hello world';
        var charStr = str1.charAt(0);
        console.log(charStr);//h

        //concat
        var str2 = "hello";
        var new_str = str2.concat(' woniu',' welcome');
        console.log(new_str);//hello woniu

        //substr
        var str3 = "hello woniu";
        new_str = str3.substr(2,2);//第一个参数：从哪个下标开始，第二参数：取几个字符
        console.log(new_str);//ll
        new_str =str3.substr(2);//如果不给第二个参数，则从指定下标开始全部获取
        console.log(new_str);

        //substring
        var str4 = "hello woniu";
        new_str =str4.substring(0,3);//第一个参数：从哪个下标开始，第二个参数：截取到这个下标前（这个下标不包含）
        console.log(new_str);

        //indexOf
        var str5 = "hello woniu";
        var index = str5.indexOf('w');
        var index2 = str5.indexOf('a');
        console.log(index);//6 索引
        console.log(index2);//-1

        //lastIndexOf
        var str6 = "hello woniu";
        var index = str6.lastIndexOf('o');
        console.log(index);//7 从右向左找到的第一个o，从左往右计算下标

        //split
        var str7 = "1,2,3,4,5";
        var arr = str7.split(",");
        console.log(arr);//[1,2,3,4,5]

        //replace
        var str8 = "we are family";
        var new_str = str8.replace(' ','_');
        console.log(new_str);//we_are family 替换找到的第一个
        new_str = str8.replaceAll(' ','-');//替换所有的
        console.log(new_str);

        //for...of
        /*
            for(var 循环变量 of 字符串){

            }
        */
        var str9 = "we are family";
        //遍历
        for(var str of str9){
            //str 每次读取的是值（而非索引）
            //console.log(str);//可以读取每一个字符串，每一次读取str都会向后一个字符指向
        }

        //循环
        for(var i=0;i<str9.length;i+=2){
            //i 作为字符串的索引存在
           // console.log(str9[i]);
        }

        var arr2 = ['a','b','c'];//遍历也可以作用在数组上
        for(var item of arr2){
            console.log(item);
        }

        //startWith
        var str10 = "we are family";
        console.log(str10.startsWith('we'));//true
        console.log(str10.startsWith('e'));//false

        //endsWith
        console.log(str10.endsWith('ly'));//true

        //trim
        var str11 = "   hel lo   ";//trim只负责字符串的左右空格，中间不负责
        console.log(str11.trim());
    </script>
</body>
</html>
````





### Math

JS为了方便放置了和数学有关的常规运算

#### min

取最小值

#### max

取最大值

#### floor

向下取整

#### ceil

向上取整

#### round

取四舍五入

#### pow

计算x的y次方

#### random

随机数

#### sqrt

开平方根

#### PI

圆周率

````js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <script>
        //min
        var arr =[3,2,1,6,-6];
        var min_val = Math.min(arr);//错误不能直接打数组名，因为这个地方需要单个值
        var min_val = Math.min(...arr);//...扩展运算符，是完成对数组中所有元素的全部获取，等于var min_val = Math.min(3,2,1,6,-6)
        console.log(min_val);
        
        //max
        var max_val = Math.max(...arr);
        console.log(max_val);

        //floor
        var num = Math.floor(5.99);
        console.log(num);//5

        //ceil
        num = Math.ceil(6.01);
        console.log(num);

        //round
        var num1 = Math.round(4.4);
        var num2 = Math.round(4.5);
        console.log(num1,num2);

        //pow
        var num3 = Math.pow(2,3);//2的3次方
        console.log(num3);

        //sqrt
        var num4 = Math.sqrt(9);
        console.log(num4);//3

        //PI
        console.log(Math.PI);
        
    </script>
</body>
</html>
````



### Date

在JS中日期格式是需要创建出来，而非系统自动生成

````js
var 日期变量 = new Date();
````

获取日期

getFullYear/getMonth/getDate/getHours/getMinutes/getSeconds

设置日期

setYears/setMonth/setDate.....

**getTime获取当前时间**

返回格式是一个长数字：从1970年1月1日0点到现在的毫秒值

````js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <script>
        //创建日期对象
        var myDate = new Date();
        //获取日期
        var year = myDate.getFullYear();
        var month = myDate.getMonth();//月份是从0开始算 0-11
        var day = myDate.getDate();
        var hours = myDate.getHours();
        var minutes = myDate.getMinutes();
        var seconds = myDate.getSeconds();
        console.log(year,month+1,day,hours,minutes,seconds);//

        //获取时间
        var time = myDate.getTime();//返回的是时间戳（长毫秒值）
        console.log(time);

        //提问：两个时间中间差多少 两个时间戳的相减
        //星期
        var week = myDate.getDay();
        console.log(week);//0-6 0星期天

        //自定义格式
        function getDateTime(str,date){
            var now = date;
            str = str.replaceAll("YYYY",now.getFullYear());
            str = str.replaceAll("MM",now.getMonth()+1);

            return str
        }

        console.log(getDateTime("YYYY/MM/DD HH/mm/SS",new Date())); 
        console.log(getDateTime("YYYY-MM-DD HH/mm/SS",new Date())); 
    </script>
</body>
</html>
````





## 1.12BOM

### 概念

BOM(Browser-object-model)浏览器对象模型，可以用Javascript来完成对部分浏览器的操作。JS自带有控制浏览器的对象（**Math**.random,**Console**.log()）`Window原生对象`，同时window下也提供了多个api来完成控制浏览器的操作，比如新建、关闭浏览器、浏览器前进、后退、刷新、跳转

### Window

window是一个JS的内置对象。可以操作整个浏览器

````js
console.log(window);
````

![image-20220801141807846](https://woniumd.oss-cn-hangzhou.aliyuncs.com/web/caoshengjie/20220801141815.png)

说明：window的确存在，同时也可以看到window下有非常多的api

比如

### 属性和方法

任何一个对象（比如：window）都是可以完成两个内容的点操作

对象通过“点”可以点出两种形式的内容

- 属性：不带有小括号，可以直接使用赋值号完成赋值操作
- 方法：方法带有小括号，需要通过函数的调用传值格式传送参数

````js
//方法
console.log("hello");//类似函数的使用传参
window.prompt("请输入一个数字");//同理，函数使用传参
Math.random();//直接调用，无需给参数
````

### window对象常用属性

- innerWidth: 获取页面的宽度
- innerHeight: 获取页面的高度

````js
//属性
console.log(window.innerWidth,window.innerHeight);
````

说明：两个值分别说明为可视区域的高度和宽度

说明：对于属性是可以直接赋值的，这里由于innerHeight是在页面自动获取和更改，无法通过代码来完成修改的。所以这里语法对的，但是实际无意义。

### window的方法

- close：关闭当前页面

说明：通过我点击网页上的按钮，触发JS的函数，函数中执行了关闭浏览器的命令。从而浏览当前页面关闭（等价于点击了页面上的关闭按钮）

**即通过JS完成了一个浏览器的操作事宜，就是BOM的特点**

- open：打开一个新浏览器页面

````js
window.open("需要打开的页面地址","打开的方式","打开配置")

 window.open('http://www.baidu.com','_blank','width=300,height=150,top=200,left=400');
````

说明：也是使用html点击操作，调用函数，函数中完成open操作，示例是打开百度可以看见百度页面在新的浏览器打开了

特别说明：open的第三参数时配置打开新的浏览器的参数，但由于这些会受到浏览器更新和多浏览器窗口的限制，所以不是都有效（甚至很多浏览器就全无效）

- setTimeout
- setInterval
- clearTimeout
- clearInterval





### **setTimeout/setInterval**

定时器

非立即执行函数

- setTimeout：延迟执行
- setInterval：轮询执行

````js
window.setTimeout(sayHello,3000);//3000毫秒=3秒

function sayHello() {
    console.log("hello");
}
window.setTimeout(sayHello, 3000);//3000毫秒=3秒

window.setTimeout(function () {
    console.log("world");
}, 3000);//3000毫秒=3秒

//5秒后自动暂停
setTimout(function(){
    clearInterval(timer);
},5000)
//或者放到点击按钮中，点击暂停

function stopCount( ){
    clearInterval(timer);
}
//说明：我们即可以直接调用函数名，也可以直接把函数写在setTimeout的第一个参数位置

//第二个参数时毫秒值: 1000毫秒=1秒
````







## 1.13window四大对象

- location
- history
- navigator
- screen

### location

是window对象的一个属性（window.location）同时也是一个对象，location是用来控制浏览器的地址栏

![image-20220801155847138](https://woniumd.oss-cn-hangzhou.aliyuncs.com/web/caoshengjie/20220801155847.png)

### location的属性

host：页面地址中的主机全称，本地指localhost

````js
console.log(window.location.host);//127.0.0.1:5500
````

127.0.0.1==localhost

````js
     console.log(window.location);
        console.log(window.location.host);//获取主机信息（地址+端口）127.0.0.1:5500
        console.log(window.location.port);//获取端口5500
        console.log(window.location.hostname);//获取主机地址lostname/127.0.0.1
        console.log(window.location.protocol);//获取协议 http:
        console.log(window.location.pathname);//获取路径 20220801/06.location.html

        /*
        setTimeout(
            //指定页面的跳转
            function(){window.location.href="http://www.baidu.com";},
            3000
        )
        */
````

说明：location是需要以服务器的方式进行页面访问。不然会拿不到属性值

即不能出现：D:/a/b/hello.html

启动服务器

#### **reload**

刷新页面，我们现在可以通过js完成对页面的刷新操作了

````js
    <script>
		document.write(Math.random());
       function showReload(){   
            console.log("aaa");
           location//刷新页面
       }
    </script>
    <button onclick="showReload()">按钮</button>
````

### **小总结**

location三大点

- 获取当前页面的地址栏信息（host、port.....）
- 指向跳转的地址栏路径（href="....."）
- 刷新页面  reload()

**补充**

**跳转的其他写法**

````js
location.assign('要跳转的页面地址')
location.replace('要跳转的页面地址')
````

区别：assign在跳转后会在浏览器中生成一个历史记录，而replace是不会生成历史记录的

````js
 function showReload(){   
            console.log("aaa");
            //location.reload();//刷新页面
            //location.assign("http://www.baidu.com");
            // location.replace("http://www.baidu.com");
            window.location.href="http://www.baidu.com";
       }
    </script>
    <button onclick="showReload()">按钮</button>
````

### **地址栏的转换**

对中文会有一定的加密操作

encodeURIComponent:加码

decodeURIComponent:解码

````js
 var str = encodeURIComponent("http://www.baidu.com?wd=计算机&name=hello");
       console.log(str);
       console.log( decodeURIComponent(str));
````

![image-20220801163617099](https://woniumd.oss-cn-hangzhou.aliyuncs.com/web/caoshengjie/20220801163617.png)

### 地址栏

URL（统一资源定位符）

由`协议：主机：端口/虚拟路径/网页名称`

域名：是主机的一部分 www.baidu.com 

​	www:协议名称（万维网协议）

​	baidu:公司名

​	com:域名  net  org    edu

端口：默认互联网的统一端口80

### history

history也是window对象，可以对浏览器的历史记录做一些前进、后退操作

**常用函数**

- forward()：前进
- back(): 后退
- go（数字）正数表示前进，负数表示后退

````js
//前进一页
history.go(1);
history.forward();
//后退一页
history.go(-1);
history.back();


//案例
    <a href="./01.作业分析.html">跳转作业分析</a>
    <button onclick="history.forward()">前进一页</button>
    <button onclick="history.go(2)">前进两页</button>
    <button onclick="history.back()">后退一页</button>
    <a href="./06.location.html">打开location页面</a>
````

说明：history跳转页面更准确的说是把浏览器本地的历史页面展示出来，而如果是超链接的跳转则会显示出新页面。新页面中就不会有之前填写的信息

### navigattor

获取浏览本身的一些信息

````js
console.log(navigator.userAgent);
````

### screen

显示和屏幕(显示器)有关的信息

````js
console.log(screen);
````

![image-20220801165911666](https://woniumd.oss-cn-hangzhou.aliyuncs.com/web/caoshengjie/20220801165911.png)





## 1.14原生对象

### 定义对象

````js
//定义一个对象
var 对象名 = {};
// 2定义对象中的一些数据（属性和方法）
var 对象名 = {
    属性名1：属性值1,
    属性名2：属性值2
    key:value
    ...
}

例子
1.创建一个学员对象
var student1 = {
    name:'张三',
    age:12,
    gender:true
}
````

配合函数的使用

````js
function showStudent(student){
    console.log(`当前学员${student.name},年龄：${student.age}性别${student.gender?"男":"女"}`);
}

showStudent(student1)
````

对象可以作为一个参数传递给函数，函数可以在函数体里使用`对象.属性`来操作和显示属性值

特点：

- 函数的调用和函数的定义都完成了一个对象的操作。而不是多个变量

````js
传递变量
function showStudents(name,age,gender){....}
传递对象
function showStudents(stud1)
````

传递对象是，对象的创建是无需对应的位置关联

````js
showStudents('tom',20,true);

//stud1的属性没有前后顺序
var stud1={
	gender:true,
    name:'mary',
    age:19
}
showStudents(stud1)
````

- 对象中是不做任何逻辑判断，即没有任何分支语句和循环语句

- 对象中的方法

````js
var student1 = {
            name:'张三',
            age:12,
            gender:true,
            run:function(){
                console.log("我运动");
            }
        }
````

属性中理论上是有方法存在的，但是实际开发中一般对象中只写属性



**特殊情况**

调用不存在的属性会返回undefined，不会报错



对象在传递给函数时依然是按照应用类型传递

说明：代码中原始值为“张三”，结果因为在函数中的修改，最终导致原始值的name也被修改了，这就证明对象在函数传递时依然是使用引用传递（地址传递）

### 对象修改和新增

#### 对象修改

把对象中属性给二次赋值

````js
var stud = {name:'tom',age:20}
//修改
stud.name = 'mary'

````



#### 对象属性新增

在对象后书写一个未曾定已在对象中的属性,给其赋值

````js
var stud = {name:'tom',age:20}
//新增
stud.gender = "男"
stud["city"] ="上海"
````



### 对象和数组嵌套

## 1.15遍历

````js
数组遍历：for

字符串遍历：for of
对象遍历：for in
````

### 数组的遍历

````js
var arr = [1,2,3,4,5];
//froEach()方法需要一个函数作为参数
arr.forEach(function(value,index,obj){
    	//value 是值
    	//index 是索引
    
});
arr.forEach(( value，index)=>{
//可以只输入value，用两个值需要（）
    //如果只return则可以不用{ }
} )
//像这种函数，由我们创建但是不由我们调用的，我们称为回调函数
//数组有几个元素函数就会执行几次，每次执行时，浏览器会将遍历到的元素以实参的形式传递进来，我们可以定义形参来读取这些内容
//浏览器会在回调函数中传递三个参数
//第一个参数，就是当前正在遍历的元素(value)
//第二个参数，就是当前正在遍历的元素的索引(index)
//第三个参数,就是正在遍历的数组(obj)
````

### 对象遍历

````js
var obj = {
    name:'tom'
	age:20
}

for(var item in obj){
    console.log(item);//name age
    console.log(obj[item]);//‘tom' 20
}
````





## 1.16DOM

document object model(文档对象模型)，document在js中是一个对象，来表示当前整个网页。即window是浏览器，document是网页

document是window的属性，也是独立一个对象



### Document对象

````js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <script>
        console.log(document.body);//输入当前网页（document）中的body标签部分
        console.log(document.documentElement);//获取HTML标签
        console.log(document.title);//获取网站的标题
        console.log(document.URL);//获取页面的完整地址
    </script>
    <h2>热点新闻</h2>
    <strong>国内新闻</strong>
    <ul>
        <li>今天晚上会有好戏吗？</li>
        <li>世界还有贫穷的人吗</li>
    </ul>
</body>
</html>
````

![image-20220802144445559](https://woniumd.oss-cn-hangzhou.aliyuncs.com/web/caoshengjie/20220802144445.png)

说明：直接获取整个页面的html标签元素



### **api**

获取指定HTML标签

- querySelector
- querySelectorAll



### 获取标签名

#### document.querySelector().css/#css ,

返回第一个元素

````js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
  
  
    <h2 id="hotNews">热点新闻</h2>
    <strong>国内新闻</strong>
    <ul>
        <li>今天晚上会有好戏吗？</li>
        <li>世界还有贫穷的人吗</li>
    </ul>


    <script>
        // console.log(document.body);//输入当前网页（document）中的body标签部分
        // console.log(document.documentElement);//获取HTML标签
        // console.log(document.title);//获取网站的标题
        // console.log(document.URL);//获取页面的完整地址

        // 获取标签

        /*
            document:当前网页
            query：查询
            selector：css选择器
        */
        var hotNews = document.querySelector("#hotNews");//返回当前找到的html标签
        console.log(hotNews);
    </script>
</body>
</html>
````

说明：querySelector是寻找能找到的html选择器匹配的节点的第一项，上述案例只能找到“热点新闻”，无法找到“全部hotNews”



#### document.querySelectorALL().css/#css

返回当前网页中的所有符合选择器的标签（数组）

````js
 var hotNews = document.querySelectorAll(".hotNews");//返回当前网页中的所有符合选择器的标签（数组）
// console.log(hotNews);
for(var i=0;i<hotNews.length;i++){
    console.log(hotNews[i].innerHTML);
}
````

### 设置标签的属性/获取标签的属性

- #### setAttribute设置标签的属性

  名称.setAttribute('属性'，'值')

  只能设置内置属性

- #### getAttribute获取标签的属性

  名称.getAttribute('属性')

  只能获得内置属性

````js
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    
</head>

<body>
    <script>
        // console.log(document.body);//输入当前网页（document）中的body标签部分
        // console.log(document.documentElement);//获取HTML标签
        // console.log(document.title);//获取网站的标题
        // console.log(document.URL);//获取页面的完整地址
        // 获取标签
        /*
            document:当前网页
            query：查询
            selector：css选择器
        */
        // var hotNews = document.querySelector(".hotNews");//返回当前找到的html标签，只能找到第一项
        function showNews() {
            var hotNews = document.querySelectorAll(".hotNews");//返回当前网页中的所有符合选择器的标签（数组）
            // console.log(hotNews);
            for (var i = 0; i < hotNews.length; i++) {
                console.log(hotNews[i].innerHTML);
            }

        }

        //获取水果地址
        function getFruitPath(){
            //获取标签
           var imgHtml = document.querySelector("#fruit_img");
           var img_src = imgHtml.getAttribute("src");//获取单个html标签的属性值
           var width = imgHtml.getAttribute("width");
           //设置（修改）html标签的属性
            imgHtml.setAttribute("width","100");
            imgHtml.setAttribute("height","100");

           console.log(img_src,width);
        }

    </script>
    <h2 class="hotNews">热点新闻</h2>
    <strong>国内新闻</strong>
    <img id="fruit_img" src="https://img0.baidu.com/it/u=2196880996,332849298&fm=253&fmt=auto&app=138&f=JPEG?w=525&h=420" width="300"  alt="">
    <ul>
        <li>今天晚上会有好戏吗？</li>
        <li><a href="javascript:showNews()">世界还有贫穷的人吗</a></li>
    </ul>
    <h2 class="hotNews">每日新闻</h2>

    <button onclick="getFruitPath()">获取水果地址</button>

</body>

</html>
````

### 可读写、获取元素的内容

#### InnerHTML/InnerText/value

````js
innerHTML:可以在开始标签和结束标签中间插入一段html标签文本
innerText:可以在开始标签和结束标签中间插入一段纯文本
value:针对属性中含有value属性的标签的设置
````

````js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <button onclick="insertHTML()">插入html</button>
    <p id="myP">
        hello
        <h3>P标签</h3>
        尾部
    </p>
    <input type="text" value="">
    <!-- <button id="btn">记录</button> -->
    <input type="button" id="btn" value="">
    <script>
        function insertHTML(){
            var p_element = document.querySelector("#myP");
            //p_element.innerHTML="<h2>world</h2>";
            //p_element.innerText="<h2>文本</h2>";
            var html_element = document.querySelector("input");
            html_element.value = "臧三";
            var btn = document.querySelector("#btn");
            btn.value = "loading...";
            //取值
            console.log(p_element.innerText);
        }
    </script>
</body>
</html>
````

### 创建节点

#### createElement

动态生成html标签

````js
var 新标签名字 = document.createElement("标签名");

//创建新标签
var newLi = document.createElement("div");
newLi.innerText="abc";
//在网页中插入一个子标签
document.body.appendChild(newLi);
appendChild:在当前指定的位置进行子标签的插入,示例是给到document.body,代表网页body标签中
````

### 添加节点

#### 父级.appendChild（子级）

**原先元素后**

**在指定父标签内插入子标签**

````js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        div{
            color:red;
        }
        ul li{
            list-style: none;
            line-height: 26px;
            float: left;
            margin: 0 10px;
        }
        ul li a{
            text-decoration: none;
            color: gray;
        }
        ul li a:hover{
            text-decoration: underline;
            color:tomato;
        }
    </style>
</head>
<body>
    友情链接
   <ul></ul>
    <script>
        var newsTitleArr= [
            {newsTitle:'百度',url:'http://www.baidu.com'},
            {newsTitle:'新浪',url:'http://www.sina.com.cn'},
            {newsTitle:'搜狐',url:'http://www.sohu.com'}
        ]
        //创建新标签
        /* var newLi = document.createElement("div");
        newLi.innerText="abc";
        //在网页中插入一个子标签
        document.body.appendChild(newLi); */

        var ul_element = document.querySelector("ul");
        //创建新li标签

        for(var i=0;i<newsTitleArr.length;i++){
            //创建了一个html标签
            var new_li = document.createElement("li");
            new_li.innerHTML=`<a href='${newsTitleArr[i]['url']}' target='_blank'>${ newsTitleArr[i]['newsTitle']}</a>`;
            ul_element.appendChild(new_li);
        }
    </script>
</body>
</html>
````

#### 父级.insertBefore(子级 ， 指定元素)





### 删除节点

#### removeChild

````js
父标签变量名.removeChild(待删除的标签)

//示例
1.需要删除的标签
var img = document.querySelector('#box img');
2.父标签
var div = document.querySelector('#box');
3.删除
div.removeChild(img);
````

补充：如果需要删除批量图片(img)

````js
1.获取所有的img标签 querySelectorAll("#box img")  可以使用数组的方式操作
2.父标签 querySelectorAll("#box")
3.循环标签
for
    box.removeChild(img)
````

## 1.17DOM操作

### 获取css

通过`window.getComputedStyle()`来获取标签的css属性

````js
var  css对象名 = getComputedStyle(标签名，null);
获取指定CSS属性值：css对象名.具体css属性名
````

获取到的css对象包含了该标签所有css属性的值

````js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        #box{
            width: 100px;
            height: 100px;
            color:red;
            background-color: pink;
        }
    </style>
</head>
<body>
    <div id="box">hello</div>
    <script>
        //获取这个div
        var box = document.querySelector('#box');
        //获取css对象
        var cssObj = getComputedStyle(box,null);
        //通过cssObj对象来取得css具体的值
        console.log(cssObj.color);
        console.log(cssObj.backgroundColor);
        console.log(cssObj.width);
    </script>
</body>
</html>
````

### 修改css

````js
1.获取标签
2.利用style的修改css
标签变量名.style.css属性名= 新css属性值
````

````js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <div id="box">hello</div>
    <script>
        //获取对象
        var box = document.querySelector("#box");
        //通过style来修改
        box.style.color = 'red';
        box.style.backgroundColor = 'green';//在css中有中划线的词需要去掉线然后改驼峰命名
        box.style.width= "200px";
        box.style.cssFloat = 'left';//浮动
    </script>
</body>
</html>
````

**JS可以改变html中的css**

### Javascript的小动画

利用JS完成页面的小动画是需要完成对css属性的不间断数值改变

示例：div的移动

````js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        #result{
            width: 100px;
            height: 100px;
            background-color: pink;
            margin-top: 10px;
        }
    </style>
</head>
<body>
    <div id="result"></div>
    <script>
        var div = document.querySelector('#result');
        var style = getComputedStyle(div,null);
        //轮询
        setInterval(function(){
            var oldTop = parseInt(style.marginTop);
            //修改
            div.style.marginTop = oldTop + 2 +"px";
        },17);
    </script>
</body>
</html>
````

### 获取父、子、兄弟标签

#### firstElementChild

第一个子html标签

#### lastElementChild

最后一个子html标签

#### previousElementSibling

前一个兄弟HTML标签

#### nextElementSibling

下一个兄弟HTML标签

#### children

所有直接子标签

#### parentElement

获取父标签

````js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <p>这是一个p标签</p>
    <div id="box">
        <button>--</button>
        <input type="text">
        <button>++</button>
    </div>

    <script>
        //获取这个标签
        var box = document.querySelector('#box');
        //获取父标签
        console.log(box.parentElement);//整个完整的body标签

        //获取兄弟标签
        console.log(box.previousElementSibling);//获取P标签

        //获取box的第一个子标签
        var first = box.firstElementChild;
        //获取box的最后一个子标签
        var last = box.lastElementChild;
        console.log(first,last);

        //获取所有子标签
        console.log(box.children);
    </script>
</body>
</html>
````

说明，通过各种方式可以得到当前需要的子元素（子标签、子结点）



### 补充

````js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <div id="box">hello</div>
    <input type="text" class="input-form">
    <p>world</p>
    <p>tom</p>
    <script>
        var box =document.querySelector("#box");//可以获取class和id或任何html选择器对应的html
        var newBox = document.getElementById("box");//只能填写id选择器
        var newBox2 = document.getElementsByClassName("input-form");//只能填写class选择器
        var newBox3 = document.getElementsByTagName("p");//只能填写html选择器
        console.log(box);
        console.log(newBox);
        console.log(newBox2);
        console.log(newBox3);
    </script>
</body>
</html>
````





## 1.18DOM事件

### 概念

事件是用户和网页之间会有交互动作的统称。比如点击操作、鼠标移动操作、输入框获取光标操作。键盘操作等.....

### 事件分类

#### 基础事件

##### load

载入事件，网页的所有资源在这个打开网页时进行加载，加载完成后执行load事件，一般可以用于图片等加载

语法

````js
元素对象名.onload = function(){
    //加载事件
}

````



##### 元素加载

````js
var img = document.querySelector("img");
//img的load事件
img.onload = function(){
    alert("图片加载完成");
}
````



##### 网页载入事件

````js
 //网页加载事件
window.onload = function(){
    alert('页面上所有标签都加载完毕，可以使用js来获取标签并进行操作');
    var img = document.querySelector("img");
    console.log(img);
}
````

##### resize

当页面尺寸发生变化时会自动触发

````js
//resize
window.onresize = function(){
    console.log('页面尺寸发生了变化');
}
````

#### 鼠标事件

##### mousemove

鼠标在指定标签中移动

##### mouseenter

鼠标移动到标签里是触发

##### mouseleave

鼠标移出标签使触发

##### mousewheel

滚轮滚动时触发(只有部分浏览器支持)

##### click

单击触发

##### dbclick

双击触发

````js
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        div {
            width: 200px;
            height: 200px;
            background-color: pink;
        }
    </style>
</head>

<body>
    <div></div>
    <script>
        var div_obj = document.querySelector('div');
        //鼠标操作
        div_obj.onmousemove = function () {
            console.log('鼠标在div里移动');
        }

        div.onmouseenter = function () {
            console.log('进去了');
        }

        //双击div
        div.ondblclick = function(){
            console.log("div被双击了，666")
        }

        //鼠标在网页上移动
        document.body.onmousemove = function(){
            console.log('鼠标在body里移动')
        }
        
    </script>
</body>

</html>
````

#### 键盘事件

##### keydown

键盘按下事件

##### keyup

键盘松开事件，如果说设置input操作，获取的是input修改之后的数据

##### keypress

释放键帽事件，如果说设置input操作，获取的是input修改之前的数据

````js
    var input = document.querySelector("input");

        //keydown
        input.onkeydown = function(){
            console.log('keydown',input.value);
        }

        //keypress
        input.onkeypress = function(){
            console.log('keypress',input.value);
        }

        //keyup
        input.onkeyup = function(){
            console.log('keyup',input.value);
        }
````

**说明：keypress和keyup都只能拿到旧值，而keydown可以获取到新值**





#### 焦点事件

##### focus

当某个元素获得光标时触发

##### blur

当某个元素失去光标时触发，一般都用于input

````js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        input{
            outline:none;
            transition: all .5s;
            border:1px solid #ccc;
            box-shadow: 0 0 10px #ccc;
        }
        .active{
            border:1px solid green;
            box-shadow: 0 0  10px green;
        }
    </style>
</head>
<body>
    用户名：
    <input type="text" id="username">
    密码：
    <input type="text">
    <script>
        var username = document.querySelector("#username");
        //获取光标
        var userinput = document.querySelector("#username");
        userinput.onfocus = function(){
            userinput.setAttribute('class','active');
        }
        userinput.onblur = function(){
            userinput.setAttribute('class','');
        }
        
    </script>
</body>
</html>
````

**输入框获得光标后变化为路色边框，变化过程使用css过渡效果**



#### 文本事件

##### change

当内容发生变化时

### 移动端

- touchstart
- touchend
- touchmove



### 事件流

#### 背景

- 当点击一个子标签时，其父标签是否算被点击呢？

![image-20220803141534234](https://woniumd.oss-cn-hangzhou.aliyuncs.com/web/caoshengjie/20220803141534.png)

在P元素内部的点击，直接触发了两个onclick事件，默认状态下，先处理的是p（内部），在是div（外部）

顺序（从内向外）



事件流：是指事件在触发时，父子标签的触发顺序

按照流向不同可以分为两种：

- 冒泡
- 捕获
- 

#### 冒泡

是指当事件触发时，应该是具体触发事件的子标签先执行，再执行父标签事件，一直到祖先标签执行后才结束

子->父->祖父->祖先

完整线路：具体子标签->父标签->爷爷标签->body->html->doucment->window

````js
<ul>
    <li>
    	<p>
            <span>这是一个span标签</span>
            <a>超链接</a>
        </p>
    </li>
</ul>

如果每个标签都做了点击事件，则触发顺序

a/p/li/ul/body/html/document/window
````



#### 捕获

指当前触发后，应该是祖先标签先执行，再一直到具体触发事件的子标签

父->子

```js
<ul>
    <li>
    	<p>
            <span>这是一个span标签</span>
            <a>超链接</a>
        </p>
    </li>
</ul>

点击a：window/document/html/body/ul/li/p/a
```



### 事件处理程序

#### 概念

当某个时间被触发时，这个事件所对应函数就是事件处理程序，也就是要执行的js代码



#### 分类

**DOM0级**

​	on+事件名，load事件（onload），click事件（onclick）

````js
document.body.onclick=function (){
    console.log('hello');
}
````

  **只支持冒泡，不支持捕获**



**DMO2级**

​	自定义添加

````js
标签变量名.addEventListener("事件名",事件处理程序,是否捕获处理)
````

````js
//示例：给body设置点击事件，输入hello
document.body.addEventListener("click",handler,true);//true为捕获操作

function handler(){
    console.log('hello');
}
````

**如果设置false，则表示冒泡处理，false为默认值**

```js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <div>
        <p>hello</p>
    </div>

    <script>
       
        var div = document.querySelector("div");
        var p = document.querySelector("p");
        // onclick 是冒泡，不能捕获
       /* 
        div.onclick = function(){
            console.log("div-onclick");
        }

        p.onclick = function(){
            console.log("p-onclick");
        }
        */

        //捕获格式
        div.addEventListener('click',function(){
            console.log("div-onclick");
        },true);

        p.addEventListener('click',function(){
            console.log("p-onclick");
        },true)
    </script>
</body>
</html>
```



#### **删除事件处理程序**

````js
document.body.removeEventListener("click",handler,true)
````

用的是`removeEventListener`

**案例**

**注意，删除时需要把事件处理函数和添加时写成一个，不然会删除失败**

````js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <button id="btn">按钮</button>
    <script>
        var btn = document.querySelector('#btn');
       
        function fun(){
                console.log('hello');
        }
        
        function addEvent(){
            btn.addEventListener('click',fun)
        }


        function removeEvent(){
            btn.removeEventListener('click',fun)
        }
    </script>
    <a href="javascript:addEvent()">添加事件</a>
    <a href="javascript:removeEvent()">删除事件</a>
</body>
</html>
````







### event事件对象

概念

在触发事件的时候，我们总会有所需要当前触发的位置以及触发原，这些信息系统提供了一个event事件对象可以直接获取

````js
document.body.addEventListener('click',function(event){
    console.log(event);
})
````

![image-20220803172630276](https://woniumd.oss-cn-hangzhou.aliyuncs.com/web/caoshengjie/20220803172630.png)

**说明：这个变量名是可以自定义的。同时所获得的内容也是和浏览器的位置有关 **





#### **event常见可以用属性和方法**



- **target：真正触发事件的位置**

  

- **clinetX**：触发事件时鼠标相对于页面左上角的x位置

  

- **clinetY**：触发事件时鼠标相对于页面左上角的Y位置

  

- offsetX：触发事件时鼠标相对于标签的x轴偏移量

  

- offsetY：触发事件时鼠标相对于标签的Y轴偏移量

  

- pageX：触发时鼠标里页面左上角的X坐标位置

  

- pageY：触发时鼠标里页面左上角的Y坐标位置

  

- **preventDefault()：取消标签的默认行为**



- **stopPropagation()：阻止冒泡事件**

```js
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>

<body>
    <div id="box">aa</div>
    <a href="http://www.baidu.com" id="link">跳转</a>
    <script>
        // window.document.addEventListener('click', function (e) {
        //     console.log(e);
        // })
        // document.getElementById("box").addEventListener('click', function (e) {
        //     console.log(e);
        // })

        // function link(e){
        //     console.log(e);
        //     alert("跳转");
        // }
document.getElementById("link").addEventListener('click',function(e){
                e.preventDefault();//组织当前事件默认行为发生
                alert("aaa")          
            })
    </script>
</body>

</html>
```

说明：html触发事件处理程序带动e的获取。是需要用`addEventListener`来完成，不能直接使用`onclick`的函数，因为onclick只是完成函数的调用。而没有event对象

#### stopPropagation

当有冒泡的事件发生，我们就需要有阻止的动作可以执行

![image-20220804102446192](https://woniumd.oss-cn-hangzhou.aliyuncs.com/web/caoshengjie/20220804102453.png)

说明：打上红色语句后，当前事件后的所有冒泡行为都将终止

特别说明：IE不支持

````js
event.cancelBubble = true;//IE支持（Chrome也已经实现了）
````

## 1.19事件委托

### 概念

把事件处理程序从原有的事件源上移动到其他元素，而非自己执行。这称为“事件委托”

![image-20220804104643064](https://woniumd.oss-cn-hangzhou.aliyuncs.com/web/caoshengjie/20220804104643.png)

如果**事件源是动态生成**或**无法确定具体的操作事件源**。此时就**无法直接绑定事件监听**

需要去添加`event.target`来判断真正的触发事件

````js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <div>
        <img class="good-img" src="../20220803/img/id1.jpg" alt="">
        <p class="good-title">经典时尚小摆件</p>
        <p class="good-price">￥30</p>
    </div>
    <script>
        //所有div的子元素都不执行事件监听（onclick）,而直接在父元素上做监听div，由div来完成页面具体那个子元素的触发
        //获取父元素的对象
        var div_element = document.querySelector("div");
        //给父元素对象绑定单击事件
        div_element.addEventListener('click',function(e){
            //通过event事件对象 自带有一个target属性，可以获取子元素的触发对象
            var touch_element = e.target;
            //对象.属性 对象.方法()  typeof-object   {}
            var class_name = touch_element.getAttribute('class');
            switch (class_name) {
                case 'good-img':
                    eventImg();
                    break;
                case 'good-price':
                    eventPrice()
                    break;
                default:
                    eventDesc()
                    break;
            }
        })

        //图片事件处理函数
        function eventImg() {
            console.log("img被点击了");
        }
        //价格事件处理函数
        function eventPrice(params) {
            console.log("第二个P被点击了");
        }
        //名称事件处理函数
        function eventDesc(params) {
            console.log("title被点击了");
        }
    </script>
</body>
</html>
````

说明：委托就是安排父元素来监听子元素的触发事件

## 1.20正则表达

### 概念

正则是一种特殊的字符串，是一种**数据匹配**的书写语法，一般作用在指定的数据验证上，比如手机号码、邮箱等这样格式要求上

### 语法调用

````js
var 正则表达式变量名 = /正则表达式语法/;

//方法一
var reg=new RegExp("正则表达式","匹配模式");
//方法二
var reg=/正则表达式/匹配模式

正则表达式变量名.test(变量数据);//返回布尔值
````



### **正则对象的方法**

正则对象.test(字符串) :  这个方法用来检查字符串是否符合正则表达式的规则，符合返回true，不符合就返回false



字符串.**search**(正则对象) 可以根据正则规则来搜索字符串中是否包含指定的内容，如果搜索到指定内容则返回第一次出现的索引，否则就返回-1

字符串.**match**(正则对象) 根据正则表达式，从一个字符串中将符合规则的内容提取出来,默认情况下match只能找到第一个符合正则的内容，找到后就停止检索了。

**我们可以设置正则表达式为全局搜索，这样就会匹配到所有的符合正则规范的内容了/^xxx$/img**

```js
let onOff=reg.test(str); //正则判断数据是否存在 true/false
let index=str.search(reg);//找到的下标 -1 没有
let arr=str.match(reg);  //匹配次数,没有匹配模式，只找第一个，有g是找所有找到的;
```



### 修饰符(匹配模式)

```js
var reg=new RegExp("正则表达式","img");
var reg=/正则表达式/img; 
i: 忽略大小写
m: 执行多行匹配
g: 执行全局匹配
```



### 正则表达式语法

**基础语法**

`[]`:匹配组，表示在它里面的所有设置，只能表示为一个

- `[0-9]` 匹配任意一个数字

````js
var num = 'a1234a';
var reg = /[0-9]/;
//使用正则匹配
var result = reg.test(num);
console.log(result ? '验证成功' : '验证失败');
````

![image-20220805101701693](https://woniumd.oss-cn-hangzhou.aliyuncs.com/web/caoshengjie/20220805101708.png)

**说明：示例要求对于当前的字符串中有0-9的事少一个数值的，就算成功，如果字符串中没有数字。则判定false**

- `[0-9][0-9]`连续2个数值，判定成功
- `[a-z]`匹配任意一个小写字母

````js
var num = 'abc1';
var reg = /[a-z]/;
//使用正则匹配
var result = reg.test(num);
console.log(result ? '验证成功' : '验证失败');
````

**说明：只要匹配字符串中有(至少有)一个小写字母，就算成功**



- `[A-Z]`匹配任意一个大写字母
- `[a-zA-Z]`匹配任意一个大小或小写字母
- `[0-9a-zA-Z]`匹配任意一个大写、小写、数字



`[]`:组。可以匹配其中的任意一个字符

- `[0-9]` :匹配任意一个数字。
- `[12345]`:匹配1、2、3、4、5中的任意一个
- `[a-z]`:匹配任意一个小写字母
- `[A-Z]`:匹配任意一个大写字母
- `[a-zA-Z]`:匹配任意一个字母
- `[0-9a-zA-Z]`:匹配任意一个数字或字母
- `[abc]或[a-c]`:匹配abc中的一个字母
- `/^ab[cd]$/`:匹配abc或abd
- `/^James[ZL]S$/`:匹配 JamesZS 或JamesLS





`{}`:用于描述组`[]`的出现的次数

- `{m,n}`:表示前面的一个组至少出现m次，最多n次
- `{m}`:表示前面的一个组固定次数m次
- `{m,}`:表示前面的一个组至少m次





- `^`:以什么开头

  - `/^[0-9]{3}/`:以3个连续的数字开头
  - `/^[a-z]/`:以一个小写字母开头

- `$`:以什么结束

  `/[0-9a-zA-Z]{3}$/`:以3个数字或字母结尾



`/^正则表达式语法$/`:匹配整个的字符串必须符合正则表达式规则

- `/^[a-zA-Z]{10}$/`:表示整个字符串是10个字母
- `/^[0-9a-zA-Z]{6,16}$/`:表示整个字符串是6~16位的数字或字母



`()`:匹配多个字符串中的一个(分组)

- `/\.(jpg|png|gif|jpeg)/`:匹配.jpg、.png、.gif、.jpeg中的一个



次数`{}`

- `{m,n}`表示匹配指定的次数
- `{1,4}`表示匹配字母长度至少为1，最多为4

````js
var num = 'ab';
var reg = /[a-z]{3,5}/;
//使用正则匹配
var result = reg.test(num);
````

**说明：设置连续的变量为3-5个，因为输入ab只有2个，所以失败**



- `{1，}`匹配至少超过1个
- `{,5}`不能超过5个

开始和结束

- `^` 表示开始
- `$`表示结束

如果^和$同时使用。那么就意味着判断整个数据



````js
var num = 'abc';
var reg = /^[a-z]{2}$/;
//使用正则匹配
var result = reg.exec(num);
console.log(result ? '验证成功' : '验证失败');
````



### 简写语法

`[0-9a-zA-Z]`可以简写为`\w`

`[0-9]`可以简写为`\d`

`{1，}`简写为`+`

`{0,1}`简写为`?`

`{0,}`简写为 `*`



**常用的正则规则**



| 表达式 | 描述                                   |
| :----- | :------------------------------------- |
| [abc]  | 查找方括号之间的任何字符。只匹配一个。 |
| [0-9]  | 查找任何从 0 至 9 的数字。只匹配一个。 |
| (x\|y) | 查找任何以 \| 分隔的选项。             |



| 元字符(一个字符) | 描述                                                         |
| :--------------- | :----------------------------------------------------------- |
| \d               | 查找数字  [0-9] 只匹配一个。                                 |
| \s               | 查找空白字符及换行  “ ”  \n                                  |
| \w               | 查找字母，数字，下划线  [0-9a-zA-z_]                         |
| .                | 表示一个任意字符                                             |
| \u0053           | 查找以十六进制数  `S` 规定的 Unicode 字符   汉字编码范围 [\u4E00-\u9FA5] |
| \D \S \W         | 反向操作                                                     |





| s+     | 匹配任何包含至少一个 s 的字符串。 {1,}                       |
| ------ | ------------------------------------------------------------ |
| s*     | 匹配任何包含零个或多个 s 的字符串。{0,}                      |
| {m,n}? | 表示前面的一个组至少出现m次，最多n次。（? 非贪婪模式，懒惰模式，尽可能少匹配） |

### 方法



| 方法                                          | 描述                                                         |
| :-------------------------------------------- | :----------------------------------------------------------- |
| 正则对象.**test**(字符串)                     | 验证字符串是否匹配正则规则                                   |
| 字符串.**split**(正则对象)                    | 以正则规则作为字符串分割的条件，返回分割后的数组对象         |
| 字符串.**search**(正则对象)                   | 可以根据正则规则来搜索字符串中是否包含指定的内容，如果搜索到指定内容则返回第一次出现的索引，否则就返回-1 |
| 字符串.**match**(正则对象)                    | 根据正则表达式，从一个字符串中将符合规则的内容提取出来,默认情况下match只能找到第一个符合正则的内容，找到后就停止检索了。 我们可以设置正则表达式为全局搜索，这样就会匹配到所有的符合正则规范的内容了 |
| 字符串.**replace**(字符串/正则对象, 替换的值) | 将字符串中的指内容/正则匹配内容替换成新的内容，会返回一个新的字符串 |

## 1.21本地存储

### 概念

前端在浏览器中可以进行一定的存储操作，可以方便作为页面的临时使用(当然早期也有另一种存储方式)



### 存储方式

1. 文件存储

   1. cookie 小饼干，是浏览器在加载页面时，如果页面中有要求存储，则浏览器会在指定的系统盘符下建立一个cookie小文件。进程存储

      缺点：1.明文存储，存储格式为txt，不安全

      2.操作系统是可以关闭cookie的创建

2. 浏览器存储

   - localStorage：保存时永久的，在不明确删除的情况下。始终存在
   - sessionStorage：保存的数据值直到网页的关闭才销毁



### SessionStorage

建立方式是以**键值对**的形式完成设置

````js
1.创建保存数据[item,item]  item {属性名，属性值}
sessionStorage.setItem("属性名","属性值")
2.读取数据
sessionStorage.getItem("属性名")
3.删除数据
sessionStorage.removeItem("属性名")
4.清空
sessionStorage.clear()
````





```js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <a href="./03.本地存储跳转.html">本地存储跳转</a>
    <h2>sessionStorage</h2>
    <input type="text" id="item">
    <button id="saveBtn">保存</button>
    <button id="getBtn">读取</button>
    <button id="delBtn">删除</button>
    <button id="clearBtn">清空</button>
    <script>
        document.getElementById("saveBtn").addEventListener('click',function(){
            //读取输入框的值
            var text = document.getElementById('item').value;
            //创建并保存在本地
            sessionStorage.setItem('input',text);
            sessionStorage.setItem('password',"123");
            sessionStorage.setItem('age',"20");
        })
        //注意，跳转页面后在新页面的操作都是可以访问
        document.getElementById('getBtn').addEventListener('click',function(){
            console.log(sessionStorage.getItem('input'));
        })
        //删除
        document.getElementById('delBtn').addEventListener('click',function(){
            sessionStorage.removeItem('input');
            console.log(sessionStorage.getItem('input'));
        })
        //清空
        document.getElementById('clearBtn').addEventListener('click',function(){
            sessionStorage.clear();//删除会话（session）中的所有本地存储
        })
    </script>
</body>
</html>
```

![image-20220805144637616](https://woniumd.oss-cn-hangzhou.aliyuncs.com/web/caoshengjie/20220805144637.png)



### localStorage

```js
1.创建保存数据
localStorage.setItem("属性名","属性值")
2.读取数据
localStorage.getItem("属性名")
3.删除数据
localStorage.removeItem("属性名")
4.清空
localStorage.clear()
```





## 1.22JSON

JSON是我们在数据传输格式上一种书写格式



### 数据传输

- 基础数据类型 method传递

- 格式化数据
  - XML
  - JSON





### **JSON是什么？**

所有数据都是以对象的形式进行传递，多值数据使用数组封装

对象形式：`{}`

数组形式：`[]`

所有在对象中的数据都以`键值对`形式传输

如

```js
var student = {
    nianling:20,
    fenshu:[90,87,88],
    pengyou:[
    	{name:'mary'},
    	{name:'alice'}
    ],
    gender:true,
    dizhi:80,
    xingming:'tom',
}
```

说明：**json是一种书写规范。**所有人在书写后都可以直接观察到数据的结构，都可以理解和读取数据，json中的数据是没有排列顺序的。所有内容可以描述所有数据类型，而且全部都是文本形式，所以JSON格式适合于数据在网络上的传输



现实开发中。适合于前后端的交互





**需要说明**

可以把json格式数据存储在本地storage都可以，只是存储后是字符串形式，而在系统中是需要转换为json格式才能操作

````js
//JSON数据对象
var student = {
    name:'tom',
    age:20
}

//互联网接受到的数据
var student1 = "{name:'tom',age:20}"
````

这里需要做一个数据转换

- #### JSON.parse()   可以将字符串转换为JSON对象

- #### JSON.stringify()  可以将JSON对象转换为字符串





**本地存储和Cookie的优势**

Cookie是可以关闭的而本地存储是不能关闭
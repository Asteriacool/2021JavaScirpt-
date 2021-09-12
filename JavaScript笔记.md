### 一、基础语法

#### 1.一句话定义JavaScript

解释型语言，动态语言，基于原型的面向对象

#### 2.输出语句

- js代码要写在script标签中
- js的注释方式为/*……*/

##### 三种输出语句

- alter()
  - 是弹出警告框，括号内是警告框的内容

- document.write()
  - 在页面显示内容，即向body中输出内容
- console.log()
  - 向控制台输出内容（不打开开发者工具无法看到）

##### 基础框架实例

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    <title></title>
    <script type="text/javascript">
      /*
       *控制浏览器弹出一个警告框
       */
      alert("这是我的第一行js代码");
      /*
       *让计算机在页面输出一个内容，即在body中输出一个内容
       * */
      document.write("在页面显示一个内容");
      /*
       * 向控制台输出一个内容
       * */
      console.log("向控制台写一个内容");
    </script>
  </head>
  <body>
  </body>
</html>
```

#### 3.js编写

* 按钮的设置

  `<button onclick="语句"></button>`

- 语句条的设置

  `<a href="语句"></a>`

* 将外部的js代码引入

  `<script type="" src="外部文件的路径"></script>`

##### 外部代码引入示例

```javascript
//script.js文件
alter("我是外部js文件中的代码")
```

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    <title></title>
    <!--可以将js代码编写到外部js文件中，然后通过script标签引入，
		src属性指向外部的路径写到外部文件中可以在不同的页面中同时引用，
		也可以利用到浏览器的缓存机制，是推荐的方式-->
    <!--script标签一旦用于引入外部文件，就不能再编写代码，
		即使编写了，浏览器也会忽略如果需要，
		则可以创建一个新的script标签，用于放置内部的代码-->
    <script type="text/javascript"  src="js/script.js">
      alter("我是内部的js代码");   //此句无效
    </script>
    <script>
      alter("我是内部的js代码");
    </script>
  </head>
  <body>
    <!--可以将js代码编写到标签的onclick属性中
		当我们点击按钮时，onclick中的内容才得以执行，生成一个警告框
		虽然可以写在标签的属性中，但是他们属于结构与行为耦合，不方便维护-->
    <!--双引号里面要用单引号-->
    <button onclick="alert('你点我干什么？')">点我一下</button>
    <!--可以将js代码写在超链接的href属性中，这样点击超链接时，会执行js代码效果是生成一个警告框-->
    <a href="javascript:alert('让你点你就点');">你也点我一下</a>
  </body>
</html>
```

#### **4.js基本语法**

- js中严格区分大小写
- js中每一条语句以分号结尾
- js会忽略多个空格和换行，可以利用空格和换行对代码进行格式化

#### **5.字面量和变量**

- 字面量都是不可改变的值，是可以直接使用的，但一般不直接使用
- 变量，可以用来保存字面量，所以在开发中使用变量来保存字面量

##### （1）变量的声明：var

`var a;`

##### （2）变量的赋值

`a = 123;`

##### （3）声明和赋值同时进行

`var a = 123;`

#### **6.标识符的定义与规则**

在js中所有可以由我们自主命名的都可以认为是标识符，例如变量名、函数名、属性名，命名时需要遵守以下规则：

- 标识符中可以含有字母、数字、_、$
- 标识符不能以数字开头标识符不能是es中的关键字或保留字
- 标识符一般采用驼峰命名法，首字母小写，每个单词的开头字母大写，其余字母小写——helloWorld
- js底层保存标识符时，实际上是采用Unicode编码，所以理论上讲，所有的utf-8中含有的内容都可以作为标识符（含有中文）

#### **7.数据类型**

数据类型是字面量的类型，有六种

- String：字符串
- Number：数值
- Boolean：布尔值
- Null：空值
- Undefined：未定义
- Oject：对象

其中，String、Number、Boolean、Null、Undefined属于基本数据类型，而Object属于引用数据类型

##### （1）String：字符串

- 需要使用引号引起来

`var str = "hello";`

- 使用双引号或者单引号都可以，但是不要混用
- 引号不能嵌套，双引号内部不能有双引号，只能单引号
- 如果字符串内部一定要使用双引号**或者**单引号，可以使用\作为转义字符，比如\"表示"，\'表示'，\\表示\

`str = "我说：\"今天天气很不错""`

##### （2）Number：数值

所有的数值都是Number类型，整数和浮点数都是该类型

- 运算符typeof可以用来检查一个变量的类型

`console.log( typeof a);`

* Number.MAX_VALUE是Number类型可以表示的最大值，如果超过该值，则为Infinity（正无穷，若为负无穷，为-Infinity，是字面量），使用typeof检查，也为number

`Numer.MAX_VALUE  //1.7976931348623157e+308`

- NaN：是一个特殊的数字，表示Not a Number，是字面量，使用typeof检查，也为number
- Number.MIN_VALUE是Number类型可以表示的正数范围的最小值

`console.log( Number.MIN_VALUE );  //5e-324`

- JS中的整数运算基本可以保证精确，如果使用JS进行浮点数计算，可能得到不精确的结果，所以不要使用JS进行对精确度要求比较高的运算

##### （3）Boolean：布尔值

布尔值只有两个，表示真假，主要用来逻辑判断

`var bool = true;`

`var bool = false;`

##### （4）Null&Undefined

Null类型的值只有一个null，专门用来表示为空的对象

- 使用typeof检查null的时候，会返回一个Object

Undefined类型的值只有一个undefined

- 当声明一个变量但是并不给该变量赋值时，这个变量的类型就是undefined

#### **8.强制类型转换**

转换的目标类型是String、Number、Boolean

##### （1）将其他的数据类型转换为String

①方式一：调用被转换数据类型的toString()方法

- 该方法不会影响到原变量，会将转换的结果返回
- 如果原变量为Null或者Undefined类型，没有该方法，如果调用，会报错

```javascript
//调用a的toString方法
var b = a.toString();  //将该方法的执行结果赋值给b
a = a.toString();
```

②方式二：调用String()函数，并将被转换的数据作为参数传入

- 可以实现将null和undefined进行转换

`a=String(a)`

##### （2）将其他数据类型转换为Number

①方法一：调用Number()函数，并将被转换的数据作为参数传入

- 字符串→数值：如果字符串是数字，则转换为对应的数值；**如果存在字母**，则转换为NaN；如果是空字符串或者是全为空格的字符串，则转换为0
- 布尔值→数值：如果为true，则为1；如果是false，则为0
- null→数值：结果为0
- undefined→数值：结果为NaN

`a=Number(a)`

②方法二：

parseInt()——把字符串转换成一个整数

parseFloat()——把字符串转换成一个浮点数

- 专门用于解决字符串转换，如果 对非String类型，会现将其转换成String，然后再操作
- parseInt()可以将字符串中有效的整数内容取出来
- parseFloat()可以取出有效的小数

```javascript
a="123a456px"
a=parseInt(a) //返回123

a="123.456px"
a=parseInt(a) //返回123

a="123.456px"
a=parseFloat(a) //返回123.456
```

##### （3）将其他数据类型转换为Boolean

使用Boolean()函数

- Number→Boolean：除了0和NaN，其余都是ture

```javascript
var a = 123;
a = Boolean(a); //true

var a = 0;
a = Boolean(a); //false

var a = NaN;
a = Boolean(a); //false
```

- String→Boolean：除了空串，其都是true
- Null→Boolean：结果为false
- Undefined→Boolean：结果为false
- Object→Boolean：结果为true

#### **9.其他进制的表示**

16进制：a=0x123

8进制：a=070

2进制：a=0b6

可以在parseInt()中传递第二个参数，来指定数字的进制

a=parseInt(a,10)

### 二、基本运算

#### **1.算术运算符**

通过运算符可以对一个或多个值进行运算

- typeof就是运算符，可以来获得一个值的类型。它会将该值的类型以字符串的形式返回。
- 运算符不会对原变量产生影响
- +

（1）当对非Number类型的值进行运算时，会先将其转换成Number，再进行运算

（2）任何值和NaN做运算时，结果都是NaN

（3）如果对两个字符串进行加法操作，是进行拼串操作（用于书写一些比较长的字符串）

（4）任何值和字符串做加法运算，都会先转化为字符串，再和字符串做拼串操作

```javascript
result = true + 1   //2

result = “123” + “456”  //“123456”

result = 123 + "1"  //1231

result = true + "hello"  //truehello

c = c+""  //可以将其他类型的c转化为空串（隐式类型转换，由浏览器自动完成，实际上调用了String函数）
```

- \-
- *

（1）当对非Number类型的值进行- * /运算时，会先将其转换成Number，再进行运算

```javascript
r = 2 * "8" //转为Number再运算,16

r = 2 * Undefined // NaN

var d="123"
d = d-0  //可以利用这一特点做隐式的类型转换
```

- /
- %:取模运算

#### **2.一元运算符**

只需要一个运算符

- 正号不会对数字产生任何影响
- 可以对其他数据类型使用+，将其转化为Number

#### **3.自增自减**

- 无论是a++还是++a，都会使得原变量自增1，不同的是a++和++a的值不同，a++的值等于原变量的值（自增前的值），++a的值等于原变量自增后的值
- a--的值等于原变量的值（自减后的值），--a的值等于原变量自减后的值

#### **4.逻辑运算符**

- ！非

对一个布尔值进行取反操作，如对一个值进行两次取反，不会发生变化，如果对非布尔值进行运算，则先将其转换成布尔值，然后再对其运算，所以可以利用该特点将其他类型的值变化为布尔值

`b = !!b //将b转化为布尔值（隐式类型转化）`

- &&

两个值中只要有一个值为false，就返回false，只有两个值都为true时，才返回true

- 如果第一个值为false，则不再看第二个值
- 如果第一个值为true，则会检查第二个值

- ||

可以对符号两侧的值进行或运算并返回结果，只要有一个true，就返回true

- js中的“或” 是 短路的或
- 如果第一个值为true，则不会检查第二个值
- 如果第一个值为false，则会检查第二个值
  - 对非布尔值进行运算时，先将其转换为布尔值，然后再运算，并且**返回原值**

- 与运算
  - 如果两个值都为true，则返回第二个值；如果有false，则返回第一个

```javascript
r = 5 && 6  //两个值都为true，返回第二个值，6
r = 6 && 5  //两个值都为true，返回第二个值，5

r = NaN && 0   //含有false，返回第一个值，NaN
```

* 或运算
  * 如果第一个值为true，则直接返回第一个值；如果第一个值为false，则直接返回第二个值

```javascript
r = NaN || 0  //第一个值为false，返回第二个值，0
r = 2 || 0    //第一个值为true，返回第一个值2
```

#### **5.赋值运算符**

=：将符号右侧的值赋值给左侧的变量

+=、-=、*=、%=

#### **6.关系运算符**

- \>\>=\<\<=
- 非数值的情况，会将其转换为数字，然后再进行比较
- 任何值与NaN做任何比较，都是false
- 如果符号两侧的值都是字符串，不会将其转换为数字进行比较，而是分别比较字符串中字符的Unicode编码，比较字符编码时，一位一位进行比较，如果两位一样，则比较下一位（比较中文没有意义）
- 注意在比较两个字符串类型的数字时，首先进行转型
- 在字符串中使用转义字符输出Unicode编码：\u四位编码（这里的编码是十六进制）
- 在网页中使用Unicode编码：&#编码（这里的编码需要的是十进制）

#### **7.相等运算符**

##### ==：相等判断

* 如果值的类型不同，则会自动进行类型转换，将其转换为相同的类型，然后再比较

```javascript
"1" == 1 //true
true == "1"  //true
null == 0  //false
```

* Undefined衍生自null，所以两者做相等判断时，结果为Ture

```javascript
undefined == null //true
```

- NaN不和任何值相等，包括它本身
- 可以通过isNaA()函数判断是否是NaN，如果是，返回true，否则，返回false

```javascript
NaN == NaN  //false
isNaA(b)
```

##### !=：不相等判断

- 不相等判断时也会对变量进行自动的类型转换，如果转换后相等，则返回false

```javascript
1 != "1" //false
```

##### ===：用来判断两个值是否全等

* 不会做自动类型转换，如果两个值的类型不同，则直接返回false

```javascript
1 === "1"  //false
```

##### !==：用来判断两个值是否不全等

* 不进行类型转换，如果类型不同，则返回true

#### **8.条件运算符**

**语法： 条件表达式?语句1:语句2**

条件运算符在求值时，首先对条件表达式进行求值，如果结果为true，则执行语句1，否则，执行语句2

如果条件表达式的结果是一个非布尔值，会将其转化为布尔值，然后再继续进行运算

```javascript
var max = a > b? a:b  //获取a和b中的最大值

var max = a > b? (a > c ? a : c):(b > c ? b : c)  //获取a\b\c中的最大值
```

**9.运算符的优先级**

,——可以用来分割多个语句

```javascript
var a,b,
```

* 先乘除，后加减

### 三、语句

#### 1.基本概念

* js中可以用{}来为语句分组，同一个大块中的语句为一组语句，他们要么都执行，要么都不执行，{}中的语句又称为一个代码块，在代码块的后面，不需要编写;
* js中的代码块只具有分组的作用，没有其他的功能——代码块内部的内容，在外部是完全可见的

#### 2.流程控制语句

* 条件控制语句

（1）在执行某个语句之前进行判断，如果条件成立就执行语句，如果条件不成立就不执行，如果条件表达式的值为true，就执行if后的语句，如果条件表达式的值为false，就不执行if后的语句

```javascript
if(条件表达式)
    语句;
```

（2）if语句只能控制紧随其后的语句/代码块

（3）if……else if……else if语句只能执行其中一个代码块

#### 3.输入函数prompt()

可以弹出一个提示框，该提示框中会带有一个文本框，用户可以在文本框中输入一段内容，该函数需要一个字符串作为参数，该字符串将会作为提示框的提示文字

* 用户输入的内容将会作为函数的返回值返回，可以定义一个变量来接收该内容
* 返回值为String类型

```
var a = prompt("请输入第一个数")
```

#### 4.条件分支语句switch

语法结构

```
switch(条件表达式)
{
    case 表达式：
        语句
        break;  //退出switch语句
    case 表达式：
        语句
        break;
    case 表达式：
        语句
        break;
    case 表达式：
        语句
        break;
    default:
        语句
        break;
}
```

执行时会依次将case后的表达式的值与switch后的条件表达式进行全等比较，如果比较结果为true，如果比较结果为true，则从当前case开始执行代码（当前case后的代码都会被执行，加上break才会终止代码）；如果所有的比较结果都是false，则只执行default后的语句

#### 5.while循环

`document.write(1+"<br/>")  //<br/>标签可以实现在网页中换行`

while语句可以反复执行一段代码多次

语法：

```
while（条件表达式）
{
    循环体
}
```

在执行时，先对条件表达式进行求值判断，如果值为true，则执行循环体，循环体执行完毕后，继续对表达式进行执行判断

- 循环的三个步骤
  - 初始化一个变量
  - 在循环中设置一个条件表达式
  - 定义更新表达式

```
//1.初始化一个变量
var i =0;
//2.在循环中设置一个条件表达式
while(i<10)
{
     alert(i);
     //3.定义一个更新表达式，每次更新初始化变量
     i++;
}
```

```
do{
    语句
}while（条件表达式）
```

do-while语句在执行时，会先执行循环体，循环体执行完毕后，在对while后的条件表达进行判断，如果为true，则进行下一次的执行

#### 6.for循环

```
for (var i = 10;i<10;i++)
{
    alter(i);
}
```

判断是否是质数

```
var flag = true

//获取2-num之间的数字
for(var i = 2;i<num;i++)
{
    if(num % i == 0){ 
        //不是质数
        flag = flase;
      }
}
    if(flag)
    {  //flag 始终没有被标记为false，则为质数
        alter(num + "是质数");
    }else
    {  alter(num + "不是质数");
    }
```

`空格：&nbsp`

#### 7.break和continue

##### break：可以用来退出switch或循环语句

- <u>if语句中不可使用break和continue</u>（循环中if判断的break是对循环起作用，而不是对if语句起作用）
- break会立即终止离他最近的那个循环语句
- 可以为循环语句创建一个label，来标识当前的循环

- label语句可以与break语句结合起来使用，用来说明是终结哪一层循环

循环语句——使用break语句时，可以在break后面加一个label，这样break会结束指定的循环，而不是最近的

```
outer:
for (var i=0;i<5;i++)
{
    for(j =0;j<5;j++)
    {
        break outer;    //终结的是outer循环
    }
}
```

##### continue:跳过当次循环

- 默认只会对离他最近的循环起作用

```
//使用break进行质数判断的例子
var flag = true

//获取2-num之间的数字
for(var i = 2;i<num;i++)
{
    if(num % i == 0){ //不是质数，不需要再继续进行判断
        flag = flase;
        break;
      }
}
    if(flag)
    {  //flag 始终灭有被标记为false，则为质数
        alter(num + "是质数");
    }
    else
    {  alter(num + "不是质数");
    }
```

【问题】测试代码的执行时间

```
//在程序开始前，开启计时器
//console.time("计时器的名字")函数需要一个字符串作为参数，这个参数会作为计时器的标识
//在程序的前后调用计时器工具，即可实现计时的功能
console.time("test") 
……程序……
//终止计时器
console.timeEnd("test") 
```

【问题】打印2-100之间所有的质数

```
for(var num=2;num<=100;j++)
{
    var flag = true

//获取2-根号num之间的数字
//使用根号计算的时候用到了math对象
for(var i = 2;i<Math.sqrt(num);i++)
{
    if(num % i == 0){ //不是质数，不需要再继续进行判断
        flag = flase;
        break;
      }
}

    if(flag)
    {  //flag 始终没有被标记为false，则为质数
        alter(num + "是质数");
    }else
    {  //alter(num + "不是质数");
        continue;
    }
}
```



### 四、对象

#### 1.对象的基本概念

**对象属于一种复合的数据类型，在对象中可以保存多个不同数据类型的属性。**

对象是属性和方法的集合。

（注意：这里的对象不是Object数据类型，而是外延更广的概念）

**对象的分类**：

##### （1）内建对象

由ES标准中定义的对象，在任何的ES的实现中都可以使用。

比如：Math/String/Number/Boolean/Function/Object

##### （2）宿主对象

由ES的运行环境提供的对象，由浏览器提供的对象

比如BOM DOM

console.log()、document.write()中的console和document

##### （3）自建对象

由开发人员自己创建的对象

#### 2.对象的基本操作

* 创建对象

```
//使用new关键字调用的函数，是构造函数constructor，是专门用来创建对象的函数
//使用typeof检查一个对象时，会返回object
var obj = new Object();
/*
 * 在对象中保存的值称为属性
 * 向对象添加属性
 * 语法 对象.属性名 = 属性值;
 */
//向obj中添加三个属性
obj.name = "孙悟空";
obj.gender = "男";
obj.age = "18";
```

* 读取对象中的属性

语法： 对象.属性名

```
obj.name
```

* 修改细项中的属性值

语法：对象.属性名="新值"

```
obj.name = "tom"
```

* 删除对象的属性

语法： delete 对象.属性名

```
delete obj.name
```

#### 3.属性名和属性值

属性名：

- 对象的属性名不强制要求遵循标识符的规范
- 如果要使用特殊的属性名，不能采用.的方式来操作，需要使用另一种方式

   语法： 对象["属性名"] = 属性值 （存取的方式应该相同）

   使用这种方式去操作属性，更加灵活，在[]中可以直接传递一个变量，这样变量值是多少就会读取那个属性

```
obj["123"] = 789

//等效
var n = "123"
obj[n] = 789
```

属性值：

js对象的属性值，可以是任意的数据类型，甚至也可以是一个对象

```
obj.test = "hello"
obj.test = 123
obj.test = true
obj.test = null
obj.test = undefined

var obj2 = new Object()
obj2.name = "猪八戒"
obj.test = obj2;
obj.test.name  //猪八戒
```

in 运算符：

通过该运算符可以检查一个对象中是否含有指定的属性，如果有，则返回true，如果没有，则返回false

语法：  "属性名" in 对象

```
//检查obj中是否有test1
"test2" in obj
```

#### 4.**基本数据类型和引用数据类型**

内存包括：栈内存和堆内存

- js中所有的变量都是保存在栈内存中的，基本数据类型的值直接在栈内存中存储，值与值直接独立存在，修改一个变量，不会影响其他变量
- 对象保存在堆内存中

（1）对象的<u>名字</u>保存在<u>栈内存</u>中，对象的<u>内容</u>保存在<u>堆内存</u>中，该内容的地址表存在对象的名字对应的栈内存下，每创建出一个新的对象，就会在堆内存中开辟出一个新的空间，而<u>变量值保存的是对象内存的地址（对象的引用）</u>

（2）如果两个变量保存的是同一个对象的引用，当通过一个变量修改属性时，另一个也会受到影响。如果直接修改变量的值，则不会受到影响。

（3）比较两个引用数据类型时，<u>比较的是对象的内存地址</u>，如果是内容完全相同的两个对象（但地址不同），在进行判断的时候结果为false，因为其实质为两个对象

#### 5.对象字面量

使用对象字面量来创建一个对象（本质上与new方法一样）

- 使用对象字面量可以在创建对象时直接指定对象的属性。
- 对象字面量的属性值可以加引号也可以不加，建议不加
- 如果要使用特殊的作为属性名，则必须加引号
- 属性名和属性值是一组一组的名值对结构，名和值之间使用:连接，多个名值对之间使用,隔开，如果一个属性之后没有其他的属性，则不需要写逗号

```
var obj = {name:"猪八戒",  //"name":"猪八戒"
           age:28,
           gender:"男",
           test:{name:"沙和尚"}
};
```

### 五、函数

#### 1.简介

- 函数也是一个<u>对象</u>
- 函数中可以封装一些功能（代码），在需要时可以执行这些功能（代码）
- 函数中可以保存一些代码在需要的时候调用
- 使用typeof检查一个函数对象时，会返回function

#### 2.创建一个函数对象

方法一：构造函数，形参是新函数对象将要封装的代码以字符串的类型

```
var fun = new Function("js代码");
```

- 封装到函数中的代码不会立即执行，函数中的代码会在函数调用的时候执行
- 调用的语法： 函数对象+()
- 当调用函数时，函数中封装的代码会按照顺序执行

```
fun()
```

函数本身具有普通对象所有的功能，但是比普通对象更加强大，因为其中可以封装代码。



方法二：使用函数声明来创建一个函数对象（在实际开发中很少使用方法一种的构造函数来创建一个对象）

语法：

​     function 函数名([形参1，形参2...形参n]){

​     语句

​     }

```
function fun2(){
     console.log("这是第二个函数");   
}
```

方法三：使用函数表达式来创建一个函数

语法：

​     var 函数名=function([形参1，形参2...形参n]){

​     语句

​     }

```
var fun3 = function(){
    console.log("我是函数3中封装的代码");
};
```

#### 3.函数的返回值

可以使用return来设置函数的返回值

语法：

​     `return 值`

- return后的值将会作为函数的执行结果返回
- return后的语句都不会执行
- 如果return语句后不跟任何值，就相当于返回一个undefined，如果函数中不写return，则也会返回一个undefined
- return后可以跟任何类型的值，也可以是一个对象，可以是一个函数

```
function fun(){
    var obj = {name:"aaa",age:18};
    return obj;  //返回一个对象
}

var a = fun();
console.log(a.name)
```

```
function fun(){
     function fun1()  //在函数内部再声明一个函数
    {   alter("我是fun1");
    }

    //fun1();//调用函数
    return fun1; //将fun1()作为函数返回值返回
    //return fun1();//将fun1()的返回值作为fun()的函数返回值返回
}

var a = fun()
a();// 此时由于a就是fun1,调用a相当于调用fun1()
```

#### 4.立即执行函数

往往只能执行一次

```
//定义匿名函数
(function(){
    alter("这是一个匿名函数")
})

//立即执行匿名函数
(function(a,b){
    alter("这是一个匿名函数")
})(123,456);
```

#### 5.方法

函数也可以成为对象的属性，如果一个函数作为一个对象的属性保存，那么称这个函数是这个对象的方法，调用函数等效于调用对象的方法（method）

```
var obj = new Object();

//向对象中添加属性
obj.name = "孙悟空";
obj.age = 18;

//对象的属性值可以是任何的数据类型，也可以是个函数
//用函数表达式的方法来创建一个函数，该函数是对象的方法
obj.sayName = function(){
    console.log(obj.name);
}
```

```
var obj2={
    name:"孙悟空",
    age:18,
    sayName:function(){
        console.log(obj2.name);
    }
};

obj2.sayName()  //调用obj2的名字为sayName的方法
```

#### 6.枚举对象中的属性

语法：

  for(var 变量 in 对象){

​     }

for...in语句 对象有几个属性，循环体就会执行几次，每次执行时，会将对象中的一个<u>属性的名字</u>赋值给变量

```
var obj = {
    name:"孙悟空",
    age:18,
    gender:"男"
};

for(var n in obj){
  //n依次为name,age,gender
    console.log(obj[n]);  //不能用obj.n的方式查属性值
}
```

#### 7.作用域

##### （1）全局作用域

直接在script标签中的js代码，全都在全局作用域

- 全局作用域在页面打开时创建，在页面关闭时销毁
- 在全局作用域中，有一个全局对象window，代表的是浏览器的窗口，由浏览器创建，可以直接在界面中使用
- 在全局作用域中，创建的变量都会作为window对象的属性保存；创建的函数都会作为window对象的方法保存

```
var a = 10;
console.log(window.a);  //10

function fun(){
    console.log("hello");
}
window.fun();
```

**变量的声明提前**

- 使用var关键字声明的变量会在所有的代码执行之前被声明（但是不会赋值），但是如果声明的时候不使用var关键字，则不会进行声明提前

**函数的声明提前**

- 使用<u>函数声明形式</u>创建的函数function(){}，在代码执行之间就已经被声明，所以可以<u>在函数声明前调用函数</u>
- 使用函数表达式创建的函数var fun = function(){}不会被声明提前，所以不能在声明前调用

```
console.log(a);

var a = 123; //undefined
a = 123;   //报错
__________________________
fun();  //函数声明的方式定义函数时，如果在函数声明之前调用函数，正常调用

function fun(){
    console.log("hello");
}
--------------------------------------------------
fun2();   //函数表达式的方式定义函数时，如果在函数声明之前调用函数，报错
var fun2 = function(){
        console.log("hello2");
}
```

全局作用域中的变量都是全局变量，在页面的任意部位都可以被看到

##### （2）局部作用域

调用函数时创建函数作用域，函数执行完毕后，函数作用域销毁，每调用一次，函数就会创建一个新的函数作用域，他们之间是相互独立的

- 在函数作用域中可以访问到<u>作用域为全局的变量</u>，在全局作用域中，无法访问函数作用域的变量
- 当在函数作用域中操作一个变量时，会先在自身的作用域中寻找，如果有，就直接使用，如果没有，就向上一级的作用域（不一定是全局）中寻找，直到找到全局作用域，如果全局作用域没有找到，则会报错
- 在函数作用域中也有声明提前的特性，使用var关键字声明的变量，会在函数中所有的代码执行之前被声明，函数声明也会在函数中所有的代码执行之前被执行（函数的作用域可以看做是一个小的全局）

```
var a = 10; //全局作用域的变量
function fun(){
    var a = 20;
    console.log("a="+a); //a = 20
    function fun2(){
        console,log("a="+a);
    }
}
fun();
```

* 在函数中不使用var声明的变量，都会成为全局变量

```
var c = 33;
function fun(){
    console.log("c="+c); //c=33，函数作用域的c没有用var，所以去上一层找
    c = 10;  //10的赋值对象是全局变量c
   // var c = 10;//c是局部变量
}
fun();
console.log("c="+c); //c = 10，此时c已经在函数中完成了赋新值的操作
```

#### 8.this

解析器在调用函数时每次都会向函数内部传递一个隐含的参数，this。this指向的是一个对象，这个对象我们称为执行的上下文对象。<u>根据函数调用方式的不同</u>，this会指向不同的对象。

（1）以函数的形式调用，this永远指向Window

（2）以方法（对象内部的函数属性是方法）的形式调用，this指向方法所存在的对象中

```
function fun(){
    console.log(this);
}

var obj = {
    name:"孙悟空",
    sayName:fun
}

fun();   //[Window]
obj.sayName();  //fun函数是obj内部的方法，this指向fun方法所存在的对象中，即[obj]
```

#### 9.使用工厂方法创建对象

用于大批量创建对象

```
function createPerson(name,age,gender){
    //第一步：创建一个新的对象  
    var obj = new Object();

    //第二步：向对象中添加属性
    obj.name = name;
    obj.age = age;
    obj.gender = gender;
    obj.sayName = function(){
        alter(this.name)
    };

    //第三步：将新的对象返回
    return obj;
}

var obj1 = createPerson("孙悟空",18,"男")
var obj2 = createPerson("猪八戒",20,”男")
```

使用工厂方法创建的对象，使用的构造函数都是Object,所以所有创建的对象都是Object类型，无法区别不同的类别。

#### 10.构造函数

- 构造函数就是一个普通的函数，**创建方式和普通函数没有区别**，不同的是构造函数习惯上**首字母大写**。
- 构造函数和普通函数的区别是调用方式的不同，普通函数是直接调用，**构造函数需要使用new关键字来调用**。
- 执行流程：

（1）调用构造函数时，会自动立即创建一个新的对象（省去了工厂方法的第一步）

（2）<u>将新建的对象设置为函数中的this，在构造函数中，可以使用this来引用新建的对象</u>

（3）逐行执行函数中的代码

（4）将新建的对象作为返回值返回

- 使用同一个构造函数构造的对象，称为一类对象，我们将通过构造函数创建的对象，称为是该类（该构造函数）的实例。
- 使用instanceof可以检查某一个对象是否是一个类的实例，如果是，则返回true，否则返回false。<u>所有的对象都是Object的后代，任何对象在进行instanceof判断时，结果都为true。</u>

```
function Person(name,age,gender){
    this.name = name ;
    this.age = age;
    this.gender = gender;
    this.sayName = function(){
        alter(this.name)
    };
}

var per1 = new Person("孙悟空",18,"男")  
var per2 = new Person("猪八戒",28,"男")
var dog1 = new Dog()

console.log(per1 instanceof Person)  //true
console.log(dog instanceof Person)  //false
console.log(dog instanceof Object)  //true
```

- 总结：this

1.当以函数的形式调用时，this是Window

2.当以方法的形式调用时，this就是调用该方法的对象

3.当以构造函数的方式调用时，this就是创建的对象

```
//在Person构造函数中，为每一个对象都创建了sayName方法，构造函数每执行一次，就需要创建一个sayName方法，即每一个sayName方法不同。但其实质相同，完全可以使所有的对象共享一个方法。
function Person(name,age,gender){
    this.name = name;
    this.age = age;
    this.gender = gender;
    this.sayName = function(){
        alter(this.name);
    }        
}

var per1 = ("孙悟空",18,"男")

//解决：将sayName方法在全局作用域中定义
//弊端：将函数定义在全局作用域，污染了全局作用域的命名空间，而且定义在全局作用域中很不安全
var fun = function(){
        alter(this.name);
    }   
     
function Person(name,age,gender){
    this.name = name;
    this.age = age;
    this.gender = gender;
    this.sayName = fun;
}
```

### 六、原型

#### 1.原型（prototype）的定义

我们所创建的每一个函数，解析器都会向<u>函数中</u>添加一个<u>属性prototype</u>，这个属性对应了一个对象，这个对象就是所谓的原型对象。

- 如果函数作为普通函数调用，prototype没有任何作用
- 如果函数作为构造函数调用，它所创建的对象中都会有一个隐含的属性指向该构造函数的原型对象，我们可以通过`__proto__`来访问该属性

```javascript
//创建构造函数
function MyClass(){

}
//用new语句来调用函数，创建实例instance
var mc = new MyClass();
// 访问原型属性
console.log(mc.__proto__);
```

* 原型对象相当于一个<u>公共</u>的区域，所有同一个类的实例都可以访问到原型对象，我们可以将对象共有的内容统一设置到原型对象中。由同一个构造函数创建的实例中都有一个共同的原型对象。在构建函数时，可以将对象共有的属性/方法，统一添加到构造函数的原型对象中，这样不需要为每一个对象分别添加，也不会影响到全局作用域，就可以是的每一个对象都具有该属性和方法。

* 当访问对象的一个属性或者方法时，会现在对象自身中查找，如果有，就直接使用；如果没有，就去原型对象中查找

* ```javascript
  //在prototype中给a属性赋值，并访问
  MyClass.prototype.a = 123  
  console.log(mc.a)  //123
  
  //在prototype属性范围之外的区域中给a属性赋值，并访问
  mc.a = "我是mc中的a";
  console.log(mc.a)  //我是mc中的a
  
  //向MyClass中的原型对象中添加一个方法，可以使得所有的对象都拥有该方法
  MyClass.prototype.sayHello = function(){
          alter("hello");
  }
  ```

* 使用in语句检查对象是否含有某个属性，如果对象中没有但是原型中有该属性，最后结果也是返回true
* 对象名.hasOwnProperty("属性名")——用于检查对象自身中是否含有该属性，只有对象自身中含有该属性时，才会返回true（需要注意的是，原型对象也有原型对象，该方法本身在原型对象的原型对象中）

总结：原型对象也是对象，所以它也有原型，当我们使用一个对象的属性或方法时，会先在自身中查找，如果自身中有需要查找的内容，就直接使用，如果没有，就去原型对象中寻找；如果原型对象中油，就直接使用，如果原型对象中没有，就去原型对象的原型汇总寻找，直到找到object对象的原型，object对象的原型没有原型，如果在该位置仍然没有找到，就返回undefined

#### 2.toString()

- 当我们直接在页面打印一个对象时，实际上是print输出对象的toString()方法的返回值
- 该方法在原型的原型（Objcy的原型）中
- 如果我们希望在输出对象时不输出[obkect Object]，可以为对象添加一个toString()方法，覆盖掉默认的toString()方法，返回指定的，需要打印的内容

```javascript
//修改Person原型的toString可以实现在所有的对象中都实现目标功能
//此时如果再直接打印person对象，则不会输出默认对象的返回值，而是输出设定的返回值
Person.prototype.toString = function(){
    return "Person[name="+this.name+",age="+this.age+",gender="+this.gender+"]";
}
```

#### 3.垃圾回收机制

程序运行过程中产生的垃圾会使得程序运行速度过慢，所以我们需要垃圾回收的机制来处理程序运行过程中产生的垃圾。

- 当一个对象没有任何的变量或者属性对其进行引用，此时我们将无法操作该对象，此时该对象就是垃圾。这种类型的对象过多会占有大量的内存空间，导致程序运行变慢。所以这种垃圾必须进行清理。
- 在js中拥有自动的垃圾回收机制，会自动将垃圾对象从内存中销毁因此我们不需要也不能够进行垃圾回收的操作。我们需要的是将不会再使用的对象设置为null。

```javascript
var obj = new Object();
//对对象进行各种操作
obj = null;  //没有用处的对象，浏览器将会对其进行回收
```

### 七、数组

#### 1.简介

数组也是一个<u>对象</u>，与普通的对象功能类似，用于存储一些值，不同的是普通对象是使用<u>字符串作为属性名</u>，而数组是使用<u>数字作为索引操作元素</u>

- 索引：从0开始的整数（从功能上来看，数组的数字索引与普通对象的属性名是相同的）
- 数组的存储特性比普通对象好
- 使用typeof检查一个数组时，会返回object

```javascript
//数组的构造函数
var arr = new Array(); 
//创建后在数组中添加元素，将要添加的元素作为参数传递
var arr = new Array(1,2,3); 
```

##### (1)添加元素

语法：

`数组[索引]=值`

**数组[索引]=值（普通对象：对象名.属性名=属性值；对象名["属性名"]=属性值）**

```javascript
arr[0]=10
```

##### (2)读取元素

语法：

**数组[索引]**

* 如果读取的索引并不存在，此时不会报错，而是返回undefined

##### (3)获取数组的长度

使用数组对象汇总的length属性来获取数组的长度（元素的个数）

语法：

**数组.length**

* 对于连续的数组，可以获得元素的个数
* 对于非连续的数组，获取到数组的最大索引+1

##### (4)修改数组的长度

如果修改后的长度大于原长度，则空出；如果修改后的长度小于原长度，则多出的元素会被删除

```javascript
arr.length = 10
```

##### (5)在数组的最后一个位置添加元素

语法：

**数组[数字.length] = 值** 

```javascript
arr[arr.length] = 80;
```

##### (6)使用字面量来创建数组

语法：

**var 数组名=[(数组元素)]**

- 在创建的时候就指定数组中的元素

```javascript
//创建一个只含有一个元素10的数组
arr = [10];  
//创建一个长度为10的数组
arr2 = new Array(10);  
```

- 数组中的元素可以是任意的数据类型，可以是一个对象，也可以是一个函数

```javascript
var obj = {name:"孙悟空"}
var arr = []
arr[arr.length] = obj;
——————————————————————————————————————————————————————————————
var arr=[{name:"孙悟空"},{name:"孙悟空"},{name:"孙悟空"}]
var arr = [function(){},function(){},function(){}]
arr[0]();  //对第一个位置的函数进行调用
——————————————————————————————————
arr = [[1,2,3],[4,5,6],7,8,9]]  //数组中也可以放数组（二维数组）
```

#### 2.数组的方法

##### (1)push()

该方法可以用来向数组的末尾添加一个或者多个元素。并返回数组的新的长度。

* 可以将要添加的与萨努作为方法的参数传递，这样元素将会自动添加到数组的末尾

```javascript
var result = arr.push(4,5,6)
//result = 6(新长度)
//arr = [1,2,3,4,5,6]
```

##### (2)pop()

删除并返回数组中的最后一个元素，并将删除的元素作为返回值返回

```javascript
var result = arr.pop()
//result = 6
//arr=[1,2,3,4,5]
```

##### (3)unshift()

向数组的开头添加一个或者多个元素，并返回新的数组长度

* 向前面加入元素后，其他位置的元素会一次调整
* 返回值是数组新的长度

```javascript
arr.unshift(0)
//arr=[0,1,2,3,4,5]
```

##### (4)shift()

删除数组的第一个元素，并将被删除的元素作为返回值返回

```javascript
var result = arr.shift()
//arr = [1,2,3,4,5]
//result = 0
```

##### (5)slice()

从某个已有的数组返回选定的元素。该方法不会改变原有的数组，而是将截取到的元素封装到一个新的数组中返回。

语法：

**arr.slice(start, end)**

**start: 截取开始的位置，包含开始的元素**

**end：截取结束的位置，不包含结束的元素**

- 第二个参数可以省略不写，此时会截取从开始索引往后的所有元素
- 索引可以传递一个负值，如果传递一个负值，表示从后往前计算-1, -2, -3

```javascript
var arr = [1,2,3,4,5]
var result = arr.slice(0,2)
//result = [1,2]

var result = arr.slice(1,-1)
```

##### (6)splice()

删除元素并向数组添加新的元素。使用splice会影响到原数组，会将指定元素从原数组中删除，并将被删除的元素作为返回值返回

参数：

(1)第一个参数：开始位置的索引

(2)第二个参数：删除的数量

(3)第三个以后的参数可以传递添加的新的元素，这些元素将自动插入到开始位置的索引位置之前

```javascript
// 删除位于第一个位置的两个元素，并添加元素“88”
var arr = [1,2,3,4,5]
var result = arr.splice(0,2,"88")
//arr = [88,3,4,5]
//result = [1,2]
```

```javascript
//元素去重练习
//获取数组中的每一个元素

for(var i = 0;i<arr.length,i++){
    //获取当前元素后的每一个元素
    for(var j = i+1;j<arr.length.j++){
        //判断两个值是否相等
        if(arr[i] == arr[j]){
        //如果相等，则出现了重复元素，则删除j对应的元素
            arr.splice(j,1);
        //当删除了当前j所在的元素之后，后边的元素会自动补位，此时不会再比较这个元素
        //应当再比较依次当前的元素，使j自减
            j--;
        }
    }
}
```

##### (7)concat()

可以连接两个或者更多的数组，并将新的数组返回。该方法不会对原数组产生影响。

```javascript
var result = arr.concat(arr2,arr3,"666");
```

##### (8)join()

该方法可以将数组转换为字符串。该方法不会对原数组产生影响，而是将转换后的字符串作为结果返回。字符串中的元素以逗号分隔。

* 在join()中可以指定字符串作为参数，这个参数会成为数组中元素的连接符。如果不指定连接符，就默认以","作为连接符

```javascript
var result = arr.join("--")
```

(9)reverse()

该方法用来翻转数组。该方法会<u>直接修改原数组。</u>

```javascript
arr.reverse();
```

(10)sort()

对数组中的元素进行排序。该方法会直接修改原数组。默认按照Unicode编码进行排序。

* 即使对于纯数字的数组，在使用sort()方法进行排序时，也会按照Unicode的标准进行排序，所以在进行数字排序时，可能会得到错误的结果，因此应当自己制定排序的规则。可以在sort中添加一个回调函数，用来指定函数规则，其中需要定义两个形参，浏览器将会分别使用数组中的元素去调用回调函数。使用哪个元素调用并不确定，但是a在的位置之前
* 浏览器会根据回调函数（作为参数传递的函数）的返回值来确定元素的顺序。如果返回一个大于0的值，则元素会交换顺序；如果返回一个小于0的值，则元素位置不变；如果返回一个等于0的值，则认为两个元素相等，也不交换位置
* 如果需要升序排列，返回a-b，如果需要降序排列，返回b-a

```javascript
arr.sort();

arr.sort(function(a,b){
    if(a>b){ //升序
        return 1;
    else if(a<b){
        return -1;
    else{
        return 0;
    }

    //升序的另外一种写法：
   return a-b;
    //降序的另外一种写法：
    return b-a;
});
```

#### 3.数组的遍历

所谓遍历数组就是将数组中的所有元素都取出。

(1)for 循环遍历

```javascript
var arr = [1,2,3,4];
for(var i = 0;i<arr.length;i++){
    console.log(arr[i]);
}
```

(2)forEach的方法进行遍历（IE8以上的浏览器）

- 需要一个函数作为参数——这种函数，由我们创建但是并不是由我们调用，成为回调函数
- 数组中有几个元素，该函数就执行几次，每次执行时，浏览器会将遍历到的元素以实参的形式传递进来，我们可以通过定义形参来读取这些内容
- 浏览器会在回调函数中传递三个参数
  - 第一个：当前遍历到的元素
  - 第二个：当前遍历到的索引值
  - 第三个：被遍历的数组

```javascript
arr.forEach(function(value,index,obj){
    console.log(value);
    console.log(index);
});
```

### 八、函数的方法

#### 1.call()和apply()方法

这两个方法都是函数对象的方法，需要通过函数对象来调用。当对函数对象调用call()和apply()，该函数都会被调用执行。

* 在调用call()和apply()可以将一个对象指定为第一个参数，此时这个对象将会成为函数执行时的this
* call()方法可以在实参对象之后依次传递
* apply()方法需要将实参封装到数组中，再统一进行传递

```javascript
var obj={
    name:"obj"
};
        
function fun(a,b){
    alter(this);
    alter(a+b);
}

fun.call();
fun.apply();

fun.call(obj,2,3);  
fun.apply(obj,[2,3]); 
```

关于this用法的总结：

(1)以函数形式调用时，this是Window

(2)以方法形式调用时，this是调用该方法从属的对象

(3)以构造函数的形式调用时，this是当前正在创建的新对象

(4)使用call和apply调用时，this是参数所指定的对象

#### 2.arguments

在调用函数时，浏览器每次都会传递两个隐含的参数：

(1)函数的上下文对象this

(2)封装实参的对象arguments

* arguments是一个类数组对象（并不是数组），它也可以通过索引来操作数据，也可以获取长度
* 在调用函数时，我们所传递的实参都会在argument中保存
* argument.length可以用来获取实参的长度
* 即使不定义形参，也可以通过argument来使用实参，argument[0]表示第一个形参
* arguments其中有一个属性，这个属性对应一个函数对象，就是当前正在指向的函数对象

```javascript
function fun(){
    console.log(arguments.length);  //3
    console.log(argumets[0]); //1
    console.log(arguments.callee); //function(){函数内容}
}

fun(1,2,3); 
```

### 九、Date对象 Math对象 包装类

#### Date对象

用来表示一个时间

##### 1.创建对象

* Date()函数是构造函数

```javascript
// 无参数创建Date对象
// 如果直接使用构造函数创建一个对象，则会封装为当前代码执行的时间
var d = new Date();
var d2 = new Date();

//创建一个指定的时间对象
//需要在构造函数中传递一个表示时间的字符串作为参数
//日期的格式：月份/日/年 时:分:秒
var d = new Date();
var d2 = new Date("12/03/2016 11:10:30");

console.log(d);  //输出当前的时间
console.log(d2); //输出指定的时间
```

##### 2.Date的方法(注意使用方法前首先要创建对象实例)

- getDate()

获取当前日期对象是几日

```javascript
var date = d2.getDate();
console.log(date);  //13
```

- getDay()

获取当前的日期是周几。返回0~6的值，0表示周日。

```javascript
var day = d2.getDay();
console.log(day);  //2
```

- getMonth()

获取当前时间对象的月份，返回0~11的值

```javascript
var month = d2.getMonth();
console.log(month);  //11
```

* getFullYear()

获取当前日期对象的年份

```javascript
var year = d2.getFullYear();
console.log(year);  //2016
```

- getTime()

获取当前日期对象的时间戳。【时间戳：指的是从格林威治时间的1970年1月1日，0时0分0秒所花费的毫秒数。（1秒=1000毫秒）计算机底层在保存时间时，使用的都是时间戳。】

```javascript
var time = d2.getTime();
console.log(time);

//获取当前的时间戳
time = Date.now();

//可以利用时间戳来测试代码的执行性能
time1 = Date.now();
function fun(){}
time2 = Date.now();
console.log(time2-time1);
```

#### Math对象

它不是一个构造函数，而是一个工具类，<u>不需要创建对象</u>，其中封装了数学运算相关的属性和方法

比如：

Math.PI表示圆周率

abs()可以用来计算一个数的绝对值

ceil()可以对一个数进行向上取整，小数位只要有值，则自动进1

floor()可以对一个数进行向下取整，小数部分会被舍掉

round()可以对一个数进行四舍五入取整

random()可以用来生成一个0~1之间的随机数，不会出现0，也不会出现1

* 生成0-x之间的随机数Math.round(Math.random()*x)
  生成x-y之间的随机数Math.round(Math.random() * (y-x)+x)

```javascript
console.log(Math.PI)
console.log(Math.abs(33))
console.log(Math.ceil(1.4)) //2
console.log(Math.floor(1.4)) //1
console.log(Math.random())
```

max(x,y,……)可以获取多个数中的最大值，并返回

min(x,y,……）可以获取多个数中的最小值，并返回

pow(x,y)返回x的y次幂

sqrt(x)开x次方

#### 包装类

在JS中，有三个包装类，通过这三个包装类可以将基本类型的数据转换为对象。

注意：在实际应用时，不会使用基本数据类型的变量。如果使用基本数据类型对象，在做比较的时候可能会出现不可预期的结果。

* String()

可以将基本数据类型字符串转换为String对象

```javascript
var str = new String("hello");
```

- Number()

可以将基本数据类型的字符转变为Number对象

```javascript
var num = new Number(3);

//向num中添加一个属性
num.a = "123";
```

* Boolean()

可以将基本数据类型字符串转换为Boolean对象

```javascript
var bool = new Boolean(true);
```

当我们对一些基本数据类型调用一些属性和方法时（比如toString）,浏览器会临时使用包装类将其转换为对象，然后调用对象的属性和方法。在调用完成后，再将其转变为基本数据类型的变量。

### 十、字符串的相关方法

```javascript
//创建一个字符串
var str = "hello world";
```

在底层，字符串是以字符数组的形式保存的。

#### 1.length属性

可以用来获取字符串的长度

```javascript
console.log(str.length)	//获取字符串的长度
```

#### 2.charAt()

可以返回字符串中指定位置的字符

```javascript
// 返回第一个位置的字符
var result = str.charAt(0);
// 返回第七个位置的字符
var result = str[6];
```

#### 3.charCodeAt()

获取指定位置字符的字符编码（Unicode编码）

```javascript
// 获取第七个位置的字符编码
result = str.charCodeAt(6)
```

#### 4.fromCharCode()

根据字符编码（十进制）去获取字符

```javascript
// 获取十进制下字符编码为72的字符
result = String.fromCharCode(72);  //H
```

#### 5.concat()

可以用来连接两个或者多个字符串，作用和加号相同，对原字符串不会产生任何影响

```javascript
result = str.concat("你好","再见");
```

#### 6.indexOf()

该方法可以检索一个字符串中是否含有指定的内容

* 如果字符串中含有该内容，则会返回其第一次出现的索引
* 如果没有找到指定内容，则返回-1
* 可以指定一个第二个参数，指定开始查找的位置

```javascript
str = "hello hworld";
result = str.indexOf("h"); //0
result = str.indexOf("h",1);  //6
```

#### 7.lastIndexOf()

该方法的用法和indexOf相同，不同的是indexOf()是从前向后查找，而lastIndexOf()是从后向前查找

* 可以指定开始查找的位置

#### 8.slice()

可以从字符串中截取指定的内容。不会影响原字符串，而是将截取的内容返回。

* 第一个参数是开始位置的索引（包括开始位置）
* 第二个参数是结束位置的索引（不包括结束位置）。如果省略第二个参数，则会截取后面所有的内容，直到末尾
* 也可以传递一个负数作为参数，意思是从后向前的索引值

```javascript
str = "abcdefghijk";
str.slice(0,2);
```

#### 9.substring()

可以用来截取一个字符串，和slice()类似

* 第一个参数是开始位置的索引（包括开始位置）
* 第二个参数是结束位置的索引（不包括结束位置）
* 与slice参数不同的是，这个方法不能接受负数作为参数，如果传递了负值，则默认转换为0
* 这个方法会自动调整参数的位置，如果第二个参数小于第一个，则自动交换

```javascript
str = "abcdefghijk";
str.slice(0,2);
```

#### 10.substr()

用来接触字符串

参数：

* 截取开始位置的索引
* 截取的长度

#### 11.split()

可以将字符串拆分成为一个数组

参数：

* 需要一个字符串作为数组的分界，将会根据字符串去拆分数组
* 如果传递一个空串作为范式，则会将灭一个字符都拆分为数组中的元素

```javascript
str = "abc,bcd,efg,hig"
result = str.split(",");
result = str.split(""); //[a,b,c,]
```

#### 12.toUpperCase()

将一个字符串转换为大写，并返回

#### 13.toLowerCase()

将一个字符串转换为小写，并返回

### 十一、正则表达式

#### 1.简介

正则表达式用于定义一些字符串的规则，计算机可以根据正则表达式来检查一个字符串是否符合规则，或者将字符串中符合规则的内容提取出来

##### (1)使用构造函数创建正则表达式

**语法：**

**var 变量 = new RegExp("正则表达式"，"匹配模式");**

* 使用typeof检查正则对象，会返回object
* 在构造函数中，可以传递一个匹配模式作为第二个参数。可以是：
  * i：忽略大小写
  * g：全局匹配模式

```javascript
//创建正则表达式的对象
//这个正则表达式可以用来检查一个字符串中是否含有a
//严格区别大小写
var reg = new RegExp("a");

//忽略大小写
var reg = new RegExp("a","i");

var str = "a";
```

##### (2)使用字面量来创建正则表达式

语法：

var 变量 = /正则表达式/匹配模式

```javascript
var reg = /a/i;
```

* 使用构造函数更加灵活

```javascript
//创建一个正则表达式，检查一个字符串中是否有a或b
//使用|表示或者
var reg = /a|b/;
```

```javascript
//创建一个正则表达式，检查一个字符串中是否有字母
//[]里的内容也是或的关系
//[a-z]表示任意小写字母
//[A-z]表示任意字母
//[0-9]表示任意数字
var reg = /[A-z]/;
var reg = /[0-9]/;
```

```javascript
//检查一个字符串中是否含有abc或adc或aec
var reg = /a[bde]c/
```

```javascript
//[^ab]检查除了a和b其他的字符
var reg = /[^ab]/
```

##### (3)正则表达式的方法test()

使用这个方法可以用来检查一个字符串是否符合正则表达式的规则

```javascript
//检查字符串str是否符合test的规则
//result中存放结果
var result = reg.test(str); //ture
```

#### 2.字符串和正则相关的方法

##### (1)split()

- 可以传递一个正则表达式作为参数，这样方法将会根据正则表达式去拆分字符串
- 即使不指定全局匹配，也会全部拆分

```javascript
var str = "1a2b3c4d5e6f7";
var result = str.split(/[A-z]/);  //1,2,3,4,5,6,7
```

##### (2)search()

可以搜索字符串中是否含有指定内容。如果搜索到指定内容，则会返回第一次出现的索引，如果没有搜索到，就返回-1

- 该方法只会查找第一个出现的位置，即使设置全局匹配也没有用

```javascript
str = "hello abc hello abc"
result = str.search("abc") //6

// 搜索字符串中是否含有abc或aec或afc
result = str.search(/a[bef]c/);
```

##### (3)match

可以根据正则表达式，将一个字符串中符合条件的内容提取出来。

* 默认情况下，match只会找到第一个符合要求的内容，找到之后就停止检索
* 我们可以设置正则表达式为全局匹配模式，这样就会匹配到所有的内容
* 可以为一个正则表达式设置多个匹配模式，并且顺序无所谓
* match()会将匹配到的内容封装到数组中返回，即使只查询到一个结果

```javascript
str = "1a2b3c4d5A6fB";
result = str.match(/[A-z]/); //a（找到第一个）
//既全局又忽略大小写
result = str.match(/[a-z]/gi); //a,b,c,d,A,B
```

##### (4)replace()

可以将字符串中指定的内容替换为新的内容

- 第一个参数是被替换的内容，可以接受一个正则表达式作为参数
- 第二个参数是新的内容
- 不会影响到原字符串
- 默认情况下只替换第一个

```javascript
result = str.replace("a","@-@");
result = str.replace(/[a-z]/ig,"");//删除所有字母
```

#### 3.语法

通过两次可以设置一个内容出现的次数

* {n}正好出现n次
* {m,n}出现m~n次
* {m,}出现m次以上
* +表示至少一个，相当于{1,}
* *表示0个或多个，相当于{0,}
* ?表示0个或1个，相当于{0,1}
* 量词只对前面的一个内容起作用

```javascript
//创建一个正则表达式检查一个字符串中是否含有aaa
var reg = /a{3}/;

//检查是否有ababab
reg = /(ab){3}/;

//b出现的次数为1-3次
reg = /ab{1,3}c/;

//b出现的次数为3次以上
reg = /ab{3,}c/;

reg = /ab+c/;

reg = /ab*c/;

reg = /ab?c/;

//检查一个字符串是否以a开头
reg = /^a/;  //区别[^a]表示除去a

//检查字符串是否以a结尾
reg = /a$/;

//检查是否以a开头以a结尾
reg = /^a$/;

//检查是否以a开头或者以a结尾
reg = /^a|$/;
```

```javascript
//创建一个正则表达式，用来检查一个字符串是否是一个合法手机号
//手机号规则：
//（1）11位
//（2）以1开头
//（3）第二位不能是3-9
//（4）三位之后任意数字9个

 var reg = /^1[^3-9][0-9]{9}$/
```

- "."表示任意字符，如果想表示符号本身的含义，需要使用转义字符
  - 在正则表达式中使用\作为转义字符，用\.来表示
  - `\\`表示一个\
  - 注意：使用构造函数时，由于它的参数是一个字符串，而\是字符串中的转义字符，因此要加两个转义字符 `\\`

```javascript
//创建一个正则表达式，检查一个字符串是否有.
// 方式一：字面量的方式
var reg = /\./;
// 方式二：构造函数的方式
reg = new RegRxp("\\.");
```

- \w——表示任意字母、数字、下划线_
- \W——除了字母、数字、下划线_
- \d——表示任意的数字
- \D——除去数字
- \s——空格
- \S——除去空格
- \b——单词边界

```javascript
//创建一个正则表达式，检查一个字符串中是否有child
reg = /\bchild\b/;
reg.test("children"); //false
```

- \B——除了单词边界

```javascript
//去掉字符串前后的空格
str = str.replace(/^\s*|$/g,"")
```

#### 4.邮件的正则表达式

```javascript
//电子邮件格式
//任意字母数字下划线.任意字母数字下划线 +@+任意字母数字+.+任意字母（2-5位）+.+任意字母（2-5位）

reg = /^\w{3,}(\.\w+)* @ [A-z0-9]+(\.[A-Z]{2,5}){1,2}$/
```

### 十二、DOM

#### 1. 定义

DOM=Document Object Model 文档对象模式

- Document 文档：文档表示的是整个HTML网页
- Object 对象：将网页中的每个部分都转化为了一个对象，可以通过面向对象的形式操作网页
- Model 模型：使用模型来表示对象之间的关系，目的是为了便于获取对象，可以体现节点和节点之间的关系，比如HTML DOM树
  - html
    - head
      - title
        - 文本节点
    - body
      - a标签
        - 文本节点

作用：可以通过JS来对HTML网页进行操作

#### 2.节点

##### 定义

node是构成网页最基本的组成部分，网页中的每一个部分都可以称为是一个节点（节点的本质是一个对象）

##### 分类

- 文档节点：整个HTML文档
- 元素节点：HTML文档中的HTML标签，p标签，a标签等
- 属性节点：元素的属性，比如p标签中的id属性
- 文本节点：HTML标签中的文本内容，比如标签之间的文本内容

##### 节点的属性


|   | nodeName | nodeType | nodeValue |
| --- | --- | --- | --- |
| 文档节点 | #document（固定值）| 9 | null |
| 元素节点 | 标签名 | 1 | null |
| 属性节点 | 属性名 | 2 | 属性值 |
| 文本节点 | #text | 3 | 文本内容 |

###### (1)文档节点

浏览器已经为我们提供了文档节点对象document，这个对象是window属性，可以在页面中直接使用，文档节点代表的是整个网页

```html
<body>
		<button id="btn">我是一个按钮</button>
		<script type="text/javascript">
			// 通过document获取button对象
			// 通过document对象的getElementById()方法实现
			// 此时的btn即为按钮对象
			var btn = document.getElementById("btn");
			// 通过获取到的button对象修改按钮中的文字
			// 通过属性修改修改值
			btn.innerHTML="i am button"
		</script>
	</body>
```

###### (2)元素节点

**通过document对象的方法获取元素节点**

- getElementById()：通过元素的id属性获取一个元素节点对象
- getElementByTagName()：通过标签名获取一组元素节点对象
  - 该方法会返回一个类数组对象，所有查询到的元素都会封装到对象中
  - 即使查询到的内容只有一个，也会封装到数组中饭返回

- getElementByName()：通过name属性获取一组元素节点对象
  - 该方法会返回一个类数组对象，所有查询到的元素都会封装到对象中

**通过innerHTML属性获取元素内部的HTML代码**

- 对于一个自结束标签，比如input，这个标签并没有内部的HTML代码，因此使用该方法没有意义

如果要读取元素节点的属性，则直接使用元素.属性名，比如：元素.id 元素.name。但是注意：class属性不能采取这样的方式，读取class属性的时候，语法：元素.className

```javascript
window.onload = function(){
            // 为id为btn01的按钮绑定一个单击响应函数
            var btn01 = document.getElementById("btn01");
            btn01.onclick = function(){
                //查找#bj节点（根据id属性查找节点）
                var bj=document.getElementById("bj");
                // 打印北京
                // 通过innerHTML这个属性可以可获取得到元素内部的HTML代码
                // 对于当前的元素来说，内部的HTML代码是“北京”二字
                alert(bj.innerHTML);
            };
            
            // 为id为btn02的按钮绑定一个单击响应函数
            var btn02 = document.getElementById("btn02");
            btn02.onclick = function(){
                //查找所有li节点（根据标签名查找节点的方法getElementsByTagName()）
                var lis = document.getElementsByTagName("li");
                // 打印获取到的类数组的长度
                //alert(lis.length);
                // 遍历数组
                for(var i = 0; i<lis.length;i++){
                    alert(lis[i].innerHTML);
                }
            }
            
            // 为id为btn03的按钮绑定一个单击响应函数
            var btn03 = document.getElementById("btn03");
            btn03.onclick = function(){
                //查找name=gender节点
                var inputs = document.getElementsByName("gender");
                alert(inputs.length);
                // 遍历数组
                for(var i = 0; i<inputs.length;i++){
                alert(inputs[i].value);
                alert(inputs[i].className);
                }
            }
}
```

**获取元素节点的子节点**

- 通过具体的元素节点调用
  - getElementsByTagName()：方法，返回当前节点的指定标签的后代节点
    - 注意区别document的方法，这里的方法是通过元素对象调用的（作用范围不同）
  - childNodes：属性，表示当前节点的所有子节点（包括空白）
    - 该方法会获得包括文本节点在内的所有子节点
    - DOM标签间的空白也会被当成文本节点，注意，在IE8以及以下的浏览器中，不会讲空白文本当成自及诶点，所以该属性在IE8中的长度会返回实际子元素的个数（不包括空白）
  - children：属性，表示当前节点的所有子元素（不包括空白文本）
  - firstChild：属性，表示当前节点的第一个子节点（包括空白文本）
    - firstElementChild：属性，表示当前及诶单的第一个子元素（不包括空白文本），但是该属性的兼容性并不好，不支持IE8以下的浏览器
  - lastChild：属性，表示当前节点的最后一个子节点

```javascript
// 为id为btn04的按钮绑定一个单击响应函数
var btn04 = document.getElementById("btn04");
btn04.onclick = function(){
    //查找#city下所有li节点
    // 第一步：获取id为city的元素
    var city = document.getElementById("city");
    // 第二步：获取city下的所有li节点
    var lis = city.getElementsByTagName("li");
    // 遍历获取得到的li数组
    for(var i = 0;i<lis.length;i++){
        alert(lis[i].innerHTML);
    }
}
    
// 为id为btn05的按钮绑定一个单击响应函数
var btn05 = document.getElementById("city");
btn05.onclick = function(){
    //返回#city的所有子节点
    //第一步：获取ID为city的节点
    var city = document.getElementById("city");
    // 第二步：获取所有子节点（包括换行产生的空白文本）
    var cns = city.childNodes;
    // 获取所有子元素
    var cns2 = city.children;
}
        
// 为id为btn05的按钮绑定一个单击响应函数	
var btn06 = document.getElementById("btn06");
btn06.onclick = function(){
    //返回#phone的第一个子节点
    // 第一步：获取ID为phone的节点
    var phone = document.getElementById("phone");
    // 第二步：获取子节点（会包括空白文本）
    var fir = phone.firstChild;
    // 获取第一个子元素（不会包括空白文本）
    var fir = phone.firstElementChild;
}
```

**获取元素节点的父节点和兄弟节点**

* 通过具体的元素节点调用
  * parentNode：属性，表示当前节点的父节点
  * previousSibling：属性，表示当前节点的前一个兄弟节点（包括空白文本）
    * previousElementSibiling：获取前一个兄弟原本苏（不包括空白文本）
  * nextSibling：属性，表示当前节点的后一个兄弟节点

innerText：该属性可以获取到元素内部文本内容的所有

* 与innerHTML类似，不同的是他会自动将HTML标签去除

```javascript
/// 定义一个函数，专门用于为指定的元素绑定单击响应函数
// 参数 ： 
// idStr：要绑定单击响应函数的id属性值
// fun 事件的回调函数，当单击元素时，该函数将会被触发
function myClick(idStr,fun){
        var btn = document.getElementById("idStr");
        btn.onclick = fun;
    };
    
// 为id为btn07的按钮绑定一个单击响应函数
myClick("btn07",function(){
        //返回#bj的父节点
        // 第一步：获取ID为bj的节点
        var bj = document.getElementById("bj");
        // 第二步：获取其父节点
        var pn = bj.parentNode;
        alert(pn.innerText);
    });

// 为id为btn08的按钮绑定一个单击响应函数
myClick("btn08",function(){
//返回#android的前一个兄弟节点
// 第一步：获取ID为Android的元素
var and = document.getElementById("android");
// 第二步：获取前一个兄弟节点
var ps = and.previousSibling;
// 获取前一个兄弟元素（不包括空白）
var ps1 = and.previousElementSibling;
alert(ps1);
});
			
// 为id为btn09的按钮绑定一个单击响应函数
myClick("btn09",function(){
//设置#username的value属性值
// 第一步：获取ID为username的value属性值
var um = document.getElementById("username");
// 读取um的value属性值
// value属性值就是文本框中填写的内容
        alert(um.value);
});

// 为id为btn10的按钮绑定一个单击响应函数
myClick("btn10",function(){
// 设置#username的value属性值
// 第一步：获取ID为username的value属性值
var um = document.getElementById("username");
// 读取um的value属性值并进行修改
// value属性值就是文本框中填写的内容
um.value="今天天气真不错";
});
			
// 为id为btn11的按钮绑定一个单击响应函数
myClick("btn11",function(){
// 获取ID为bj的元素
var bj = document.getElementById("bj");
// 打印文本内容
alter(bj.innerHTML);
alter(bj.innerText);
// 获取ID为bj的文本节点的内容
// 文本节点的属性值是文本内容
var fc = bj.firstChild;
alter(fc.nodeValue);
// 另一种方法：
alter(fc.firstChild.nodeValue);
});
```

* document中有一个属性body，它保存的是body的引用
`var body = document.body; //获取body标签`
* document中有一个属性documentElement，它保存的是html根标签
`var html = document.documentElement; //获取HTML标签`
* document中有一个属性all，它代表的是页面中的所有元素
`var all = document.all; //获取页面中的所有元素`
`var all = document.getElementByTagName("*");`
* getElementsByClassName()：根据class属性值查询一组节点对象，但是该方法不支持IE8及以下的浏览器
`var box = document.getElementsByClassName("box");`
* querySelector()：需要一个选择器字符串作为参数，可以根据一个CSS选择器来查询一个元素节点对象（可以用该方法找到某一个class下的元素），使用该方法只会返回唯一的元素，如果满足条件的元素有多个，只会返回第一个
`var box = document.querySelector(".box1");`
* querySelectorAll()：该方法和querySelector()类似，不同的是它会将符合条件的元素封装到一个数组中返回（即使符合条件的元素只有一个，也会返回数组）
`var box = document.querySelectorAll(".box1");`

#### 3.事件

##### 定义

文档或者浏览器窗口中发生的一些特定的交互瞬间，比如：点击按钮，鼠标移动，关闭窗口

##### 处理方式

可以在事件的对应属性中设置一些js代码，这样当事件被触发时，这些代码将会被执行（这种结构被认为是结构和行为的耦合，不推荐使用）

`<button id="btn" onclick="alert('你点我干嘛')">我是一个按钮</button>`

* onclick 单击的时候触发
* ondbclick 双击的时候触发

可以为按钮的对应事件绑定处理函数的形式来响应事件，当事件被触发时，其对应的函数将会被调用。为单击事件绑定的函数，被称为是**单击响应函数**。

```javascript
// 获取按钮对象
var btn = document.getElementById("btn");
// 绑定一个单击事件
btn.onclick = function(){
		alert("你点我干嘛");
}
```

#### 4.文档的加载

浏览器在加载一个页面时，是按照自上向下的顺序加载的，读取到一行，就运行一行。如果js写在body的上面，那么在代码运行的时候，页面还没有加载，DOM对象也没有加载，会导致无法获取到DOM对象。将JS代码编写到页面的下部（body内部），就是为了可以在页面加载完毕后再执行JS代码。

onload事件会在整个页面加载完成之后才触发。为window绑定一个onload事件，确保给事件的函数在整个页面加载完毕后（出现对应的对象后）才会执行，这样可以确保代码在执行的时候，所有的DOM对象都已经加载完毕了，因此可以正常获取到某个对象。

```HTML
<head>
    <meta charset="utf-8">
    <title></title>
    <script>
        window.onload{
            // 获取按钮对象
            var btn = document.getElementById("btn");
            // 绑定一个单击事件
            btn.onclick = function(){
                alert("你点我干嘛");
            }
        }
    </script>
</head>
```

从性能上讲，写在页面中更好。



#### 全选、反选、全不选练习

* 在事件的相应函数中，响应函数是给谁绑定的，this就是谁（以方法的形式调用）
* 如果4个多选框全部选中，则checkedAllBox也应该选中；如果4个多选框都没有选中，则checkedAllBox也不选中
  * 每一次点击的时候都要进行判断

```HTML
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<script>
			window.onload = function(){
				
				// 获取四个多选框items(由于按钮均涉及到对多选框的设置，因此可以将其设置为全局对象)
				var items= document.getElementsByName("items");
				// 全选/全不选多选框：当其选中时，其余也选中；当其取消时，其余也取消
				var checkedAllBox = document.getElementById("checkedAllBox");
				
				
				// 全选：点击按钮之后，四个多选框全部被选中
				// 为id为checked	AllBtn的按钮绑定一个单击响应函数
				var checkAllBtn = document.getElementById("checkAllBtn");
				checkAllBtn.onclick = function(){
					// 设置四个多选框变成选中状态
					// 遍历数组items
					for(var i=0;i<items.length;i++){
						// 设置四个多选框变成选中状态
						// checked：设置或设置checkbox是否应该被选中，true为选中，flase不选中
						items[i].checked = true;
					}	
					// 将全选/全不选设置为选中
					checkedAllBox.checked = true;
				};
					
				// 全不选按钮：点击按钮之后，多选框都变成没选中的状态
				// 为ID为checkNoBtn的按钮绑定一个单击响应函数
				var checkNoBtn = document.getElementById("checkNoBtn");
				checkNoBtn.onclick = function(){
					// 设置四个多选框变成未选中状态
					// 遍历
					for (var i=0;i<items.length;i++){
						// 设置四个多选框变成未选中状态
						items[i].checked = false;
					}
					// 将全选/全不选设置为不选中
					checkedAllBox.checked = false;
				};
				// 反选按钮：点击按钮后，多选框都变成与现在相反的状态
				var checkRevBtn = document.getElementById("checkRevBtn");
				checkRevBtn.onclick = function(){
					// 在反选的时候也需要判断4个多选框是否全部选中
					checkedAllBox.checked = true;
					// 遍历
					for (var i=0;i<items.length;i++){
						// 设置四个多选框取反
						items[i].checked = !(items[i].checked);
						// 判断是否全选
						// 只要有一个没有选中（为false），则不是全选
						if(!items[i].checked){
							// 一旦“不是全选”成立，执行下列语句
							// 将checkedAllBox设置为false
							checkedAllBox.checked = false;
						}
					}
				};
				// 提交按钮：点击按钮之后，将所有选中的多选框value属性值弹出
				var sendBtn = document.getElementById("sendBtn");
				sendBtn.onclick = function(){
					// 遍历
					for (var i=0;i<items.length;i++){
						// 判断多选框是否选中
						if(items[i].checked){
							alert(items[i].value);
						}
					}
				};
				
				checkedAllBox.onclick = function(){
					for (var i=0;i<items.length;i++){
						// 多选项的状态跟选项相同
						// 此处以方法的形式调用，this为checkedAllBox(事件源)
						items[i].checked = this.checked;
						};
				};
				// 优化处理
				// 如果4个多选框全部选中，则checkedAllBox也应该选中
				// 如果4个多选框没有都选中，则checkedAllBox也不选中
				
				// 为4个多选框分别绑定单击响应函数
				for(var i=0;i<items.length;i++){
					items[i].onclik = function(){
						// 设置checkedAllBox在判断之前的状态设置为选中状态
						checkedAllBox.checked = true;
						for(var j=0;j<items.length;j++){
							// 判断是否全选
							// 只要有一个没有选中（为false），则不是全选
							if(!items[j].checked){
								// 一旦“不是全选”成立，执行下列语句
								// 将checkedAllBox设置为false
								checkedAllBox.checked = false;
								// 一旦判断完成，则已经得到结果，不需要继续进行判断（提升性能）
								break;
							}
						}				
					}
				}
			};
		</script>
	</head>
	<body>
		<form method="post" action="">
			你爱好的运动是？<input type="checkbox" id="checkedAllBox" />全选/全不选
			<br />
			<input type="checkbox" name="items" value="足球" />足球
			<input type="checkbox" name="items" value="篮球" />篮球
			<input type="checkbox" name="items" value="羽毛球" />羽毛球
			<input type="checkbox" name="items" value="乒乓球" />乒乓球
			<br />
			<input type="button" id="checkAllBtn" value="全 选" />
			<input type="button" id="checkNoBtn" value="全不选" />
			<input type="button" id="checkRevBtn" value="反 选" />
			<input type="button" id="sendBtn" value="提 交" />
		</form>
	</body>
</html>
```

#### 5.DOM对象的增删改方法

appendChild()：把新的子节点添加到指定节点

* 用法：父节点.appendChild(子节点)
* 注意，这里的节点是已经生成的节点对象，因此在传递参数的时候用到的是对象名而不是字符串

removeChild()：删除子节点

* 该方法是父节点的方法

replaceChild()：替换子节点

* 该方法是父节点的方法
* 第一个参数是新节点，第二个参数是被替换的节点
* `bj.parentNode.removeChild(bj); // 常用方法是结合子元素的parentNode属性`

insertBefore()：在指定的子节点前面插入新的子节点

* 该方法是父节点的方法
* 第一个参数是需要插入的子节点，第二个节点是插入后在后面的节点

createElement()：创建元素节点

* 可以用于创建一个元素节点对象，它需要一个标签名作为参数，将会根据该标签名创建元素节点对象，并将创建好的对象作为返回值返回

createTextNode()：创建文本节点

* 可以用来创建一个文本节点对象，将会根据该内容创建文本及诶单，并将新的文本节点返回

**使用innerHTML也可以完成DOM的增删操作，但是使用该方法的时候相当于将所有的标签重置，一般会两种方式结合使用**

```HTML
<script type="text/javascript">
        function myClick(idStr,fun){
            var btn = document.getElementById(idStr);
            btn.onclick = fun;
        };
        window.onload = function(){
        
            //创建一个“广州”节点，添加到#city下
            myClick("btn01",function(){
                // 创建广州节点<li>广州</li>
                // 创建li元素节点
                var li = document.createElement("li");
                // 创建广州文本节点
                var gzText = document.createTextNode("广州");
                // 将文本节点设置为li的子节点
                li.appendChild(gzText)
                // 获取ID为city的节点
                var ci = document.getElementById("city");
                // 将广州节点添加到city下
                city.appendChild(li);
            });
            
            myClick("btn02",function(){
                //将“广州”节点插入到#bj前面
                // 创建一个广州节点
                var li = document.createElement("li");
                var gzText = document.createTextNode("广州");
                li.appendChild(gzText);
                // 获取id为bj的节点
                var bj = document.getElementById("bj");
                // 插入前要获取父元素
                var city = document.getElementById("city");
                city.insertBefore(li,bj);
            })
            
            myClick("btn03",function(){
                //使用“广州”节点替换#bj节点
                // 创建一个广州节点
                var li = document.createElement("li");
                var gzText = document.createTextNode("广州");
                li.appendChild(gzText);
                // 获取id为bj的节点
                var bj = document.getElementById("bj");
                // 替换前要获取父元素
                var city = document.getElementById("city");
                city.replaceChild(li,bj);
            })
            
            myClick("btn04",function(){
                //删除#bj节点
                // 获取id为bj的节点
                var bj = document.getElementById("bj");
                var city = document.getElementById("city");
                city.removeChild(bj);
                // 常用方法是结合子元素的parentNode属性
                bj.parentNode.removeChild(bj);

            })
            
            myClick("btn05",function(){
                //读取#bj内的html代码
                var bj = document.getElementById("bj");
                alert(bj.innerHTML);
            }
            )
            
            myClick("btn06",function(){
                //设置#bj内的html代码
                var bj = document.getElementById("bj");
                bj.innerHTML="昌平";
            })
            
            // 通过直接修改#city内部的HTML代码的方式添加元素
            myClick("btn07",function(){
                //向city中添加广州元素
                var ci = document.getElementById("city");
                // 通过innerHTML的属性
                // ci.innerHTML +="<li>广州</li>";
					
                // 两种方式结合使用
                var li=document.createElement("li");
                li.innerHTML = "广州";
                ci.appendChild(li);
            })
        };		
    </script>
```

**添加和删除练习**

注意：

* 点击超链接后，超链接会自动跳转页面，这个是超链接的默认行为，但是本练习中不希望出现默认行为，需要取消，可以在响应函数的最后return false来取消默认行为
* 删除之前的确认对话框用ocnfirm()来实现，它是一个显示带有一段提示文字以及确认按钮和取消按钮的对话框。如果用户点击的是确定，函数返回值是true，如果点击取消，则返回false。可以根据返回值判断后面的行为
* 如果在添加元素的之后直接将生成的tr标签加入到table中，是加在tbody的外面，与现有的元素不构成兄弟关系，因此要进行调整
* 新添加的行delete中的onclick需要在生成新元素之后重新进行绑定，才能实现理想的效果
* 注意页面的执行流程。给a标签绑定响应函数的过程中：for循环会在页面加载完成之后立即执行，而响应函数是在超链接被点击的时候才执行。for循环是用于在页面加载的时候给每个a标签绑定单击响应函数的时候用的，因此在超链接被真正点击的时候，循环变量i已经到了终止，因此在点击响应函数内部，被绑定的元素不能被allA[i]代替

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<script type="text/javascript">
			// tr的响应函数：在点击之后，将当前超链接所在行删除
			function delA(){
				// 这里点击哪个超链接，this所代表的对象就是谁
				// 获取当前tr 
				var tr = this.parentNode.parentNode;
				// 获取要删除的员工的名字
				// var name = tr.getElementsByTagName("td")[0].innerHTML;//第一种写法
				var name = tr.children[0].innerHTML;
				// 删除之前弹出提示框
				var flag = confirm("确认删除"+name+"吗？");
				// 如果用户点击确认
				if(flag){
					tr.parentNode.removeChild(tr);
				}
				// 取消默认行为
				return false;
			};
			
			window.onload = function(){
				// 删除功能：点击超链接之后，删除员工信息
				// 获取所有的超链接
				var allA = document.getElementsByTagName("a");
				// 为每一个超链接都绑定单击响应函数
				for (var i=0;i<allA.length;i++){
					allA[i].onclick = delA;
					};
				// 添加员工的功能：点击按钮之后，将输入的员工的信息添加到上面的表格中
				// 为提交按钮绑定单击函数
				var addEmpButton = document.getElementById("addEmpButton");
				addEmpButton.onclick = function(){
					// 获取用户填写的表格信息
					var name = document.getElementById("empName").value;
					var email = document.getElementById("email").value;
					var salary = document.getElementById("salary").value;
					
					// 需要将获取到的信息保存在tr中
					
					// 创建tr 
					var tr = document.createElement("tr");
					
					/*------方法一：常规方法通过函数添加------
					// 创建四个td 
					var nameTd = document.createElement("td");
					var emailTd = document.createElement("td");
					var salaryTd = document.createElement("td");
					var aTd = document.createElement("td");
					// 创建一个a元素
					var a = document.createElement("a");
					// 创建文本节点
					var nameText = document.createTextNode(name);
					var emailText = document.createTextNode(email);
					var salaryText = document.createTextNode(salary);
					var aText = document.createTextNode("Delete");
					
					// 将文本添加到td中
					nameTd.appendChild(nameText);
					emailTd.appendChild(emailText);
					salaryTd.appendChild(salaryText);
					a.appendChild(aText);// 将文本添加到a中
					aTd.appendChild(a);
					
					// 将td添加到tr中
					tr.appendChild(nameTd);
					tr.appendChild(emailTd);
					tr.appendChild(salaryTd);
					tr.appendChild(aTd);
					
					// 向a中添加href属性
					a.href = "javascript:;";
					------方法一：常规方法通过函数添加------*/
					
					//-------方法二：通过HTML添加-------
					// 设置tr中的内容
					tr.innerHTML="<td>"+name+"</td>"+
					             "<td>"+email+"</td>"+
								 "<td>"+salary+"</td>"+
								 "<td><a href='deleteEmp?id=003'>Delete</a></td>";
					// 获取a元素
					var a = tr.getElementsByTagName("a")[0];
					//-------方法二：通过HTML添加-------
					
					// 为新添加的a再绑定一次单击响应函数
					a.onclick = delA;	
						
					// 将td添加到table的tbody中
					var employTable = document.getElementById("employTable");
					// 获取tbody 
					var tbody = employTable.getElementsByTagName("tbody")[0];
					tbody.appendChild(tr);					
				};				
				};
		</script>
	</head>
	<body>
		<table id="employTable">
			<tr>
				<th>Name</th>
				<th>Email</th>
				<th>Salary</th>
				<th> </th>
			</tr>
			<tr>
				<td>tom</td>
				<td>tom@tom.com</td>
				<td>5000</td>
				<td><a href="javascript:;">Delete</a></td>
			</tr>
			<tr>
				<td>Jerry</td>
				<td>jerry@sohu.com</td>
				<td>8000</td>
				<td><a href="deleteEmp?id=002">Delete</a></td>
			</tr>
			<tr>
				<td>BOB</td>
				<td>BOB@tom.com</td>
				<td>10000</td>
				<td><a href="deleteEmp?id=003">Delete</a></td>
			</tr>
		</table>
		<div id="formDiv">
			<h4>添加新员工</h4>
			<table>
				<tr>
					<td class="word">name:</td>
					<td class="inp">
						<input type="text" name="empName" id="empName"/>
					</td>
				</tr>
				<tr>
					<td class="word">email:</td>
					<td class="inp">
						<input type="text" name="email" id="email"/>
					</td>
				</tr>
				<tr>
					<td class="word">salary:</td>
					<td class="inp">
						<input type="text" name="salary" id="salary"/>
					</td>
				</tr>
				<tr>
					<td colspan="2" align="center">
						<button id="addEmpButton">
							Submit
						</button>
					</td>
				</tr>		
			</table>
		</div>		
	</body>
</html>
```

#### 6.DOM对象创建CSS样式

###### 修改元素的样式

语法：

**元素.style.样式名 = 样式值**

- 注意这里的样式值必须要是一个字符串(即使是一个像素值也要写成字符串)
- 如果css的样式名中包含减号，这样的名称在js中不合法。需要将这样的样式名修改为驼峰命名法——去掉“-”，然后将“-”后面的字母大写
- 我们通过style属性设置的样式都是内联样式，而内联样式具有较高的优先级。所以我们通过Js做出的修改往往会立即显示
- 当style标签中的样式设置为"!important"优先级的时候，js中修改的样式不会对其生效。此时的样式具有最高的优先级，即使通过js也不能修改其样式

###### 获取元素的样式

语法：

**元素.style.样式名**

* 通过style属性读取的是内联样式，无法读取到样式表中的样式

```html
<script type="text/javascript">
			window.onload = function(){
				// 点击按钮之后，修改box1的大小
				// 获取box1
				var box1  = document.getElementById("box1");
				// 为按钮绑定单击响应函数
				var btn01 = document.getElementById("btn01");
				btn01.onclick = function(){
					// 修改Box1的宽度
					box1.style.width = "300px";
					box1.style.backgroundColor = "yellow";
				};
				
				// 点击按钮之后，获取Box1的样式
				var btn02 = document.getElementById("btn02");
				btn02.onclick = function(){
					// 获取样式
					alert(box1.style.width);
				};
			}
    </script>
```

定义一个方法，用来获取指定元素的当前样式

参数：

- obj 要获取样式的元素
- name 要获取的样式值

```javascript
function getStyle(obj,name){
// 在正常的浏览器中，存在getComputeStyle()方法，但是在ie8中没有，可以利用这一点作为判断浏览器的条件
 // 这里加上window指明了对象，没有找到，将返回false；如果去掉window，则是作为一个变量寻找，找不到时将会报错
// 本质上，这里使用currentStyle方法也可以，区别在于不同的浏览器
// 注意判断是否存在某个函数和调用函数的区别
if(window.getComputedStyle){
    // 正常浏览器的方式
      return getComputeStyle(obj,null)[name];
}else{
    // ie8的方式
      return obj.currentStyle[name];
 }
 //以上等效为三元运算符的方式
 //return window.getComputedStyle?getComputeStyle(obj,null)[name]:obj.currentStyle[name];
};
```

#### 7.样式操作的其他属性

clientWidth, clientHeight：这两个属性可以获取元素的可见可见宽度和高度

* 以上两个属性返回的数字不带px，可以直接参与运算
* 会获取元素的宽和高度，包括内容区和内边距
* 以上两个属性只读，不能对样式修改

offestWidth, offsetHeight：这两个属性可以获取元素全部的高度和宽度

* 包括内容区、内边距和边框

offsetParent：定位父元素，可以用来获取当前元素的定位父元素

* 定位父元素就是包含块，即里当前元素最近的开启了定位的祖先元素，如果所有的祖先元素都没有开启定位，则返回body

offsetLeft：当前元素相对于其定位父元素（包含块）的水平偏移量

offsetTop：当前元素相对于其定位父元素（包含块）的垂直偏移量

scrollLeft：获取水平滚动条滚动的距离

scrollTop：获取垂直滚定条的距离

* 当满足scrollHeight - scrollTop == clientHeight的时候，说明垂直滚动条滚动到底部
* 当满足scrollWeight - scrollLeft == clientWight的时候，说明水平滚动条滚动到底部

##### 条款协议练习

```HTML
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<style type="text/css">
				
			#info{
				width: 300px;
				height: 500px;
				background-color: #bfa;
				overflow: auto;	
			}
		</style>
		<script type="text/javascript">
			window.onload = function(){
				// 当垂直滚动条滚动到底时，是表单项可用
				// onsscroll：该事件会在滚动条滚动时触发
				// 获取ID为info的元素
				var info=document.getElementById("info");
				
				// 获取两个表单项
				var inputs = document.getElementsByTagName("input");
				// 为info绑定一个滚动条滚动的事件
				info.onscroll = function(){
					
					// 检查垂直滚动条是否滚动到底部
					if(info.scrollHeight-info.scrollTop == info.clientHeight){
						// 滚动条滚动到底，使表单项可用
						// disabled属性可以设置元素是否禁用，如果设置为true，则元素禁用，如果设置为false，则元素可用
						inputs[0].disabled = false;
						inputs[1].disabled = false;
					}
				}
			}		
		</script>
	</head>
	<body>
		 <h3>欢迎亲爱的用户注册</h3>
		 <p id="info">
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。
			 亲爱的用户，请你仔细阅读以下协议。		 
		 </p>
		 <!-- 如果为表单项添加disabled，表单项将会变成不可用的状态 -->
		 <input type="checkbox" disabled="disabled"/>我已经仔细阅读
		 <input type="submit" value="注册" disabled="disabled"/>
	</body>
</html>
```

#### 8.事件对象

onmousemove：事件，该事件将会在元素汇总移动的时候被触发

##### (1)事件对象

当事件的相应函数被触发时，浏览器每次都会将事件对象作为实参传递进响应函数。

* 在事件对象中封装了当前事件相关的一切信息，比如，鼠标的坐标、键盘哪个按键被按下、鼠标滚轮的方向等等
  * clientX/clientY：当事件被触发时，鼠标指针相对于视口的水平坐标和垂直坐标
  * pageX/pageY：当事件被触发时，鼠标指针相对于页面的水平坐标和垂直坐标（IE8不支持）
  * 在IE8中，响应函数被触发时，浏览器不会传递事件对象，在IE8及以下的浏览器中，是将事件对象作为window对象的属性保存的

###### 坐标显示练习

```HTML
<script type="text/javascript">
    window.onload = function(event){
        // 当鼠标在areaDiv中移动时，在showMsg中来显示鼠标的坐标
        var areaDiv = document.getElementById("areaDiv");
        var showMsg = document.getElementById("showMsg");

        areaDiv.onmousemove = function(event){
            /*
            // 处理不同的浏览器的兼容性问题方法一：
            // 通过判断是否有event参数传入判断浏览器的种类，从而采取不同的处理方式
            if(!event){
                var x = window.event.clientX;
                var y = window.event.clientY;
            }
            */
           // 处理不同的浏览器的兼容性问题方法二：
            event = event || window.event;
            var x = event.clientX;
            var y = event.clientY;
            showMsg.innerHTML="x="+x+" "+"y="+y;
        }
    }
</script>
```

###### 鼠标跟随练习

* 获取滚动条的距离
  * chrome认为浏览器的滚动条是body的，可以通过body.scrollTop来获取滚动条的距离
  * 火狐等浏览器认为浏览器的滚动条是HTML的
  * 用的时候考虑兼容性

```HTML
<style type="text/css">
    #box1{
        width: 100px;
        height: 100px;
        background-color: red;
        /* 开启绝对定位 */
        position: absolute;
    }
</style>
<script type="text/javascript">
    window.onload = function(){
        // 使得div可以跟随鼠标移动
        var box1 = document.getElementById("box1");
        document.onmousemove = function(event){
            // 解决事件对象的兼容问题
            event = event || window.event;
            // 获取鼠标的坐标

            // clientX(Y)用于获取鼠标在可见窗口的坐标，总是相对于可见窗口（视口）
            //  div的偏移量是相对于整个页面（body）而言的，因此在出现滚动的时候会出现差值
            //  该差值是滚动条滚动的距离
            //  pageX(Y)获取到的坐标是相对于页面而言的。但是该属性在IE8中无法使用
            //var left = event.pageX;
            //var top = event.pageY;

            // 获取滚动条的距离并解决scrollTop的兼容性问题
            var st = document.scrollTop || document.documentElement.scrollTop;
            var sl = document.scrollLeft || document.documentElement.scrollLeft;

            var left = event.pageX;
            var top = event.pageY;

            // 设置div的偏移量
            box1.style.left = left + sl + "px";
            box1.style.top = top + st + "px";
        }

    }
</script>
```

##### (2)事件的冒泡（bubble）

所谓的冒泡指的是时间的向上传导，当后代元素上的对象被触发时，其祖先的**相同事件**也会被触发

* 比如，对于同时绑定了单击响应函数的父元素和子元素而言，虽然点击的是子元素，但是父元素的单击响应函数也会被触发
* 在开发中，大部分的事件冒泡是有用的。如果不希望事件发生冒泡，可以通过事件对象取消冒泡，可以将事件对象的cancelBubble设置为true，即可取消冒泡

```javascript
window.onload = function(){
        // 为s1绑定一个单击响应函数
        var s1 = document.getElementById("s1");
        s1.onclick = function(event){
            event = event || window.event;
            // 取消冒泡
            event.cancelBubble = true;
        };
        // 为box1绑定一个单击响应函数
        var box1 = document.getElementById("box1");
        box1.onclick = function(){
            alter("我是div");
        };
    }
```

##### (3)事件的委派

将事件统一绑定给元素的共同祖先元素，这样当后代元素上的事件被触发时，会一直冒泡给祖先元素，从而通过祖先元素的相应函数来处理事件

* 事件的委派是利用了事件冒泡。通过委派可以减少事件绑定的次数，提高程序的效率
* 如果触发事件的对象是期望的元素，则执行，否则不执行

事件对象的target属性表示触发此事件的元素（事件的目标节点）

###### 事件的委派练习

```HTML
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<script type="text/javascript">
			window.onload = function(){
				// 点击按钮之后添加超链接
				// 只绑定一次事件，即可应用到所有的元素上，即使元素是后添加的
				
				// 可以尝试将其绑定个元素共同的祖先元素
				var btn01 = document.getElementById("btn01");
				var u1 = document.getElementById("u1");
				btn01.onclick = function(){
					// 创建一个li 
					var li = document.createElement("li");
					li.innerHTML="<a href='javascript:;' class=''link'>新建的超链接</a>";
					// 将li添加到ul中
					u1.appendChild(li);		
				};				
				u1.onclick = function(event){
					event = event || window.event;
					// 如果触发事件的对象是我们期望的元素，则执行，否则不执行
					if(event.target.className=="link"){
						alert("我是超链接");
					}								
				};
				
			};
		</script>
	</head>
	<body>
		<button id="btn01">添加超链接</button>
		<ul id="u1" style="background-color: #bfa;">
			<li><a href="javascript:;" class="link">超链接1</a></li>
			<li><a href="javascript:;" class="link">超链接2</a></li>
			<li><a href="javascript:;" class="link">超链接3</a></li>
		</ul>
	</body>
</html>
```

##### (4)事件的绑定

使用“**对象.事件=函数**”的形式绑定响应函数，它只能同时为元素的一个事件绑定响应函数，不能绑定多个如果绑定了多个，后面的会覆盖前面的。

addEventListener()：通过这个方法可以为元素绑定响应函数（除去IE8以下）

* 参数：
  * 事件的字符串，不要带"on"
  * 回调函数，当事件触发时，该函数会调用
  * 是否 在捕获阶段触发事件，需要一个布尔值，一般都传false
* 可以同时为一个元素的相同事件同时绑定多个响应函数，这样当事件被触发时，响应函数将会按照函数的绑定顺序执行
* 函数中的this是绑定事件的对象

```javascript
// 点击按钮之后，弹出一个内容
var btn01 = document.getElementById("btn01");
// 为btn01绑定一个单击响应函数
// btn01.onclick = function(){
// };
btn01.addEventListener("click",function(){
    alert("1");
},false);
btn01.addEventListener("click",function(){
    alert("2");
},false);
btn01.addEventListener("click",function(){
    alert("3");
},false);
btn01.addEventListener("click",function(){
    alert("4");
},false);
```

attrachEvent()：可以使用attrachEvent()来绑定事件（IE8及以下）

* 参数
  * 事件的字符串，要带"on"
  * 回调函数
* 后绑定先执行，执行顺序与addEventListener()相反，对于通过这种方式绑定的函数来说，顺序往往并不关键，因此可以不用对其进行处理
* 函数中的this是window

```javascript
btn01.attrachEvent("onclick",function(){
    alert("1");
});
btn01.attrachEvent("onclick",function(){
    alert("2");
});
btn01.attrachEvent("onclick",function(){
    alert("3");
});
btn01.attrachEvent("onclick",function(){
    alert("4");
});
```

**兼容不同浏览器的事件需要用多事件绑定函数**

- 浏览器方式兼容：通过“传递进来的对象是都具有addEventListener来判断浏览器”的方式
- this指向的转变：this是由调用的方式决定的。如果直接用浏览器调用，this为window，同时调用方式不变动，可以通过匿名函数将调用方式显现出来，即，在匿名函数中调用回调函数，并自行定义回调函数的调用方式
  - 实现方式：浏览器调用bind函数时，调用匿名函数（此时this为window），匿名函数中改变callback的调用方式，通过call调用callback函数，this为callback函数中的参数obj，即被绑定事件的对象

```javascript
window.onload = function(){
        bind(btn01,"click",function(){
            alert("1");
        });
        bind(btn01,"click",function(){
            alert("2");
        });
};

// 定义一个函数，用来为指定元素绑定响应函数
// 参数：
// obj 要绑定事件的对象
// eventStr 事件的字符串(不要on)
// callback回调函数
// 需要统一两个方法this，使得都是绑定事件的对象  
function bind(obj,eventStr,callback){
    // 判断是否有addEventListener方法
        if(obj.addEventListener){
            // 大部分浏览器兼容的方式
            obj.addEventListener(eventStr , callback , false);
    }else
            // 使用call和apply调用时，this是参数所指定的对象
            // ie8及以下
            obj.attachEvent("on"+eventStr , function(){
            callback.call(obj);
        });
    };		
};
```

##### (5)事件的传播

关于事件的传播，网景公司和微软公司有不同的理解。
微软公司：事件应该是由内向外传播的，当事件触发时，应该先触发当前元素上的响应函数，然后再从当前元素向当前元素的祖先元素上传播。即事件应该在冒泡阶段（方向：用内向外）执行。

网景公司：事件应该是由外向内传播的，当事件触发时，应该先触发当前元素的最外层的祖先元素的事件，然后从祖先元素向当前元素传播。即事件先发生冒泡（方向：从内向外），然后从外向内触发，后面的过程被称为事件的捕获阶段。

w3c：综合了两个公司的方案，将事件分成了三个阶段: 

- 第一个阶段为事件的捕获阶段：从最外层的祖先元素向内层进行事件的捕获，但是默认此时不会触发事件。（从window开始）
- 第二个阶段为事件的目标阶段：事件捕获到目标元素，捕获结束。开始在目标元素上触发事件。
- 第三个阶段为事件的冒泡阶段：事件函数从目标元素向它的祖先元素传递，一直触发事件函数。

如果希望在捕获阶段就触发事件，可以将addEventListener()的第三个参数设置为true。一般情况下我们不会希望在捕获阶段触发事件，所以这个参数一般都是false。
在ie8及以下的浏览器中没有捕获阶段。

| 概念 |定义  |
| --- | --- |
| 事件 | 在网页中对元素操作的一系列行为，比如鼠标的点击，鼠标移入。是元素的属性。 |
| 事件处理函数 | 人为在事件发生的时候所绑定的一个函数，用来指明某个事件行为发生的时候会做出何种反映 |
| 事件对象 | 包含与事件行为相关的一些特征或者状态，比如鼠标在点击时候的位置。 |

#### 9.拖拽

拖拽的流程：

1.当鼠标在被拖拽元素上被按下时，开始拖拽——onmousedown

2.当鼠标移动时，元素跟随鼠标一起移动——onmousemove

* 注意：鼠标移动是在鼠标被按下之后同时发生的，因此鼠标移动的函数应该在鼠标被按下的内部被书写

3.当鼠标松开时，被拖拽元素固定在当前的位置——onmouseup

* 为了使得被拖拽的元素不受到其他元素的影响，应该将该事件绑定给onmouseup
* 注意，在事件函数的内部的末尾应该取消该函数

注意：

* 为了使得元素在拖动的时候处于鼠标初始点击元素的位置而不是左上角，需要在元素移动的时候将相对相位做出修改（该设置要设置在鼠标被点下的时候）
  * 水平偏移量=鼠标.clientX-元素.offsetLeft
  * 竖直偏移量=鼠标.clientY-元素.offsetTop
* 当我们去拖拽一个网页中的内容，尤其是文字或者图片，浏览器会默认去搜索引擎中搜索内容。此时会导致拖拽功能的异常。这是浏览器提供的默认行为。如果不希望发生这个行为，则可以通过return false来取消这个默认行为。但是对于IE8来说，没有作用，要解决IE8的问题，可以采用以下思路：
  * 当调用一个元素的setCapture()方法后，这个元素会把下一次所有的鼠标按下相关事件捕获到自身上。releaseCapture()方法可以取消上面的行为（该方法只有IE支持，在火狐中调用的时候不会报错，但是在Chrome调用的时候会报错）
  * 可以利用该方法解决上述问题：鼠标点击的时候进行捕获，鼠标松开的时候结束捕获
* 如果要拖拽的对象是图片，注意要给对象开启绝对定位 <img src="an.jpg" id="img1" style="position: absolute;">

```html
<script type="text/javascript">	
        // 封装一个专门用来设置拖拽的函数
        // 参数：开启拖拽的元素对象
        function drag(obj){
            // 为obj绑定一个鼠标按下的事件函数
            // 当鼠标在被拖拽元素上按下时，开始拖拽
            obj.onmousedown = function(event){

                // 设置obj捕获所有鼠标按下的事件(在执行之前首先要进行判断)
                obj.setCapture && obj.setCapture();

                event = event || window.event;
                // div的偏移量 鼠标.clientX - 元素.offsetLeft
                // div的偏移量 鼠标.clientY - 元素.offsetTop
                var ol = event.clientX - obj.offsetLeft;
                var ot = event.clientY - obj.offsetTop;

                // 为document元素绑定一个onmousemove事件
                // 鼠标移动函数要写在内部
                document.onmousemove = function(event){
                    // 当鼠标移动时，被拖拽元素跟随鼠标移动onmousemove
                    // 根据事件对象获取鼠标的坐标
                    event = event || window.event;
                    var left = event.clientX;
                    var top = event.clientY;
                    // 修改被拖拽元素obj的位置
                    obj.style.left = left+"px";
                    obj.style.top = top+"px";
                };

                // 取消去浏览器搜索的默认行为
                return false;
            };

            // 当鼠标松开的时候，结束拖拽
            document.onmouseup  = function(){
                // 取消document的onmousemove事件
                document.onmousemove = null;
                document.onmouseup = null;	
                // 当鼠标松开的时候取消对事件的捕获
                obj.releaseCapture && obj.releaseCapture();
            };
        };		

        window.onload = function(){
            // 拖拽box1元素
            var box1= document.getElementById("box1");
            drag(box1);
            // 拖拽box2
            var box2= document.getElementById("box2");
            drag(box2);			
        };
</script>
```

#### 10.滚轮的事件

onmousewheel：鼠标滚轮滚动事件，会在滚轮滚动的时候触发，但是火狐并不支持该属性

- 在火狐中需要使用DOMouseScroll来绑定滚动事件，注意：该事件需要通过addEventListener()函数来绑定
- 事件对象中的wheelData可以获取鼠标滚轮的滚动方向
  - 向上滚动为120，向下滚动为-120
  - 该数值不看大小只看正负
  - 这个属性在火狐中不支持，火狐汇总会使用event.detail来获取滚动的方向
- 当滚动发生的时候，往往伴随着浏览器滚动条滚动，如果不希望发生，则可以取消浏览器的默认行为

```HTML
<script type="text/javascript">
    function bind(obj,eventStr,callback){
        // 判断是否有addEventListener方法
            if(obj.addEventListener){
                // 大部分浏览器兼容的方式
                obj.addEventListener(eventStr , callback , false);
        }else
                // 使用call和apply调用时，this是参数所指定的对象
                // ie8及以下
                obj.attachEvent("on"+eventStr , function(){
                callback.call(obj);
            });
        };		
    };
    window.onload = function(){
        var box1 = document.getElementById("box1");
        box1.onmousewheel = function(event){
            event = event || window.event;
            // 判断鼠标滚动事件的方向
            if(event.wheelData > 0 || event.detail < 0){
                // 向上滚动，box1变短
                box1.style.height = box1.clientHeight - 10+"px";
            }else{
                // 向下滚动，box1变长
                box1.style.height = box1.clientHeight + 10+"px";
            }
        };
        // 为火狐绑定滚动事件
        bind(box1,"DOMMouseScroll",box1.onmousewheel);
        // 取消浏览器滚动的默认行为（对于用addEventListener()绑定的响应函数，不能使用该语句，需要使用event.preventDefault();
        // 但是IE8中不支持event.preventDefault()需要先判断
        event.preventDefault && event.preventDefault()
        return false;
    }
</script>
```

#### 11.键盘事件

键盘事件往往绑定给一些可以获得焦点的对象或者是document

onkeydown：某个键盘按键被按下

* 如果一直按着某个按键不松手，则事件会一直触发
* 当onkeydown连续触发时，第一次和第二次之间会有较长的时间间隔，其他会非常快（这种设计时为了防止误操作的发生）
* 事件对象中的属性包含了按键被按下的信息：
  * keyCode属性：按键的编码，通过它可以判断哪个按键被按下
  * altKey属性：用来判断alt是否被按下，如果按下则返回true，否则返回false
  * ctrlKey属性：用来判断control是否被按下，如果按下则返回true，否则返回false
  * shiftKey属性：用来判断shift是否被按下，如果按下则返回true，否则返回false

```javascript
document.onkeydown = function(event){
    event = event || window.event;
    // 判断y（89）和control（17）是否同时被按下
    if(event.keyCode === 89 && event.ctrlKey){
};
```

* 在文本框中输入内容属于onkeydown的默认行为，如果在onkeydown中取消默认行为（return false），则输入的内容不会出现在文本框中

```javascript
var input = document.getElementsByTagName("input")[0];
input.onkeydown = function(event){
    // 功能：在文本框中不能输入数字(48-57)
    event = event || window.event;
    if(event.keyCode >= 48 && event.keyCode <=57){
        return false;
    }
}
```

* onkeyup：某个键盘按键被松开

##### 方块移动练习

```javascript
// 使得div可以根据不同的方向键向不同的方向移动
// 注意定位position：absolute
window.onload = function(){
    document.onkeydown = function(event){
        event = event || window.event;
        // 上：38 下：40 左：37 右：39
        // 定义一个变量用来表示移动的速度
        var speed = 10;
        // 当用户按下ctrl后速度加快
        if(event.ctrlKey){
            speed = 50;
        }
        switch(event.keyCode){
            case 37:
                box1.style.left = box1.offsetLeft - speed + "px";
                break;
            case 39:
                box1.style.left = box1.offsetLeft + speed + "px";
                break;
            case 38:
                box1.style.top = box1.offsetTop + speed + "px";
                break;
            case 40:
                box1.style.top = box1.offsetTop - speed + "px";
                break;
        }
    };
};
```

### 十三、BOM

#### 1.概述

BOM：浏览器对象模型（browser object model）
BOM可以使得我们通过JS来操作浏览器，在bom中为我们提供了一组对象，用来完成我们对浏览器的操作。

BOM对象：

- Window
  - 代表整个浏览器窗口，同时window也是网页中的全局对象
- Navigator
  - 代表当前浏览器的信息，通过该对象可以来识别不同的浏览器
- Location
  - 代表当前浏览器的地址栏信息，通过Location可以获取地址栏信息，或者操作浏览器跳转页面
- History
  - 代表浏览器的历史记录，可以通过该对象来操作浏览器的历史记录。由于隐私的原因，该对象不能获取到具体的历史记录，只能操作浏览器向前或者向后翻页。而且该操作只在当次访问时有效。
- Screen
  - 代表用户屏幕的信息，通过该对象可以获取到用户显示器的相关信息

这些BOM对象在浏览器中都是作为window对象的属性保存的。我们可以通过window对象来使用，可以通过window对象使用，也可以直接使用。

#### 2.Navigator

由于历史原因，大部分属性无法帮助我们识别浏览器。一般只使用userAgent来判断浏览器信息。userAgent是一个字符串，这个字符串包含用来描述浏览器信息的内容，不同的浏览器有不同的userAgent。

- 火狐：包含“Firefox”，可以利用正则表达式做判断
  `if(/firefox/i).test(ua)`
  但是在IE11中已经将IE相关的标识去除，不能根据userAgent做出判断

可以通过浏览器中一些特有的对象，来判断浏览器的信息。比如：ActiveXObject对象（可以作为分支判断的一个条件）
`if("ActiveXObject" in window)`

#### 3.History

该对象可以用来操作浏览器向前或者向后翻页。
属性：
length：返回浏览器历史列表中的URL数量。（当次访问）
方法：
back()：可以用来回退大上一个页面，作用与浏览器的回退按钮一样
forward()：可以跳转到下一个页面，作用与浏览器的前进按钮一样
go()：可以用来跳转到指定页面，需要一个整数作为参数
* 1表示向前跳转一个页面，2表示向前跳转两个页面。相当于forward()
* -1表示向后跳转一个页面，-2表示向后跳转两个页面。相当于back()

#### 4.Location

该对象中封装了浏览器的地址栏的信息。

- 如果直接打印location，则可以获取地址栏的信息（当前页面的完整路径）
- 如果直接将location属性修改为一个完整路径或者一个相对路径，则自动跳转。并且会生成相应的历史记录。
  `location = "src"`

方法：
assign()：用来跳转到其他页面，作用与修改location相同
`location.assign("src")`
reload()：重新加载当前文档，作用与刷新按钮相同
`location.reload()`
`location.reload(true) //强制清空缓存刷新页面`
replace()：可以使用新的页面替换当前页面，调用完毕也会跳转页面（不会生成历史记录，不能使用回退按钮回退）
`location.replace("src")`

#### 5.定时（延时）器简介

window对象的方法：
（1）定时调用
setInerval()：按照指定的周期（以毫秒计）来调用函数或计算表达式。

- 每间隔一段时间执行一次，可以实现定时调用。
- 参数：
  - 回调函数：被调用
  - 每次调用间隔的事件：单位为毫秒
- 返回值：一个number类型的数据。这个数字用来作为定时器的唯一标识。

clearInterval()：可以用来关闭一个定时器，方法中需要一个定时器的标识作为参数，这样将关闭标识对应的定时器

- 可以接受任何参数，如果参数是一个有效的定时器的标识，则停止对应的定时器；如果参数不是一个有效的标识，则什么也不做

```javascript
var num=1;
// 每隔一秒更新一次数据
// 返回值timer用来标识对应的定时器
var timer = setInterval(function(){
    count.innerHTML = num++;

    if(num == 11){
        // 停止计时
        clearInterval(timer);
    }
},1000);
```

##### 用定时器切换图片练习

如果连续点击开始计时的按钮，会同时触发多个定时器，并且在关闭的时候只关闭最新的那一个。导致图片切换速度过快。因此在开启定时器之前，要将上一个定时器关闭。

```javascript
<script type="text/javascript">
window.onload(){
        // 使图片可以自动切换
        // 获取img标签
        var img1 = document.getElementById("img1");
        // 创建一个数组来保存图片的路径
        var imgArr = ["../../img/kiss.jpeg","../../img/lili.jpeg","../../img/lzy.jpeg"];
        // 创建一个变量，用来保存当前图片的索引
        var index = 0;
        // 定义一个变量用来保存定时器的标识
        var timer;
        // 设置按钮开始计时
        var btn01 = document.getElementById("btn01");
        btn01.onclick = function(){
            // 在开启定时器之前，需要将当前元素上的其他定时器关闭
            clearInterval(timer);
            // 开启定时器来自动切换图片
             timer = setInterval(function(){
                // 使得索引自增
                index ++;
                // 判断索引是否超过最大索引
                // if(index >= imgArr.length){
                // 	index = 0;
                // }
                index = index % imgArr.length;
                img1.src=imgArr[index];
            },1000);
        };
        // 设置按钮关闭定时器
        var btn02 = document.getElementById("btn02");
        btn01.onclick = function(){
            // 结束计时
            clearInterval(timer);
        };
    };
</script>
```

**方块移动练习改进**

- 借助定时器可以消除卡顿
- 将方向和速度分开进行控制

```javascript
<script type="text/javascript">
    window.onload = function(){
        // 定义一个变量用来表示移动的速度
        var speed = 10;

        // 创建一个变量表示方向
        // 可以通过修改dir改变移动的方向
        var dir = 0;

        // 开启一个定时器来控制div的移动，定时时间为30秒
        setInterval(function(){
            switch(dir){
                case 37:
                    box1.style.left = box1.offsetLeft - speed + "px";
                    break;
                case 39:
                    box1.style.left = box1.offsetLeft + speed + "px";
                    break;
                case 38:
                    box1.style.top = box1.offsetTop + speed + "px";
                    break;
                case 40:
                    box1.style.top = box1.offsetTop - speed + "px";
                    break;
            }
        },30)

        document.onkeydown = function(event){
            event = event || window.event;
            // 上：38 下：40 左：37 右：39

            // 定义一个变量用来表示移动的速度
            var speed = 10;
            // 当用户按下ctrl后速度加快
            if(event.ctrlKey){
                speed = 50;
            }else{
                speed = 10;
            }
            // 获取移动的方向
            dir = event.keyCode;
        };

        // 当按键松开的时候，div不再移动
        document.onkeyup = function(){
            // 设置方向为0
            dir = 0;
        }
    };
</script>
```

（2）延时调用
setTimeout()：在指定的毫秒数后调用函数或计算表达式。

- 延时调用只执行一次。定时调用执行多次。两者可以互换。
  clearTimeout()：关闭延时调用

```javascript
var timer = setTimeout(function(){
    console.log(num++);
},3000);

clearTimeout(timer);
```

**定时器应用练习**

- 利用自己定义的getstyle()函数；来获取指定元素的当前任意样式
- 用parseInt()函数获得含有px单位的数值的整数部分
- 如果以800作为边界，则需要在到达边界之前作出判断，以防止超过边界
- 在本次计时器开始前首先进行判断，停掉当前的计时器

```HTML
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<style type="text/css">
			* {
				margin: 0;
				padding: 0;
			}

			#box1 {
				width: 100px;
				height: 100px;
				left = 0;
				background-color: red;
				position: absolute;
			}
		</style>
		<script type="text/javascript">
			window.onload = function() {
				// 获取box1
				var box1 = document.getElementById("box1");
				// 获取btn01
				var btn01 = document.getElementById("btn01");
				// 定义一个变量，用来保存定时器的标识
				var timer;
				// 点击按钮之后，使得left值增大
				btn01.onclick = function() {
					// 关闭上一个定时器
					clearInterval(timer);
					// 开启一个定时器用来执行动画效果
					var timer = (function() {
						// 获取box1原来的left值
						var oldValue = parseInt(getStyle(box1,"left"));
						// alert(oldValue);
						// 在旧值的基础上增加
						var newValue = oldValue + 10;
						
						// 判断newValue是否大于800
						if(newValue > 800){
							newValue = 800;
						}
						
						// 将新值设置给box1
						box1.style.left = newValue + "px";
						
						// 当元素移动到800px的时候，使其停止动画
						if(newValue == 800){
							// 达到目标，关闭定时器
							clearInterval(timer);
						}

					}, 30);
				};
				function getStyle(obj, name) {
					if (window.getComputedStyle) {
						// 正常浏览器的方式
						return getComputedStyle(obj, null)[name];
					} else {
						// ie8的方式
						return obj.currentStyle[name];
					}
				};				
			};
			
		</script>
	</head>
	<body>
		<button id="btn01">点击按钮之后box1向右移动</button>
		<br /><br />
		<div id="box1"></div>
	</body>
</html>
```

封装到函数中之后
处理封装函数的方法：

- 速度为正值，具体在定时器中是加还是减取决于方向，这一部分要在定时器之前完成判断

```HTML
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<style type="text/css">
			* {
				margin: 0;
				padding: 0;
			}

			#box1 {
				width: 100px;
				height: 100px;
				left=0;
				background-color: red;
				position: absolute;
			}
		</style>
		<script type="text/javascript">
			window.onload = function() {
				// 获取box1
				var box1 = document.getElementById("box1");
				// 获取btn01
				var btn01 = document.getElementById("btn01");
				// 获取btn02
				var btn02 = document.getElementById("btn02");

				// 点击按钮之后，使得left值增大
				btn01.onclick = function() {
					move(box1, 10);
				};
				// 点击按钮之后，使得left值减小
				btn02.onclick = function() {
					move(box1, 0, -10);
				};
				// 定义一个变量，用来保存定时器的标识
				var timer;

				// 创建一个可以设置动画效果的函数
				// 参数
				// obj：要执行动画的对象
				// speed：移动的速度（正值）
				// target：执行函数的目标位置
				function move(obj, target, speed) {
					// 关闭上一个定时器
					clearInterval(timer);
					
					// 获取obj当前的位置
					var current = parseInt(getStyle(obj, "left"));
					
					// 判断速度的正负值
					// 如果为从0向800，则为正值
					// 如果是从800向0，则为负值
					if(current > target){
						// 此时速度应为负值
						speed = -speed;
					}
					
					// 开启一个定时器用来执行动画效果
					timer = setInterval(function() {

						// 获取obj原来的left值
						var oldValue = parseInt(getStyle(obj, "left"));
						// alert(oldValue);
						// 在旧值的基础上减小
						var newValue = oldValue + speed;

						// 判断newValue与最终位置的关系
						// 当向左移动时，要看新值是否小于target
						// 当向右移动时，要看新值是否大于target
						if ((speed < 0 && newValue < target) || (speed > 0 && newValue > target)) {
							newValue = target;
						}

						// 将新值设置给obj
						obj.style.left = newValue + "px";

						// 当元素移动到0px的时候，使其停止动画
						if (newValue == target) {
							// 达到目标，关闭定时器
							clearInterval(timer);
						}
					}, 30);
				};

				function getStyle(obj, name) {
					// 在正常的浏览器中，存在getComputeStyle()方法，但是在ie8中没有，可以利用这一点作为判断浏览器的条件
					// 这里加上window指明了对象，没有找到，将返回false；如果去掉window，则是作为一个变量寻找，找不到时将会报错
					// 本质上，这里使用currentStyle方法也可以，区别在于不同的浏览器
					if (window.getComputedStyle) {
						// 正常浏览器的方式
						return getComputedStyle(obj, null)[name];
					} else {
						// ie8的方式
						return obj.currentStyle[name];
					}
				};
			};
		</script>
	</head>
	<body>
		<button id="btn01">点击按钮之后box1向右移动</button>
		<button id="btn02">点击按钮之后box1向左移动</button>
		<br /><br />
		<div id="box1"></div>
	</body>
</html>
```

- 目前定时器的标识由全局变量timer保存，所有正在执行的定时器都在变量中保存。

处理方法：向执行动画的元素中添加timer属性，使其保存各自的计时器值。

- move函数中的回调函数可以拓展动画效果。把回调函数作为可选项的处理方法：

```
callback && callback(); // 如果有回调函数，则调用，否则不调用
```

- 将写好的工具函数作为外部文件放在js文件中，然后利用script标签导入
  `<script type="text/javascript" src="tools.js"></script>`

```javascript
// tools.js

// 创建一个可以设置动画效果的函数
// 参数
//  obj：要执行动画的对象
// speed：移动的速度
// target：执行函数的目标位置
// attr：要执行动画的样式，比如left top width height
// callback：传递一个回调函数，该函数会在动画执行完毕后执行
function move(obj, attr, target, speed, callback) {
	// 关闭上一个定时器
	clearInterval(obj.timer);

	// 获取obj当前的位置
	var current = parseInt(getStyle(obj, attr));

	// 判断速度的正负值
	// 如果为从0向800，则为正值
	// 如果是从800向0，则为负值
	if (current > target) {
		// 此时速度应为负值
		speed = -speed;
	}

	// 开启一个定时器用来执行动画效果
	obj.timer = setInterval(function() {
		// 获取obj原来的left值
		var oldValue = parseInt(getStyle(obj, attr));
		// alert(oldValue);
		// 在旧值的基础上减小
		var newValue = oldValue + speed;

		// 判断newValue与最终位置的关系
		// 当向左移动时，要看新值是否小于target
		// 当向右移动时，要看新值是否大于target
		if ((speed < 0 && newValue < target) || (speed > 0 && newValue > target)) {
			newValue = target;
		}

		// 将新值设置给obj
		// 书写方式为style[]的形式
		obj.style[attr] = newValue + "px";

		// 当元素移动到0px的时候，使其停止动画
		if (newValue == target) {
			// 达到目标，关闭定时器
			clearInterval(obj.timer);
			// 如果有回调函数，则调用，否则不调用
			callback && callback();
		}
	}, 30);
};

function getStyle(obj, name) {
	// 在正常的浏览器中，存在getComputeStyle()方法，但是在ie8中没有，可以利用这一点作为判断浏览器的条件
	// 这里加上window指明了对象，没有找到，将返回false；如果去掉window，则是作为一个变量寻找，找不到时将会报错
	// 本质上，这里使用currentStyle方法也可以，区别在于不同的浏览器
	if (window.getComputedStyle) {
		// 正常浏览器的方式
		return getComputedStyle(obj, null)[name];
	} else {
		// ie8的方式
		return obj.currentStyle[name];
	}
};
```

```HTML
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<style type="text/css">
			* {
				margin: 0;
				padding: 0;
			}

			#box1 {
				width: 100px;
				height: 100px;
				left=0;
				background-color: red;
				position: absolute;
			}
			#box2 {
				width: 100px;
				height: 100px;
				left:0;
				background-color: yellow;
				position: absolute;
				top:200px;
			}
		</style>
		<script type="text/javascript" src="tools.js"></script>
		<script type="text/javascript">
			window.onload = function() {
				// 获取box1
				var box1 = document.getElementById("box1");
				// 获取box2
				var box2 = document.getElementById("box2");
				// 获取btn01
				var btn01 = document.getElementById("btn01");
				// 获取btn02
				var btn02 = document.getElementById("btn02");
				// 获取btn03
				var btn03 = document.getElementById("btn03");
				// 获取btn04
				var btn04 = document.getElementById("btn04");
				

				// 点击按钮之后，使得left值增大
				btn01.onclick = function() {
					move(box1,"left",800,10);
				};
				
				// 点击按钮之后，使得left值减小
				btn02.onclick = function() {
					move(box1, "left",0, -10);
				};
				
				// 点击按钮之后，使得left值增大
				btn03.onclick = function() {
					move(box1,"left",800,10);
				};
				// 点击按钮之后
				btn03.onclick = function() {
					// move(box1,"left",800,10);
					
					// move(box1,"top",800,10);
					// 先变宽，后变高
					move(box1,"width",800,10,function(){
						move(box2."height",800,10,)
					});
				};
				
			};
		</script>
	</head>
	<body>
		<button id="btn01">点击按钮之后box1向右移动</button>
		<button id="btn02">点击按钮之后box1向左移动</button>
		<button id="btn03">点击按钮之后box2向左移动</button>
		<button id="btn04">测试</button>
		<br /><br />
		<div id="box1"></div>
		<div id="box2"></div>
	</body>
</html>
```

##### 轮播图练习

- 为了使得容器盒子的宽度跟随盒子内部图片的，需要用到js来获取图片元素的数量。
- 对于已经脱离文档流的元素，居中的方法：
  `left: 50%; /* 相对父元素偏移 */`
  `transform: translateX(-50%); /* 相对元素自身偏移 */`
- 在对选中的选项的背景颜色进行设置时，如果直接:`allA[index].style.backgroundColor = "red";`则会导致直接修改内联样式，导致后续的hover无法生效，由于在css中已经设置了选项框的颜色，因此可以通过：`allA[index].style.backgroundColor = "";`使得所有元素的背景颜色的内联样式都清空，此时css中关于背景颜色的设置就能生效（因为最高级别的内联样式被清空了），这句话相当于取消了默认下对于第一个选项框背景颜色的设置

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>李泽言的轮播图❤</title>
		<script type="text/javascript" src="tools.js">
			
		</script>
		<style type="text/css">
			*{
				margin: 0;
				padding: 0;
			}
			#outer{
				width: 520px;
				height: 320px;
				/* 居中 */
				margin: 50px auto;
				background-color: yellowgreen;
				/* overflow: hidden; */
				padding: 10px 0;
				position: relative;
				/* 裁剪溢出的内容 */
				overflow: hidden;
			}
			/* 设置imgList */
			#imgList{
				/* 去除列表符号 */
				list-style: none;
				/* 开启绝对定位 */
				position: absolute;	
			}
			#imgList li{
				/* 设置浮动 */
				float: left;
				/* 设置左右外边距 */
				margin: 0 10px;
				/* 开启相对定位 */
				position: relative;
			}
			/* 设置导航按钮 */
			#navDiv{
				/* 开启绝对定位 */
				position: absolute;
				/* 设置位置 */
				bottom: 15px;
				/* 设置水平居中 */
				/* 相对父元素偏移 */
				left: 50%;
				/* 相对元素自身偏移 */
				transform: translateX(-50%);
			}
			#navDiv a{
				/* 在设置浮动的时候，一方面可以将行元素转化为块元素，另一方面可以使得元素脱离文档流 */
				float: left;
				/* 设置超链接宽高 */
				width: 20px;
				height: 20px;
				background-color: red;
				/* 设置左右外边距 */
				margin: 0 5px;
				/* 设置透明效果 */
				opacity: 0.5;
				/* 兼容IE8 的透明 */
				filter: alpha(opacity=50);
			}
			/* 设置鼠标移入的效果 */
			#navDiv a:hover{
				background-color: black;
			}
		</style>
		<script type="text/javascript">
			window.onload = function(){
				// -----设置imgList宽度跟随其中的图片数量发生改变-----
				// 获取imgList
				var imgList = document.getElementById("imgList");
				// 获取页面中所有的img标签
				var imgArr = document.getElementsByTagName("img");
				// 设置imgList的宽度
				imgList.style.width = 520 * imgArr.length+"px";
				
				// -----设置默认情况下第一个选择框为选中-----
				// 默认显示图片的索引
				var index = 0;
				// 获取所有的a
				var allA = document.getElementsByTagName("a");
				// 设置默认选中的效果
				allA[index].style.backgroundColor = "black";
				// ----点击对应超链接，切换到指定图片-----
				// 为所有的超链接都绑定绑定单击响应函数,i用来循环遍历
				for(var i=0;i<allA.length;i++){
					// 为每一个超链接添加一个num属性，用来标识其次序
					allA[i].num = i;
					//-----选中图片并进行切换-----
					allA[i].onclick = function(){
						// 获取单击超链接的索引，并将其设置为index，表示当前选中了哪一个元素
						index = this.num;
						// 切换图片
						// 第一张： 0 0
						// 第二张： 1 -520px
						// 第三张： 2 -1040px
						// imgList.style.left = -520 * index +"px";
						
						// 修改正在选中的a
						allA[index].style.backgroundColor = "black";
						// 设置选中的a
						setA();
						// 使用move函数来来切换图片
						move(imgList,"left",-520*index,20,function(){
							
						});
					};
				};
				
				
				// 创建一个工具函数用来设置选中的a
				function setA(){
					// 对所有的a进行遍历后，将对应的背景颜色设置为红色
					for(var i=0;i<allA.length;i++){
						allA[i].style.backgroundColor = "";
					}
					// 将选中的a设置为黑色
					allA[index].style.backgroundColor="black";
				};	
			};
		</script>
	</head>
	<body>
		<div id="outer">
			<ul id="imgList">
				<li><img src="../../img/kiss.jpeg" style="width: 500px;"></li>
				<li><img src="../../img/yanyan.jpeg" style="width: 500px;"></li>
				<li><img src="../../img/lzy.jpeg" style="width: 500px;"></li>
			</ul>
			<!-- 创建导航按钮 -->
			<div id="navDiv">
				<a href="javascript:;"></a>
				<a href="javascript:;"></a>
				<a href="javascript:;"></a>
			</div>
		</div>
	</body>
</html>
```

实现自动切换

- 解决最后一张图片到第一张图的切换效果问题：
  - 在最后一张图片之后添加第一张图片标签
  - 在选中导航栏的工具函数中设置对最后一张图片的索引的判断：如果到了最后一张图，则将索引index设置为0。
  - 此时显示的是最后一张图片，而最后一张图片与第一张是一样的。可以通过css将最后一张切换成第一张。
- 单击响应函数的切换和自动切换的冲突：
  - 点击的优先级更高，因此在点击的时候应该停止自动播放
  - 为了解决点击之后不再自动切换的问题，应该在move函数的回调函数中加入自动切换的函数，使得每次点击的move后都会开启自动切换
    `move(imgList, "left", -520 * index, 20, function() {autoChange()// -----自动切换图片-----});`

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>李泽言的轮播图❤</title>
		<script type="text/javascript" src="tools.js">

		</script>
		<style type="text/css">
			* {
				margin: 0;
				padding: 0;
			}

			#outer {
				width: 520px;
				height: 320px;
				/* 居中 */
				margin: 50px auto;
				background-color: yellowgreen;
				/* overflow: hidden; */
				padding: 10px 0;
				position: relative;
				/* 裁剪溢出的内容 */
				overflow: hidden;
			}

			/* 设置imgList */
			#imgList {
				/* 去除列表符号 */
				list-style: none;
				/* 开启绝对定位 */
				position: absolute;
			}

			#imgList li {
				/* 设置浮动 */
				float: left;
				/* 设置左右外边距 */
				margin: 0 10px;
				/* 开启相对定位 */
				position: relative;
			}

			/* 设置导航按钮 */
			#navDiv {
				/* 开启绝对定位 */
				position: absolute;
				/* 设置位置 */
				bottom: 15px;
				/* 设置水平居中 */
				/* 相对父元素偏移 */
				left: 50%;
				/* 相对元素自身偏移 */
				transform: translateX(-50%);
			}

			#navDiv a {
				/* 在设置浮动的时候，一方面可以将行元素转化为块元素，另一方面可以使得元素脱离文档流 */
				float: left;
				/* 设置超链接宽高 */
				width: 20px;
				height: 20px;
				background-color: red;
				/* 设置左右外边距 */
				margin: 0 5px;
				/* 设置透明效果 */
				opacity: 0.5;
				/* 兼容IE8 的透明 */
				filter: alpha(opacity=50);
			}

			/* 设置鼠标移入的效果 */
			#navDiv a:hover {
				background-color: black;
			}
		</style>
		<script type="text/javascript">
			window.onload = function() {
				// -----设置imgList宽度跟随其中的图片数量发生改变-----
				// 获取imgList
				var imgList = document.getElementById("imgList");
				// 获取页面中所有的img标签
				var imgArr = document.getElementsByTagName("img");
				// 设置imgList的宽度
				imgList.style.width = 520 * imgArr.length + "px";

				// -----设置默认情况下第一个选择框为选中-----
				// index为显示图片的索引（全局变量，默认值为0）
				var index = 0;
				// 获取所有的a
				var allA = document.getElementsByTagName("a");
				// 设置默认选中的效果
				allA[index].style.backgroundColor = "black";
				// ----点击对应超链接，切换到指定图片-----
				// 为所有的超链接都绑定绑定单击响应函数,i用来循环遍历
				for (var i = 0; i < allA.length; i++) {
					// 为每一个超链接添加一个num属性，用来标识其次序
					allA[i].num = i;
					//-----选中图片并进行切换-----
					allA[i].onclick = function() {
						// 在点击的时候关闭自动切换定时器
						clearInterval(timer);
						
						// 获取单击超链接的索引，并将其设置为index，表示当前选中了哪一个元素
						index = this.num;
						// 切换图片
						// 第一张： 0 0
						// 第二张： 1 -520px
						// 第三张： 2 -1040px
						// imgList.style.left = -520 * index +"px";

						// 修改正在选中的a
						allA[index].style.backgroundColor = "black";
						// 设置选中的a
						setA();
						// 使用move函数来来切换图片
						move(imgList, "left", -520 * index, 20, function() {
							// -----自动切换图片-----
							 autoChange()
						});
					};
				};
				
				// -----自动切换图片-----
				 autoChange()
				
				// 获取定时器的标识
				var timer;
				// 创建一个工具函数用来设置选中的a
				function setA() {
					// 判断当前索引是否是最后一张图片
					if(index >= imgArr.length - 1){
						// 则将index设置为0
						index = 0;
						// 可以通过css将最后一张切换成第一张
						imgList.style.left = 0;
					}
					
					// 对所有的a进行遍历后，将对应的背景颜色设置为红色
					for (var i = 0; i < allA.length; i++) {
						allA[i].style.backgroundColor = "";
					}
					// 将选中的a设置为黑色
					allA[index].style.backgroundColor = "black";
				};
				// 创建一个工具函数函数用来开启自动切换
				function autoChange() {
					// 开启一个定时器用来定时切换图片(每3秒切换一次)
				    timer = setInterval(function() {
						// 使得索引自增
						index ++;
						// 判断index的值
						index %= imgArr.length;
						// 执行动画来切换图片
						move(imgList, "left", -520 * index, 20, function() {
							// 修改导航点(在动画切换完毕之后)
							setA();
						})
					}, 3000);
				};
			};
		</script>
	</head>
	<body>
		<div id="outer">
			<ul id="imgList">
				<li><img src="../../img/kiss.jpeg" style="width: 500px;"></li>
				<li><img src="../../img/yanyan.jpeg" style="width: 500px;"></li>
				<li><img src="../../img/lzy.jpeg" style="width: 500px;"></li>
				<li><img src="../../img/kiss.jpeg" style="width: 500px;"></li>
			</ul>
			<!-- 创建导航按钮 -->
			<div id="navDiv">
				<a href="javascript:;"></a>
				<a href="javascript:;"></a>
				<a href="javascript:;"></a>
			</div>
		</div>
	</body>
</html>
```

**实现自动切换**

* 解决最后一张图片到第一张图的切换效果问题

  * 在最后一张图片之后添加第一张图片标签
  * 在选中导航栏的工具函数中设置最后一张图片的索引判断：如果到了最后一张图，则将索引index设置为0
  * 此时显示的是最后一张图片，而最后一张图片与第一张是一样的。可以通过css将最后一张切换为第一张

* 单击响应函数的切换和自动切换的冲突

  * 点击的优先级更高，因此在点击的时候应该停止自动播放
  * 为了解决点击之后不再自动切换的问题，应该在move函数的回调函数中加入自动切换的函数，使得每次点击后的move后都会自动开启自动切换 

  `move(imgList, "left", -520 * index, 20, function() {autoChange()// -----自动切换图片-----});`

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>李泽言的轮播图❤</title>
		<script type="text/javascript" src="tools.js">

		</script>
		<style type="text/css">
			* {
				margin: 0;
				padding: 0;
			}

			#outer {
				width: 520px;
				height: 320px;
				/* 居中 */
				margin: 50px auto;
				background-color: yellowgreen;
				/* overflow: hidden; */
				padding: 10px 0;
				position: relative;
				/* 裁剪溢出的内容 */
				overflow: hidden;
			}

			/* 设置imgList */
			#imgList {
				/* 去除列表符号 */
				list-style: none;
				/* 开启绝对定位 */
				position: absolute;
			}

			#imgList li {
				/* 设置浮动 */
				float: left;
				/* 设置左右外边距 */
				margin: 0 10px;
				/* 开启相对定位 */
				position: relative;
			}

			/* 设置导航按钮 */
			#navDiv {
				/* 开启绝对定位 */
				position: absolute;
				/* 设置位置 */
				bottom: 15px;
				/* 设置水平居中 */
				/* 相对父元素偏移 */
				left: 50%;
				/* 相对元素自身偏移 */
				transform: translateX(-50%);
			}

			#navDiv a {
				/* 在设置浮动的时候，一方面可以将行元素转化为块元素，另一方面可以使得元素脱离文档流 */
				float: left;
				/* 设置超链接宽高 */
				width: 20px;
				height: 20px;
				background-color: red;
				/* 设置左右外边距 */
				margin: 0 5px;
				/* 设置透明效果 */
				opacity: 0.5;
				/* 兼容IE8 的透明 */
				filter: alpha(opacity=50);
			}

			/* 设置鼠标移入的效果 */
			#navDiv a:hover {
				background-color: black;
			}
		</style>
		<script type="text/javascript">
			window.onload = function() {
				// -----设置imgList宽度跟随其中的图片数量发生改变-----
				// 获取imgList
				var imgList = document.getElementById("imgList");
				// 获取页面中所有的img标签
				var imgArr = document.getElementsByTagName("img");
				// 设置imgList的宽度
				imgList.style.width = 520 * imgArr.length + "px";

				// -----设置默认情况下第一个选择框为选中-----
				// index为显示图片的索引（全局变量，默认值为0）
				var index = 0;
				// 获取所有的a
				var allA = document.getElementsByTagName("a");
				// 设置默认选中的效果
				allA[index].style.backgroundColor = "black";
				// ----点击对应超链接，切换到指定图片-----
				// 为所有的超链接都绑定绑定单击响应函数,i用来循环遍历
				for (var i = 0; i < allA.length; i++) {
					// 为每一个超链接添加一个num属性，用来标识其次序
					allA[i].num = i;
					//-----选中图片并进行切换-----
					allA[i].onclick = function() {
						// 在点击的时候关闭自动切换定时器
						clearInterval(timer);
						
						// 获取单击超链接的索引，并将其设置为index，表示当前选中了哪一个元素
						index = this.num;
						// 切换图片
						// 第一张： 0 0
						// 第二张： 1 -520px
						// 第三张： 2 -1040px
						// imgList.style.left = -520 * index +"px";

						// 修改正在选中的a
						allA[index].style.backgroundColor = "black";
						// 设置选中的a
						setA();
						// 使用move函数来来切换图片
						move(imgList, "left", -520 * index, 20, function() {
							// -----自动切换图片-----
							 autoChange()
						});
					};
				};
				
				// -----自动切换图片-----
				 autoChange()
				
				// 获取定时器的标识
				var timer;
				// 创建一个工具函数用来设置选中的a
				function setA() {
					// 判断当前索引是否是最后一张图片
					if(index >= imgArr.length - 1){
						// 则将index设置为0
						index = 0;
						// 可以通过css将最后一张切换成第一张
						imgList.style.left = 0;
					}
					
					// 对所有的a进行遍历后，将对应的背景颜色设置为红色
					for (var i = 0; i < allA.length; i++) {
						allA[i].style.backgroundColor = "";
					}
					// 将选中的a设置为黑色
					allA[index].style.backgroundColor = "black";
				};
				// 创建一个工具函数函数用来开启自动切换
				function autoChange() {
					// 开启一个定时器用来定时切换图片(每3秒切换一次)
				    timer = setInterval(function() {
						// 使得索引自增
						index ++;
						// 判断index的值
						index %= imgArr.length;
						// 执行动画来切换图片
						move(imgList, "left", -520 * index, 20, function() {
							// 修改导航点(在动画切换完毕之后)
							setA();
						})
					}, 3000);
				};
			};
		</script>
	</head>
	<body>
		<div id="outer">
			<ul id="imgList">
				<li><img src="../../img/kiss.jpeg" style="width: 500px;"></li>
				<li><img src="../../img/yanyan.jpeg" style="width: 500px;"></li>
				<li><img src="../../img/lzy.jpeg" style="width: 500px;"></li>
				<li><img src="../../img/kiss.jpeg" style="width: 500px;"></li>
			</ul>
			<!-- 创建导航按钮 -->
			<div id="navDiv">
				<a href="javascript:;"></a>
				<a href="javascript:;"></a>
				<a href="javascript:;"></a>
			</div>
		</div>
	</body>
</html>
```

### 十四、以class对元素样式进行操作与工具函数

#### 1.类的操作

通过style属性来修改元素的样式，每修改一个样式，浏览器就需要重新渲染一次页面。在这种情况下执行的性能比较差，而且这种形式但我们需要修改多个样式的时候并不方便。并且存在行为和样式的耦合问题。

↓

我们可以同时修改元素的class属性来间接的修改样式。这样我们只需要修改一次，即可同时修改多个样式，浏览器只需要重新渲染页面一次，性能比较好，并且这种方式可以使得表现和行为进一步分离。

(1)判断函数：判断一个元素中是否含有class属性值

* 参数
  * obj：需要被判断class的元素
  * cn：被判断的class值

```javascript
// 定义一个工具函数，功能：判断一个元素中是否含有class属性值
function hasClass(obj, cn){
    // 判断obj中是否有cn这个className
    // 创建一个正则表达式:\b表示单词边界，用来指明有与cn完全相同的类名
    // 注意这里要通过构造函数的方式构造正则表达式，不能使用var reg = /\bb2\b/;
    // 由于转义字符的存在，这一用的是\\b
    var reg = new RegExp("\\b"+cn+"\\b");
    return reg.text(obj.className);
}
```

(2)添加函数：想一个元素中添加指定的class属性值

- 参数：
  - obj : 需要被添加class的元素
  - cn : 要添加的class值

```javascript
function addClass(obj, cn){
    // 检查obj中是否含有cn 
    if(!hasClass(obj, cn)){
        obj.className += " "+cn;
    }
}
```

(3)删除函数：删除一个元素中指定的class属性

- 参数：
  - obj : 需要被删除class的元素
  - cn : 被删除的class值

```javascript
function removeClass(obj,cn){
    // 思路：将某指定的cn替换为空串
    // 创建一个正则表达式
    var reg = new RegExp("\\b"+cn+"\\b");
    // 删除正则表达式中的内容
    obj.className = obj.className.replace(reg,"")
}
```

(4)切换函数：如果函数中有该类，则删除；如果函数中没有该类，则添加

```javascript
function toggleClass(obj,cn){
    if(hasClass(obj,cn)){
        addClass(obj,cn);
    }else{
        removeClass(obj,cn);
    }
}
```

**二级菜单练习**

* HTML结构

```html
<div id="my_menu" class="sdmenu">
        <!-- 一个二级菜单 -->
        <div>
            <span class="menuSpan">在线工具</span>
            <a href="#">图像优化</a>
            <a href="#">收藏夹图标生成器</a>
            <a href="#">邮件</a>
            <a href="#">htaccess密码</a>
            <a href="#">梯度图像</a>
            <a href="#">按钮生成器</a>
        </div>
        
        <!-- 一个二级菜单 -->
        <div class="collapsed">
            <span class="menuSpan">合作伙伴</span>
            <a href="#">JavaScript工具包</a>
            <a href="#">CSS驱动</a>
            <a href="#">CodingForums</a>
            <a href="#">CSS例子</a>
        </div>
        
        <!-- 一个二级菜单 -->
        <div class="collapsed">
            <span class="menuSpan">测试电流</span>
            <a href="#">Current or not</a>
            <a href="#">Current or not</a>
            <a href="#">Current or not</a>
        </div>	
</div>
```

- 每一个二级菜单都是一个div，当div具有collapsed这个类时，div就是折叠的状态，当没有这个类的时候，就是展开的状态。
- 点击菜单，切换菜单的显示状态（注意，要点击的是span标签）
- 封装思想：引入工具tools.js
  `<script type="text/javascript" src="../BOM/tools.js"></script>`
- 解决由于上一个被点击的元素就是其自身，因此再次点击的时候无法打开的情况
  `if(openDiv!=parentDiv) // 判断openDiv和被点击的parentDiv是否相同`
- 统一动画效果的修改：
  为了可以统一处理动画的过渡效果，我们将addClass改为toggleClass，但 此处的toggleClass不需要有移除的功能，为了达到这个目的，需要增加判断条件!hasClass(openDiv , "collapsed")，这样进入该语句块的内容只包括没有collapsed类的元素
  `if (openDiv != parentDiv && !hasClass(openDiv , "collapsed"))`

###### （1）基本功能实现

```html
<head>
<meta charset="utf-8">
<title>二级菜单</title>
<style type="text/css">
    * {
        margin: 0;
        padding: 0;
        list-style-type: none;
    }

    a,
    img {
        border: 0;
        text-decoration: none;
    }

    body {
        font: 12px/180% Arial, Helvetica, sans-serif;
    }
</style>
<!-- 引入工具类 -->
<script type="text/javascript" src="../BOM/tools.js"></script>
<script type="text/javascript">
    window.onload = function() {
        // 获取所有class为menuSpan的元素
        // querySelectorAll() 方法返回文档中匹配指定 CSS 选择器的所有元素
        var menuSpan = document.querySelectorAll(".menuSpan");

        // 定义一个变量来保存当前打开的菜单,初始为第一个div（第一个二级菜单）
        var openDiv = menuSpan[0].parentNode;

        // 为span绑定单击响应函数
        for (var i = 0; i < menuSpan.length; i++) {
            menuSpan[i].onclick = function() {
                // 对当前元素操作：this代表当前点击的span 
                // 获取当前span的父元素
                var parentDiv = this.parentNode;
                // 对于parentDiv：如果叠起则打开，如果打开则叠起
                toggleClass(parentDiv, "collapsed");

                // 判断openDiv和被点击的parentDiv是否相同
                if (openDiv != parentDiv && !hasClass(openDiv , "collapsed")) {
                    // 对之前已经打开的元素操作：打开菜单之后，应该关闭之前打开的菜单
                    // 为了可以统一处理动画的过渡效果，我们将addClass改为toggleClass
                    // addClass(openDiv, "collapsed");
                    // 此处的toggleClass不需要有移除的功能，为了达到这个目的，需要增加判断条件!hasClass(openDiv , "collapsed")
                    // 进入该语句块的内容只包括没有collapsed类的元素
                    toggleClass(openDiv, "collapsed");
                }
                
                // 修改openDiv为当前打开的菜单
                openDiv = parentDiv;
            };
        }
    }
</script>
</head>
```

###### (2)动画效果

在切换之前获取一次元素的高度，在切换之后再获取一次元素的高度，然后通过内联样式将元素的高度设置为初始值，此时的效果是元素的高度并没有因为切换发生改变。然后执行动画从初始值向终值过渡。此处应该通过回调函数解决内联样式的高优先级问题，否则函数只有一次起效果。

```javascript
// 工具函数：设置切换的效果
function toggleMenu(obj){
    // 在切换之前，首先获取元素高度
    var begin = obj.offsetHeight;

    // 对于parentDiv：如果叠起则打开，如果打开则叠起
    toggleClass(obj, "collapsed");

    // 在切换后，获取元素的高度
    var end = obj.offsetHeight;
    // ------动画效果：将高度从begin向end过渡------
    // 通过内联样式将元素的高度重置为begin（此时元素高度不会发生任何变化）
    obj.style.height = begin + "px";
    // 将高度从begin向end过渡
    move(obj,"height",end,10,function(){
        // 动画执行完毕，内联样式没有存在的意义，删除之
        obj.style.height="";
    });
}
```

汇总

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>二级菜单</title>
		<style type="text/css">
			* {
				margin: 0;
				padding: 0;
				list-style-type: none;
			}

			a,
			img {
				border: 0;
				text-decoration: none;
			}

			body {
				font: 12px/180% Arial, Helvetica, sans-serif;
			}
		</style>
		<!-- 引入工具类 -->
		<script type="text/javascript" src="../BOM/tools.js"></script>
<script type="text/javascript">
window.onload = function() {
// 获取所有class为menuSpan的元素
// querySelectorAll() 方法返回文档中匹配指定 CSS 选择器的所有元素
var menuSpan = document.querySelectorAll(".menuSpan");

// 定义一个变量来保存当前打开的菜单,初始为第一个div（第一个二级菜单）
var openDiv = menuSpan[0].parentNode;

// 为span绑定单击响应函数
for (var i = 0; i < menuSpan.length; i++) {
    menuSpan[i].onclick = function() {
        // 对当前元素操作：this代表当前点击的span 
        // 获取当前span的父元素
        var parentDiv = this.parentNode;

        // 调用切换的工具函数
        toggleMenu(parentDiv);

        // 判断openDiv和被点击的parentDiv是否相同
        if (openDiv != parentDiv && !hasClass(openDiv , "collapsed")) {
            // 对之前已经打开的元素操作：打开菜单之后，应该关闭之前打开的菜单
            // 为了可以统一处理动画的过渡效果，我们将addClass改为toggleClass
            // addClass(openDiv, "collapsed");
            // 此处的toggleClass不需要有移除的功能，为了达到这个目的，需要增加判断条件!hasClass(openDiv , "collapsed")
            // 进入该语句块的内容只包括没有collapsed类的元素
            //toggleClass(openDiv, "collapsed");
            // 调用切换的工具函数
            toggleMenu(parentDiv);
        }
        // 修改openDiv为当前打开的菜单
        openDiv = parentDiv;
    };
};

// 工具函数：设置切换的效果
function toggleMenu(obj){
    // 在切换之前，首先获取元素高度
    var begin = obj.offsetHeight;

    // 对于parentDiv：如果叠起则打开，如果打开则叠起
    toggleClass(obj, "collapsed");

    // 在切换后，获取元素的高度
    var end = obj.offsetHeight;
    // ------动画效果：将高度从begin向end过渡------
    // 通过内联样式将元素的高度重置为begin（此时元素高度不会发生任何变化）
    obj.style.height = begin + "px";
    // 将高度从begin向end过渡
    move(obj,"height",end,10,function(){
        // 动画执行完毕，内联样式没有存在的意义，删除之
        obj.style.height="";
    });
}
};
</script>
	</head>
```

#### 2.JSON

js中的对象只有js自己认识，其他语言都无法识别。而JSON作为一种特殊格式的字符串，可以被任意的语言识别，并转换为任意语言中的对象。JASON(JavaScript Object Natation JS对象表示法)在开发中主要用来做数据的交互。

* JSON和JS对象的格式一样，只不过JSON字符串中的属性名必须加双引号
* 分类
  * 对象：{}
  * 数组：[]
* 允许的值
  * 字符串、数值、布尔值、null、对象（不包括函数对象）、数组

```javascript
var obj='{"name":"孙悟空"，"age":18,"gender":"男"}';
var arr='[1,2,3,"hello",true]';
var obj2='{"arr":[1,2,3]}';
```

- 将JSON字符串转换为JS中的对象：一个工具类JSON，这个类可以帮助我们将JSON转换为JS对象，也可以把一个JS对象转换为JSON
  - JSON---->JS对象：JSON.parse()
    - 需要一个JSON字符串作为参数，会将该字符串转换为JS对象并返回 `var o = JSON.parse(obj);`
  - JS对象---->JSON：JSON.stringify()
    - 需要一个JS对象作为参数，返回一个JSON对象`var str = JSON.stringify(o);`
- JSON这个对象在IE7及以下的浏览器中不支持，所以在这些浏览器中调用时，会报错
  - 方案一（优）：引入外部json2.js文件
  - 方案二：eval()可以用来执行一段字符串类型的jS代码，并将执行结果返回当成代码块解析，需要在其前后各加入一个括号
  - 使用该函数可以将JSON转换为JS对象
  - 功能很强大，但是尽量不要使用，首先性能很差，而且有安全隐患

```javascript
var obj='{"name":"孙悟空"，"age":18,"gender":"男"}';
eval("("+obj+")");
```


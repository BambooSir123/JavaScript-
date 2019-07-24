
## (一)基本语法
### 1.注释

单行注释：
```javascript
//注释
```
多行注释：
```javascript
/*注释
*/
```

推荐注释多行方法：
```javascript
/*
*
*
```
### 2.严格模式

对ECMASCript3中不确定的行为的得到处理，不安全的操作也会抛弃
启用严格模式，在顶部加入代码：
```javascript
"use strict"
```
也可以在函数中加入此语句，函数将会按照严格模式执行

### 3.语句
(与C/C++类似)

**区分大小写**

每个语句以 *;*进行结尾
当遇到控制语句(eg:if)时，语句要执行的多条语句用{}包含

PS:个人怀疑是C的私生子

***
## (二)变量

### 1.变量创建
javascript的变量是松散型(可以用来保存任何类型的数据)
换句话说，仅仅是用于保存值的占位符。

*局部变量*
 创建局部变量如下:
```javascript
var a;
```

*全局变量*

省略var进行创建
```javascript
a;
```

### 2.数据类型
#### typeof 操作符
用来检测当前变量的类型:
* string 数字
* object 对象
* function 函数
* undefined 未定义
* string 字符串
* boolean bool值

#### undefined 类型
未定义的变量
该类型只有一个值，那就是特殊的undefined
```javascript
var a;
alert(a==undefined); //true

var a=undefined;
alert(a==undefined); //true
```
未定义的值和未创建的值不同

但未初始化的变量执行typeof时显示的值也是undefined

#### Null 类型
该类型只有一个值null
逻辑角度null表示一个空对象指针
因此typeof检测Null时返回object类型
```javascript
var car=null;
alert(typeof car); //object
```
如果变量将会用于保存对象，可以将变量初始化为null,只要检查null

的值就可以知道相应变量是否已经保存了一个对象的引用

```javascript
if(car!=null)
{

}
```

null值时undefined的衍生

但两者的用途不同
```javascript
alert(null==undefined) //true
```
#### Boolean 类型


数据类型|true|false|
-|-|-|
boolean|true|false|
number|非0数字|0|
object|全部|无|
string|非空字符串|空字符串`""`|
undefined|无|全部|

可以用Boolean()函数转换类型
```javascript
var a="听竹先生";
var b=Boolean(a);
```

#### Number类型

*0开头*

八进制
```javascript
var a=070;
```
*0x开头*

十六进制

```javascript
var a=0xA;
```

*浮点数*

```javascript
var a=1.1; //1.1
var a=.2 //0.2
var a=1.; //解析为1
var a=10.0; //解析是10
var a=3.125e7; //31250000
```
算术精度不高，不要做一些奇奇怪怪的尝试

eg:
0.1+0.2=0.30000000000000004

PS:基于IEEE754的浮点计算都有这个问题
#### NaN类型
非数值（not a number)

所有应该返回数值的值却没有返回数值，返回了NaN

NaN不与任何值相等，包括本身
```javascript
alert(NaN==NaN) //false
```
可以用*isNaN()* 函数检测参数是不是数值
```javascript
alert(isNaN("10")); //false 可以转换为数值
alert(isNaN("hello world")); //true,不能转换为数值
```

#### 数值转换
##### Number()
boolean值直接转换为1或0

数值直接传入返回

null值返回0

undefined返回NaN

字符串

* 如果只包含数字，直接转换
* 浮点数格式一样转换
* 0xf转换为十六进制数
* 空字符串则转换为0
* 包含其他字符，则NaN

##### parseInt()

*无法转换浮点数，浮点数后面部分都会被省略*

从第一个字符检测，若不是数字或者'-'则返回NaN

直到解析到遇到非数字

无法识别八进制

如果要转换为其他进制数

后面提交第二个参数
parseInt("070",8) //56

```javascript
parseInt("1234dafsaf") //1234
```
##### parseFloat()

与楼上基本类似，但是能识别浮点，但是只能识别第一个
当遇到第二个浮点时，就会停止解析

```javascript
paseFloat("22.34.2") //22.34
```
#### String 类型

(与python类似)

用"" 或 ''包含，两者没有区别，但是同一个字符串结尾符号必须和单引号相同

*字符字面量*
根据ASCII自己查阅

*ECMAScript的字符串创建后是不可变的*
要改变必须销毁之前的变量
```javascript
var a="java";
a=a+"script";
```

##### 字符串转换
函数:
String()
方法:
.toString()
```javascript
var num=10;
alert(num.toString()); //"10"
alert(num.toString(2)); //"1010"
alert(num.toString(8)); //"12"
alert(num.toString(10)); //"10"
alert(num.toString(16)); //"a"

var a=10;
alert(String(a)); //"10"
```

#### object 类型
*一组功能和数据的集合*

创建方式 new

```javascript
var o=new object();
```
object有的属性与方法：
* constructor 保存用于创建当前对象的函数
* hasOwnProperty(propertyName) 用于检查给定的属性在当前对象示例中是否存在
* isProperty(object) 用于检查传入的对象是否是当前对象的原型
* propertyIsEnumerable(propertyName) 用于检查给定的属性是否能够使用for-in枚举
* toLocaleString() 返回对象的字符串表示，该字符串与执行环境的地区堆应
* toString() 返回对象的字符串表示
* valueOf() 返回对象的字符串、数值或布尔值表示，通常与楼上相同

## (三) 操作符
(与C/C++相似)
### 基本操作符

```javascript
'+' '-' '*' '/' ......
存在
i++
--i
i=+a

大于：>
小于：<
全等：==
不全等：===
取模：%
条件语句：?
a?b:c;

```
#### 位操作符
#### 按位非(NOT)
符号：`~`表示
```javascript
var a =25; //二进制 00000000000000000000000000011001
var b=~a; //二进制 11111111111111111111111111100110
alert(b); //-26
```
*本质：操作数的相反数减1*

#### 按位与(AND)
符号：`&`表示
```javascript
var a =25; //二进制 00000000000000000000000000011001
var b =3; //二进制 00000000000000000000000000000011
var c=a&b   //二进制 00000000000000000000000000000001
```
#### 按位或(OR)
符号：`|`表示
```javascript
var a =25; //二进制 00000000000000000000000000011001
var b =3; //二进制 00000000000000000000000000000011
var c=a|b   //二进制 00000000000000000000000000011011
```

#### 左右移
符号：

`<<`表示左移

`>>`表示右移
```javascript
var a=2; //10
var b=a<<2 //1000 相当于8
```

# 基本语句

### if
(类似C/C++)
```javascript
var i=12;
if(i>25)
{
    alert("233");
}
else if(i<23)
{
    alert("233333");
}
else
{
    alert("23333333333");
}
```
### do-while
(类似C/C++)

```javascript
var i=0;
do{
    alert("23333");
    i++;
}while(i>3)
```
### while
(类似C/C++)

```javascript
var i=0;
while(i>21)
{
    i++;
    alert("23323");
}
```

### for语句
(类似C/C++)

```javascript
for(var a=0;i<10;i++)
{

}
```

### for-in语句
(类似python)
```javascript
for(number in numbers)
{
    
}
```

### label语句

emmm ~~比较特殊(~~没见过~~)~~(类似C/C++的go to语句)

添加标签，以便将来使用

帮助使用continue和break;

```javascript
var i=0;
var j=0;
start:for(;i>10;i++) //名字为start的label
{
    for(;j>20;j++)
    {
        alert("233");
        if(i>10&&j>13)
        {
            break start;
        }
    }
}
```
正常情况下，break只能跳出一层循环，
而由于label语句，可以直接跳出label标记的语句

### continue break

都是结束该次循环

continue是从头继续循环

break是结束循环

### with语句
**严格模式下不允许使用with语句**

**将会视作错误语句**

with(expression) statement;

将代码的作用域设置到一个特定的对象中
```javascript
var a=location.search.substring(1);
var b=location.hostname;
var c=location.href;
```
如果采用with语句进行简化

```javascript
with(location)
{
    var a=search.substring(1);
    var b=hostname;
    var c=href;
}
```

### switch语句
(类似C/C++)

```javascript
switch(i):
{
case 1:
    alert("2333");
    break;
case 2:
    alert("23333");
    break;
case 3:
    alert("233333");
    break;
case 4:
    alert("2333333");
    break;
default:
    alert("没找到");
}
```

### 函数
关键字：function
```javascript
function sayHi(name,message)
{
    alert("hello "+name+" "+message);
    return 0;
}
```
javascript与大多数语言不同，函数不介意传递多少参数，也不介意传递什么数据类型。即便你定义了两个参数，但是传递时不一定为两个参数，甚至可以多传，不传参数。

函数的参数用一个数组储存，函数不关心这个数组有哪些参数

可以通过arguments对象访问这个参数数组，从而获取传递给函数的每一个参数

argunments可以和参数名一起使用
```javascript
function doAdd(num1)
{
    alert(arguments.length);
    alert(arguments[0]+10);
    alert(arguments[0]+num1);
}

doAdd(10,20); // 2 20 20 
```
如果需要使用的参数没有被赋值，则默认值为undefined

### 没有重载
javascript 不支持重载
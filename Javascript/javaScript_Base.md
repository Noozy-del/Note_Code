# JavaScript
---
javascript 负责页面行为，运行在浏览器端脚本语言
## Js编写位置
1.可以编写到标签指定属性
```javascript
<button onclick="alert('hello');">我是按钮</button>
<a href="javascript:alert('aaa');">超链接</a>
```
2.可以写到script标签中
```javascript
<script type="text/javascript">
//编写js代码
</script>
```
3.写入外部JS文件中，通过标签引入
```javascript
<script type="text/javascript" src="文件路径"></script>
```
## 输出语句
```javascript
alert('内容~'); //弹出警告框
document.write('内容'); //写入body标签中，在页面显示
console.log('内容'); //开发者工具控制台
```
## 基本语法
js 函数声明不需要 ; 分号，但是赋值语句要加 ；分号
基本规则同 Java （不写不报错，程序自己加 ; ，但各方面资源有损耗，且易加错）

注释
```javascript
// 单行注释
/* 多行注释
*/
```
## 字面量和变量
字面量是固定值，如 1 2 3 true false null NaN "hello"
**字面量不可改变**
变量用来保存字面量，可声明赋值
```javascript
var a;
a = 1;
var b = 123;
```
###标识符
JS中可自主命名的内容认为是标识符
规范:
1.标识符含字母，数字，_，$
2.不以数字开头
3.无JS关键字和保留字
4.驼峰命名法 xxxYyyZzz

## 数据类型
**六种数据类型**
**5个基本数据类型 + object**

String 字符串
Number 数值
Boolean 布尔值
Null 空值
Undefined 未定义
Object 对象
### String字符串 ###
' ' 或 " " 引起
转义字符\
```javascript
\' => '
\" => "
"\t => 制表符"
"\n => 换行"
"\\ => \"
```
### Number数值 ###
最大值 Number.MAX_VALUES
最小值Number.,MIN_VALUES
超过范围 则无穷 Infinity /  -Infinity
非法数字 NaN

其他进制
0b 开头 二进制，但并非所有浏览器支持
0 开头 八进制
0x 开头 十六进制
### Boolean布尔值 ###
逻辑判断 true false
### Null空值 ###
专门表示为空对象null
typeof 检查Null 类型值返回 object
### Undefined未定义 ###
 如果一个变量声明但不赋值则 undefined
 typeof 检测返回 undefined
### Object 对象 ###
引用数据类型

## 类型转换 ##
**转换为String**
**方式一** 调用toString()方法
```javascript
var a = 123;
a = a.toString();
//对null和undefined报错
```
**方式二** 调用String()函数
包括null,undefined在内直接转为字符串
```javascript
var a;
a = String(a)//"undefined"
```
**方式三** 任意数据类型+""
```javascript
var a = true;
a = a + "";
```
**转为Number**
**方式一** Number函数
```javascript
var a = "123";
s = Number(a);//123
```
转换情况：
	1字符串转数字
		合法数字直接转
		非法数字转NaN
		空串或空格串转0
	2布尔值转数字
		true转1
		false转0
	3空值转数字
		null转0
	4未定义转数字
		underfined转NaN

**方式二** parseInt() 和parseFloat() 函数
对非String使用parseInt()或parseFloat()函数，它会先将其转为String再操作提取其数字位转换为Number （遇非数字数即停止读取）
也可指定小数位对于parseFloat()
```javascript
var a = "123.456px";
a = parseInt(a);// a = "123"
var b = "123.455px";
b = parseFloat(b,2);// b = "123.45"
```
**方式三** 一元+运算符
```javascript
var a = "123"
a = +a;//原理同Number()
```
**转为Boolean值**
**方式一** Boolean()函数
```javascript
var a = "false"
a = Boolean(a);// a = true
```
转换情况：
	1.字符串转Boolean
		除空串全是true
	2.数值转Boolean
		除0和NaN全是true
	3.null 和 undefined转 Boolean
		全是false
	4.对象转Boolean
		全是true


**方式二** !!运算
任意数据类型做两次！！运算，即可转换为boolean
```javascript
var a = "hello"
a = !!a;
```
## 基础语法 ##
### 运算符 ###
运算符称为操作符
通过运算对一个或多个值进行运算操作

**typeof运算符**
检查数据变量类型，返回一个描述类型的字符串作为结果

**算数运算符**
+，-，*，/，%
**除了加法外对非Number类型运算都会先转为Number再运算**

**一元运算符 **
一元+，正号不对值产生任何影响，但可以将非数字转换为数字
```javascript
var a = true;
a = +a;// 1
```
一元减，就是负号，对数字取反

自增
（++a),(a++)
规则同java

自减
（--a),(a--)
规则同java 

**逻辑运算符**
！
非运算对布尔值取反，对非布尔值，先转布尔值再取反
&&
与运算，短路与，对非布尔值先转布尔值再运算
||
短路或，同上

**赋值运算符**
=，+=，-=，*=，/=，%=

**关系运算符**
=，<，>......规则同数学运算

**相等运算符**
== 对不同类型进行数值转换，比较值
!= 数值转换比较不等
\=\=\= 全等，比较类型和值
!\== 不全等，比较类型和值

特殊情况：
	null和undefined的值
	由于undefined衍生于null，所以null == undefined会返回true
	但是 null === undefined 会返回false
	NaN不与任何值相等包括它自身
	判断一个值是否是NaN，用isNaN()函数

**三元运算符 ** 
条件表达式？语句1：语句2；
同java

**运算符优先级参考优先级表格**
### 流程控制语句 ###
```javascript
//if 条件判断语句
if(){
}eles if(){
}else{
}
//switch 条件分支语句
switch(){
	case 表达式1:break;
	case 表达式2:break;
	default: break;
}// 表达式的值进行全等比较！！
//while 循环语句
while(){}
//do..while() 循环语句
do{
}while()
//for 循环语句
for(;;){}
```
## 对象(Object) ##
对象是JS中一种符合数据类型，在对象中可以保存多个不同数据的属性
### 对象的分类 ###
1.内建对象
	由ES标准中定义的对象，在任何ES的实现中都可以使用
	如：Math,String,Number,Boolean,Function...
2.宿主对象
	由JS的运行环境提供的对象，目前来讲主要是由浏览器提供的对象
	如：BOM,DOM
3.自定义对象
	开发人员自己创建
```javascript
var obj = new Object();//方式一
var obj = {};//方式二
```
### 对象属性 ###
向对象中添加属性
	1 对象.属性名 = 属性值；
	2 对象["属性名"] = 属性值；//借以使用特殊属性名
		对象的属性名没有任何要求，不需要遵守标识符规范但是在开发中尽量按其要求去写，属性值也可以是任意数据类型
	3 使用对象字面量，在创建对象时向对象添加属性
```javascript
var obj = {
	属性名：属性值，
	属性名：属性值
}；
```

读取对象属性
	1 对象.属性名
	2 对象["属性名"]//"属性名"可以使用字符串常量,或者字符串变量
	如果读取一个对象没有的属性，它不会报错，而是返回undefined

删除对象中属性
	1 delete 对象.属性名
	2 delete 对象["属性名"]

遍历
	使用in检查对象是否含有指定属性
	"属性名" in 对象 返回true/false
```javascript
var obj = {'0':'a','1':'b','2':'c'};
for(var i in obj){
	console.log(i,":",obj[i]);
}
```
## 函数 ##
函数也是一个对象，也具有普通对象的功能（即包含属性）
typeof 检查函数返回 function
### 创建函数 ###
函数声明
```javascript
function 函数名(){}
var 函数名 = function(){};
```
立即执行函数
	函数定义完立即调用，仅执行一次
```javascript
(function(a,b){
	console.log("a = " + a);
	console.log("b = " + b);
})(123,456);
```
### 形参实参 ###
形参：形式参数
	声明在函数内但不赋值，在调用时赋值
实参：实际参数
	调用函数时,在()中传递实参，赋给付给对应形参
	调用函数时JS解析器不会检查实参的类型和个数，可以传递任意类型的值
	**如果实参数大于形参，多余实参不赋值** 
	**如果实参小于形参，没有对应值的形参赋undefined**
	返回值即函数执行结果
	return设置
	若不写return 或者return后不跟值默认返回undefined
### 方法 ###
可以将一个函数设置为对象属性，称其为对象方法
对象.方法名();

函数属性和方法

call()和apply():
	这两个方法是函数对象方法，用函数对象调用
	**将方法绑定到指定对象上，并进行调用** 
	利用第一个实参指定函数中this
	call 直接传递参数 apply 需要将实参封装到数组中传递
```javascript
function max(){}
console.log(max.call(Object,1,2,3));
var a = [1,2,3];
console.log(max.apply(Object,a))
```
arguments
	函数中隐含参数，类数组元素，封装执行过程实参
	其有属性callee表示当前执行函数对象
this
	this是函数上下文调用对象，根据函数调用方式不同会指向不同对象
	1 以函数形式调用，this是window
	2 以方法形式调用，this是调用方法对象
	3 以构造方法调用，this是新建对象
	4 使用call apply时，this时指定对象
	5 在全局作用域中this代表window
### 作用域 ###
变量作用范围，在js中分两种

1 全局作用域
	直接在script标签中编写的代码都运行在全局作用域中
	全局作用域在打开页面时创建，关闭时销毁
	全局作用域中有全局对象window，由浏览器提供
	可在页面中直接使用，代表整个浏览器窗口
	**在全局作用域中创建的变量都会作为window对象的属性保存**
	在全局作用域中创建的函数都会作为window对象方法保存
	在全局作用域中创建的变量和函数可以在页面任意位置访问
	在函数作用域中也可以访问到全局作用域的变量
	尽量不在全局创建对象
	
2函数作用域
	在函数执行创建作用域，执行结束时销毁
	其中变量不能在全局中访问
	当函数作用域中使用变量，先在自身作用域中寻找，再逐级向上
	
3 变量的声明提前
	在作用域中，使用var关键字声明的变量会在所有代码执行前被声明但是不会赋值。(预编译) 如果没有var声明，变成全局变量
	
4 函数的声明提前
	在作用域中使用，函数声明创建的函数会在所有代码执行之前被创建，(var fun = function(){})不包括。
### this ###
我们每次调用函数时，解析器都会将一个上下文对象作为隐含参数传递进函数，使用this引用上下文对象。
### 构造函数 ###
构造函数是专门创建对象的函数
通过一个构造函数创建的对象，称为一类对象
实质是普通函数，用new 来调用是构造函数
```javascript
function Person(){
	this.name = 'jack';
	this.sayName = function(){}
}
var p = new Person();
```
执行流程
1创建新对象
2将对象作为函数上下文this
3执行代码
4新建对象返回

**对象 instanceof 构造函数**
检查一个对象是否是一个类实例，返回Boolean
Object是所有对象祖先，均返回true
### 原型 ###
创建一个函数后，解析器会在默认函数中添加属性prototype
prototype属性指向一个对象，称为原型对象
当函数作为构造函数使用，它所创建的对象都会有一个隐含属性执行改原型对象。
**原型对象相当于一个公共区域，凡是通过同一个构造函数创建的对象，他们通常可以访问到相同原型对象**
对象公有的属性方法统一添加到原型对象
访问对象属性或者调用方法，先在自身寻找，再到原型寻找，再到原型的原型中寻找......
直到Object的原型null，没有找到返回undefined

对象.hasOwnProperty("属性名")
检查对象自身是否含某个属性
### toString()方法 ###
当我们直接在页面打印一个对象时，事件上输出的对象的toString()方法返回值。
当我们希望输出对象时不输出[Object,Object],可以为对象添加toString()方法
```javascript
Person.prototype.toString = function(){
	return "Person[name=" + this.name + "]";
};
```
### 垃圾回收(GC) ###
当对象没有任何变量属性对它引用时，成为垃圾
JS拥有自动垃圾回收机制，自动将这些垃圾对象从从内存中销毁
我们只需要将不再使用对象设置为null即可。
## 数组(Array) ##
数组也是一个对象，是一个用来存储数据的对象和Object类似，但是它的存储效率比普通对象要高
数组中保存的内容我们称作元素
数组使用索引来操作元素
### 数组操作 ###
```javascript
//创建数组
var arr = new Array();
var arr = [];
var arr = [1,2,3];
//添加元素
arr[0] = 123;
arr[1] = "hello";
arr[arr.length] = 123;
```
数组.length = 新长度
如果修改后的length大于原长度，多余部分空出来
小于原长度，多出元素删除
### 数组方法 ###








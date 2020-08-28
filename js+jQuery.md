# js

## js基本数据类型

 JS基本有5种简单数据类型：String，Number，Boolean，Null，Undefined。一种复杂的数据类型Object。 

### String

 String类型用于表示由零或多个16位Unicode字符组成的字符序列，即字符串。字符串可以由单引号（'）或双引号(")表示。 

```
var carName = "Porsche 911";   // 使用双引号
var carName = 'Porsche 911';   // 使用单引号
```

将其他数据类型转换为String类型，可以使用String()和toString()这两个方法的区别是String()可以转任何类型，而toString()方法不能转Null，undefined两种类型。

```
var a = 11;
console.log(a,typeof a);   //11 "number"
var b = a.toString();
console.log(b,typeof b);   //11 string
```

 可以在字符串内使用引号，只要这些引号与包围字符串的引号不匹配： 

```
var answer = "It's alright";             // 双引号内的单引号
var answer = "He is called 'Bill'";    // 双引号内的单引号
var answer = 'He is called "Bill"';    // 单引号内的双引号
```

### Number

JavaScript 只有一种数值类型Number。

写数值时用不用小数点均可：

```
var x1 = 34.00;     // 带小数点
var x2 = 34;        // 不带小数点
```

 超大或超小的数值可以用科学计数法来写： 

```
var y = 123e5;      // 12300000
var z = 123e-5;     // 0.00123
```

最基本的数值字面量格式是十进制整数，十进制可以在代码中直接输入。除了十进制，还可以用八进制和十六进制。

八进制字面值的第一位必须是零（0），然后八进制数字序列为（0~7），如果数字超出了0~7这个范围，那么前导0将被忽略，后面的数值按十进制解析。

```
var a = 070;   //八进制状态下的56
var b = 079;   //无效的八进制，解析为79
var c = 08;    //无效的八进制，解析为8
```

十六进制字面值前两位必须是0x,后跟任何十六进制数字（0~9及A~F），字母不区分大小写。

在算术运算时，八进制和十六进制都会被转换成十进制数值。

 **1.浮点数**

所谓浮点数值，就是该数值中必须包括一个小数点，并且小数点后面必须至少有一个数字。

由于保存浮点数所占用内存是整数的两倍，所以ECMAScript会尽可能将浮点数转换为整数。

如果小数点后没有任何数字或浮点数本身就表示一个整数，就会被转换为整数。

```
console.log(1.)    //1
console.log(10.00)   //10
```

默认情况下，ECMAScript会将小数点后面带6个零以上的浮点数值转换为以e表示法表示的数值。（例：0.0000003会被转换为3e-7）.

浮点数值的最高精度为17位。但算术计算精度远不如整数。例：0.1+0.2不是0.3，而是0.30000000000000004，这个小小的舍入误差会导致无法测试特定的浮点数值。

永远不要测试某个特定的浮点数值。

关于浮点数值计算产生舍入误差的问题：这是使用基于IEEE754数值的浮点计算的通病，ECMAScript并非独此一家，其他使用相同数值语言的也存在这个问题。

**2.NaN**

NaN（Not a Number），即非数值是一个特殊的数值，这个数值用于表示一个本来要返回数值的操作数未返回数值的情况。

NaN本身有两个特点：

1.任何涉及NaN的操作（例如NaN*10,NaN/10）都会返会NaN。

2.NaN与任何数值都不相等，包括NaN本身。

```
console.log(NaN == NaN);    //false
```

isNaN()，判断是否“不是数值”,这个函数接受一个参数，该参数可以是任何类型，isNaN()在接收到一个值之后，会尝试将值转换为数值，可以转换的将返回false,不能转换为数值的将会返回true。

**3.数值转换**

有3个函数可以把非数值转换为数值：number()，parseInt()和parseFloat()。

number()可以用于任何数据类型，而另外两个函数则专门用于把字符串转换为数值。

- 如果是Boolean，true和false将分别被转换为1和0。
- 如果是数字值，只是简单传入和返回。
- 如果是null值，返会0。
- 如果是undefined，返回NaN。
- 如果是字符串则较为复杂。

parseInt()在转换字符串的时会忽略字符串前的空格，直至找到第一个非空格字符。如果第一个字符不是数字字符或者是负号，返回NaN。

parseInt()可以接受两个参数，第一个为要转换的参数，第二个为基数（进制）。如果不指定基数意味着让parseInt()自己决定如何解析，因此为了避免错误的解析，建议指定基数。
parseFloat()用于转换浮点数。

### Boolean

此类型只有两个值：true和false，布尔值经常用在条件测试中。 

注意：boolean类型的字面值true和false是区分大小写的。

JavaScript中所有类型的值都有与这两个Boolean值等价的值。要将一个值转换为其对应的Boolean值，可以调用类型转换函数Boolean()，例如：

```
    var message = 'Hello World';
    var messageAsBoolean = Boolean(message);
```

下表列出了各种数据类型对应的转换规则

| **数据类型** | **转换为true** | **转换为false** |
| ------------ | -------------- | :-------------: |
| Boolean      | true           |      false      |
| String       | 任何非空字符串 |  ""(空字符串）  |
| Number       | 任何非零数字值 |     0和NaN      |
| Object       | 任何对象       |      null       |
| Undefined    | 不适用         |    undefined    |

### Null

Null类型也只有一个值，这个值是特殊的null,从逻辑角度来看，`null`值表示一个空对象指针，而这也正是使用`typeof`操作符检测`null`时会返回`object`的原因。

如果定义的变量将来准备用于保存对象，那么最好将该变量初始化为null，而不是其他值。这样一来，只要直接检测`null`值就可以知道相应的变量是否已经保存了一个对象的引用了。

实际上，undefined值是派生自null值的，因此ECMA-262规定对它们的相等性测试要返回true。

```
console.log(undefined == null); //true
```

在 JavaScript 中，null 是 "nothing"。它被看做不存在的事物。

不幸的是，在 JavaScript 中，null 的数据类型是对象。

您可以把 null 在 JavaScript 中是对象理解为一个 bug。它本应是 null。

您可以通过设置值为 null 清空对象：

```
var person = null;           // 值是 null，但是类型仍然是对象
```

### Undefined

`Undefined`类型只有一个值，即特殊的`undefined`。

在使用`var`声明变量但未对其加以初始化时，这个变量的值就是`undefined`。

声明但未初始化与尚未定义的变量还是不一样：

```
var message;     //age未声明

alert(message);    //"undefined"

alert(age);   //产生错误

alert(typeof(message));     //"undefined"

alert(typeof(age));     //"undefined"
```

### Undefined 与 Null 的区别

Undefined 与 null 的值相等，但类型不相等：

```
typeof undefined              // undefined
typeof null                   // object
null === undefined            // false
null == undefined             // true
```

### typeof 操作符

由于`js`中的变量是松散类型的，所以它提供了一种检测当前变量的数据类型的方法，也就是typeof关键字.
通过`typeof`关键字，对这5种数据类型会返回下面的值（以字符串形式显示)

```
undefined` ---------- 如果值未定义 `Undefined`
boolean` ---------- 如果这个值是布尔值 `Boolean
string` ---------- 如果这个值是字符串 `String
number` ---------- 如果这个值是数值类型 `Number
object` ---------- 如果这个值是对象或`null` `Object
```

需要注意的是`typeof null`返回为`object`,因为特殊值`null`被认为是一个空的对象引用。

## js函数

**JavaScript 函数是被设计为执行特定任务的代码块。**

**JavaScript 函数会在某代码调用它时被执行。**

```
function myFunction(p1, p2) {
    return p1 * p2;              // 该函数返回 p1 和 p2 的乘积
}
```

### 函数语法

JavaScript 函数通过 function关键词进行定义，其后是*函数名*和括号 ()。

函数名可包含字母、数字、下划线和美元符号（规则与变量名相同）。

圆括号可包括由逗号分隔的参数：

```
(参数 1, 参数 2, ...)
```

由函数执行的代码被放置在花括号中：*{}*

```
function name(参数 1, 参数 2, 参数 3) {
    要执行的代码
}
```

*函数参数（Function parameters）*是在函数定义中所列的名称。

*函数参数（Function arguments）*是当调用函数时由函数接收的真实的*值*。

在函数中，参数是局部变量。

在其他编程语言中，函数近似程序（Procedure）或子程序（Subroutine）。

### 函数参数

在调用函数时，您可以向其传递值，这些值被称为参数。这些参数可以在函数中使用。

您可以发送任意多的参数，由逗号 (,) 分隔：

```
myFunction(*argument1,argument2*)
```

当您声明函数时，请把参数作为变量来声明：

```
function myFunction(***var1***,***var2***)
{
*代码*
}
```

变量和参数必须以一致的顺序出现。第一个变量就是第一个被传递的参数的给定的值，以此类推。   

#### 函数显式参数(Parameters)与隐式参数(Arguments)

函数显式参数在函数定义时列出。

函数隐式参数在函数调用时传递给函数真正的值。

##### 参数规则

JavaScript 函数定义显式参数时没有指定数据类型。

JavaScript 函数对隐式参数没有进行类型检测。

JavaScript 函数对隐式参数的个数没有进行检测。

##### 默认参数

ES5 中如果函数在调用时未提供隐式参数，参数会默认设置为： **undefined**

有时这是可以接受的，但是建议最好为参数设置一个默认值：

```
 function myFunction(x, y) {    if (y === undefined) {          y = 0;    }  } 
```

##### arguments 对象

JavaScript 函数有个内置的对象 arguments 对象。

argument 对象包含了函数调用的参数数组。

通过这种方式你可以很方便的找到最大的一个参数的值：

```
 x = findMax(1, 123, 500, 115, 44, 88); 
 function findMax() {    
     var i, max = arguments[0];        
     if(arguments.length < 2) 
         return max;     
     for (i = 0; i < arguments.length; i++) {        
         if (arguments[i] > max) {            
             max = arguments[i];        
             }    
      }   
      return max; 
 } 


```

##### 通过值传递参数

在函数中调用的参数是函数的隐式参数。

JavaScript 隐式参数通过值来传递：函数仅仅只是获取值。

如果函数修改参数的值，不会修改显式参数的初始值（在函数外定义）。

隐式参数的改变在函数外是不可见的。

##### 通过对象传递参数

在JavaScript中，可以引用对象的值。

因此我们在函数内部修改对象的属性就会修改其初始的值。

修改对象属性可作用于函数外部（全局变量）。

修改对象属性在函数外是可见的。

### 函数调用

JavaScript 函数有 4 种调用方式。每种方式的不同在于 **this** 的初始化。

#### this 关键字

一般而言，在Javascript中，this指向函数执行时的当前对象。 注意 **this** 是保留关键字，你不能修改 **this** 的值。

#### 调用 JavaScript 函数

##### 1.作为一个函数调用

```
 function myFunction(a, b) {    
      return a * b; 
 } 
      myFunction(10, 2);           // myFunction(10, 2) 返回 20 
```

以上函数不属于任何对象。但是在 JavaScript 中它始终是默认的全局对象。

在 HTML 中默认的全局对象是 HTML 页面本身，所以函数是属于 HTML 页面。

在浏览器中的页面对象是浏览器窗口(window 对象)。以上函数会自动变为 window 对象的函数。

myFunction() 和 window.myFunction() 是一样的：

```
 function myFunction(a, b) {    
      return a * b; 
 } 
       window.myFunction(10, 2);            // window.myFunction(10, 2) 返回 20 
```

 这是调用 JavaScript 函数常用的方法， 但不是良好的编程习惯 全局变量，方法或函数容易造成命名冲突的bug。

**全局对象**

当函数没有被自身的对象调用时 **this** 的值就会变成全局对象。

在 web 浏览器中全局对象是浏览器窗口（window 对象）。

该实例返回 **this** 的值是 window 对象:

```
function myFunction() {    
   return this; 
} 
myFunction();                // 返回 window 对象
```

函数作为全局对象调用，会使 **this** 的值成为全局对象。 使用 window 对象作为一个变量容易造成程序崩溃。

##### 2.函数作为方法调用

在 JavaScript 中你可以将函数定义为对象的方法。

以下实例创建了一个对象 (**myObject**), 对象有两个属性 (**firstName** 和 **lastName**), 及一个方法 (**fullName**):

```
var myObject = {    
     firstName:"John",    
     lastName: "Doe",    
     fullName: function () {       
        return this.firstName + " " + this.lastName;    
     } 
} 
myObject.fullName();         // 返回 "John Doe"
```

**fullName** 方法是一个函数。函数属于对象。 **myObject** 是函数的所有者。

**this**对象，拥有 JavaScript 代码。实例中 **this** 的值为 **myObject** 对象。

测试以下！修改 **fullName** 方法并返回 **this** 值:

```
var myObject = {    
     firstName:"John",    
     lastName: "Doe",    
     fullName: function () {        
         return this;   
     } 
} 
myObject.fullName();          // 返回 [object Object] (所有者对象)
```

 函数作为对象方法调用，会使得 **this** 的值成为对象本身。 

##### 3.使用构造函数调用函数

如果函数调用前使用了 **new** 关键字, 则是调用了构造函数。

这看起来就像创建了新的函数，但实际上 JavaScript 函数是重新创建的对象：

```
// 构造函数: function myFunction(arg1, arg2) {    
                 this.firstName = arg1;    
                 this.lastName  = arg2; 
            }  // This    creates a new object 
            var x = new myFunction("John","Doe"); 
            x.firstName;                             // 返回 "John"
```

构造函数的调用会创建一个新的对象。新对象会继承构造函数的属性和方法。

注意：构造函数中 **this** 关键字没有任何的值。 **this** 的值在函数调用实例化对象(new object)时创建。

##### 4.作为函数方法调用函数

在 JavaScript 中, 函数是对象。JavaScript 函数有它的属性和方法。

**call()** 和 **apply()** 是预定义的函数方法。 两个方法可用于调用函数，两个方法的第一个参数必须是对象本身。

```
function myFunction(a, b) {    
    return a * b; 
} 
myObject = myFunction.call(myObject, 10, 2);     // 返回 20
```

```
function myFunction(a, b) {    
    return a * b; 
} 
myArray = [10, 2]; 
myObject = myFunction.apply(myObject, myArray);  // 返回 20
```

两个方法都使用了对象本身作为第一个参数。 两者的区别在于第二个参数： apply传入的是一个参数数组，也就是将多个参数组合成为一个数组传入，而call则作为call的参数传入（从第二个参数开始）。

在 JavaScript 严格模式(strict mode)下, 在调用函数时第一个参数会成为 **this** 的值， 即使该参数不是一个对象。

在 JavaScript 非严格模式(non-strict mode)下, 如果第一个参数的值是 null 或 undefined, 它将使用全局对象替代。

注意：通过 call() 或 apply() 方法你可以设置 **this** 的值, 且作为已存在对象的新方法调用。

#### 自调用函数

函数表达式可以 "自调用"。

自调用表达式会自动调用。

如果表达式后面紧跟 () ，则会自动调用。

不能自调用声明的函数。

通过添加括号，来说明它是一个函数表达式：

```
 (function () {
  var x = "Hello!!";   // 我将调用自己
})(); 
```

### 函数返回

当 JavaScript 到达 return 语句，函数将停止执行。

如果函数被某条语句调用，JavaScript 将在调用语句之后“返回”执行代码。

函数通常会计算出*返回值*。这个返回值会返回给调用者：

计算两个数的乘积，并返回结果：

```
var x = myFunction(7, 8);        // 调用函数，返回值被赋值给 x

function myFunction(a, b) {
    return a * b;                // 函数返回 a 和 b 的乘积
}
```

x 的结果将是：

```
56
```

### 为何使用函数？

您能够对代码进行复用：只要定义一次代码，就可以多次使用它。

您能够多次向同一函数传递不同的参数，以产生不同的结果。

把华氏度转换为摄氏度：

```
function toCelsius(fahrenheit) {
    return (5/9) * (fahrenheit-32);
}

document.getElementById("demo").innerHTML = toCelsius(77);
```

### () 运算符调用函数

使用上面的例子，toCelsius 引用的是函数对象，而 toCelsius() 引用的是函数结果。

访问没有 () 的函数将返回函数定义：

```
function toCelsius(f) {
    return (5/9) * (f-32);
}

document.getElementById("demo").innerHTML = toCelsius;
```

```
 function toCelsius(f) { return (5/9) * (f-32); } //返回结果
```

### 用作变量值的函数

函数的使用方法与变量一致，在所有类型的公式、赋值和计算中。

使用变量来存储函数的值：

```
var x = toCelsius(77);
var text = "The temperature is " + x + " Celsius";
```

能够把函数当做变量值直接使用：

```
var text = "The temperature is " + toCelsius(77) + " Celsius";
```

#### 局部变量

在 JavaScript 函数中声明的变量，会成为函数的*局部变量*。

局部变量只能在函数内访问。

```
// 此处的代码不能使用 carName

function myFunction() {
    var carName = "Volvo";
    // code here CAN use carName
}

// 此处的代码可以使用 carName
```

由于局部变量只能被其函数识别，因此可以在不同函数中使用相同名称的变量。

局部变量在函数开始时创建，在函数完成时被删除

## js遍历

### 遍历数组

#### 1. 普通的for循环

 需要知道数组的长度才能遍历，  最简单的一种，也是使用频率最高的一种，虽然性能不弱，但仍有优化空间 。

```
for(j = 0; j < arr.length; j++) {}
```

#### 2. 优化版的for循环

 使用临时变量，将长度缓存起来，避免重复获取数组长度，当数组较大时优化效果才会比较明显。 

```
for(j = 0,len=arr.length; j < len; j++) { }
```

这种方法基本上是所有循环遍历方法中性能最高的一种，并且这一类型的for循环可以通过用break来中断循环，如下图所示：

　　![img](https://images2018.cnblogs.com/blog/1220270/201805/1220270-20180503141944835-1049496600.gif) 

#### 3. for...of...遍历(这种遍历支持ES6)

```
var arr = [1, 2, 3]
for(var item of arr) { // item代表数组里面的元素
    console.log(item); // 1, 2, 3
};　
```

　这是最简洁、最直接的遍历数组元素的语法，这个方法避开了for-in循环的所有缺陷。与forEach()不同的是，它可以正确响应break、continue和return语句。性能要好于forin，但仍然比不上普通for循环

![img](https://images2018.cnblogs.com/blog/1220270/201805/1220270-20180503150419903-1119578011.gif)

#### 4.forEach()

```
var arr = [1, 2, 3];
arr.forEach((item, index, arr) => { // item为arr的元素，index为下标，arr原数组
    console.log(item); // 1, 2, 3
    console.log(index); // 0, 1, 2
    console.log(arr); // [1, 2, 3]
});
```

　　这种遍历便捷还是挺便捷的，看起来优雅，对目标数组的操作很人性化，要元素给元素，要下标给下标，但是当某种情况你想中断遍历的时候，你就会感觉它就像鸡肋，食之无味，弃之可惜。由于foreach是Array型自带的，对于一些非这种类型的，无法直接使用(如NodeList)，所以才有了这个变种，使用这个变种可以让类似的数组拥有foreach功能。而且forEach的性能也会比普通的for循环弱。又下面的例子我们可以看到，我们常用的return false是可以终止代码继续往下执行的，但是在forEach遍历中，并没有终止循环，所以在用forEach的时候，要考虑使用场景了。

![img](https://images2018.cnblogs.com/blog/1220270/201805/1220270-20180503154807264-21773572.gif)

#### 5.some()

```
var arr = [1, 2, 3];
arr.some((item, index, arr) => { // item为数组中的元素，index为下标，arr为目标数组
    console.log(item); // 1, 2, 3
    console.log(index); // 0, 1, 2
    console.log(arr); // [1, 2, 3]  
})
```

　　some作为一个用来检测数组是否满足一些条件的函数存在，同样是可以用作遍历的函数签名同forEach，有区别的是当任一callback返回值匹配为true则会直接返回true，如果所有的callback匹配均为false，则返回false。

　　some() 方法会依次执行数组的每个元素：

- 如果有一个元素满足条件，则表达式返回*true* , 剩余的元素不会再执行检测。
- 如果没有满足条件的元素，则返回false。

![img](https://images2018.cnblogs.com/blog/1220270/201805/1220270-20180504100325830-364467817.gif)

#### 6.every()

```
var arr = [1, 2, 3];
arr.every((item, index, arr) => { // item为数组中的元素，index为下标，arr为目标数组
    return item > 0; // true
    return index == 0; // false
})
```

　　every() 方法用于检测数组所有元素是否都符合指定条件（通过函数提供）。

　　every() 方法使用指定函数检测数组中的所有元素：

- 如果数组中检测到有一个元素不满足，则整个表达式返回 *false* ，且剩余的元素不会再进行检测。
- 如果所有元素都满足条件，则返回 true。

![img](https://images2018.cnblogs.com/blog/1220270/201805/1220270-20180504102805946-1441146685.gif)

#### 7.filter()

```
var arr = [1, 2, 3];
arr.filter(item => { // item为数组当前的元素
    return item > 1; // [2, 3]
})
```

　　filter() 方法创建一个新的数组，新数组中的元素是通过检查指定数组中符合条件的所有元素。

 **![img](https://images2018.cnblogs.com/blog/1220270/201805/1220270-20180504112126160-1691436399.gif)**

####  8.map()

```
var arr = [1, 2, 3];
arr.map(item => { // item为数组的元素
    console.log(item); // 1, 2, 3
    return item * 2; // 返回一个处理过的新数组[2, 4, 6]
})
```

　　map() 方法返回一个新数组，数组中的元素为原始数组元素调用函数处理后的值。

　　map() 方法按照原始数组元素顺序依次处理元素。

　　这种方式也是用的比较广泛的，虽然用起来比较优雅，但实际效率还比不上foreach

 ![img](https://images2018.cnblogs.com/blog/1220270/201805/1220270-20180504114644070-352776965.gif)

### 遍历对象

**常用方法 in**

　　　　![img](https://images2015.cnblogs.com/blog/893613/201705/893613-20170519135543353-1484646498.png)

in 不仅可以用来 遍历对象，还可以用来遍历数组， 不过 i 对应与数组的 key值

　　　　　![img](https://images2015.cnblogs.com/blog/893613/201705/893613-20170519135623744-1617689944.png)

 **for...in...遍历**

```
var arr = [1, 2, 3]
for(var item in arr) { // item遍历数组时为数组的下标，遍历对象时为对象的key值
    console.log(item); // 0, 1, 2
};
```

　　for...in更多是用来遍历对象，很少用来遍历数组， 不过 item 对应与数组的 key值，建议不要用该方法来遍历数组，因为它的效率是最低的。

![img](https://images2018.cnblogs.com/blog/1220270/201805/1220270-20180504105602779-1290777116.gif)

## js事件

### HTML事件

HTML 事件是发生在 HTML 元素上的“事情”。

当在 HTML 页面中使用 JavaScript 时，JavaScript 能够“应对”这些事件。

HTML 事件可以是浏览器或用户做的某些事情。

下面是 HTML 事件的一些例子：

- HTML 网页完成加载
- HTML 输入字段被修改
- HTML 按钮被点击

通常，当事件发生时，用户会希望做某件事。

JavaScript 允许您在事件被侦测到时执行代码。

*通过 JavaScript 代码*，HTML 允许您向 HTML 元素添加事件处理程序。

使用单引号：

```
<element event='一些 JavaScript'>
```

使用双引号：

```
<element event="一些 JavaScript">
```

在下面的例子中，onclick 属性（以及代码）被添加到 <button> 元素：

```
<button onclick='document.getElementById("demo").innerHTML=Date()'>现在的时间是？</button>
```

[亲自试一试](https://www.w3school.com.cn/tiy/t.asp?f=js_event_onclick)

在上面的例子中，JavaScript 代码改变了 id="demo" 的元素的内容。

在接下来的例子中，代码（使用 this.innerHTML）改变了其自身元素的内容：

```
<button onclick="this.innerHTML=Date()">现在的时间是？</button>
```

[亲自试一试](https://www.w3school.com.cn/tiy/t.asp?f=js_event_onclick_this)

JavaScript 代码通常有很多行。事件属性调用函数更为常见：

```
<button onclick="displayDate()">现在的时间是？</button>
```

[亲自试一试](https://www.w3school.com.cn/tiy/t.asp?f=js_event_onclick_function)

**常见的 HTML 事件**

下面是一些常见的 HTML 事件：

| 事件        | 描述                         |
| :---------- | :--------------------------- |
| onchange    | HTML 元素已被改变            |
| onclick     | 用户点击了 HTML 元素         |
| onmouseover | 用户把鼠标移动到 HTML 元素上 |
| onmouseout  | 用户把鼠标移开 HTML 元素     |
| onkeydown   | 用户按下键盘按键             |
| onload      | 浏览器已经完成页面加载       |

更完整的列表：[W3School JavaScript 参考手册 HTML DOM 事件](https://www.w3school.com.cn/jsref/dom_obj_event.asp)。

### JavaScript 能够做什么？

事件处理程序可用于处理、验证用户输入、用户动作和浏览器动作：

- 每当页面加载时应该做的事情
- 当页面被关闭时应该做的事情
- 当用户点击按钮时应该被执行的动作
- 当用户输入数据时应该被验证的内容
- 等等

让 JavaScript 处理事件的不同方法有很多：

- HTML 事件属性可执行 JavaScript 代码
- HTML 事件属性能够调用 JavaScript 函数
- 您能够向 HTML 元素分配自己的事件处理函数
- 您能够阻止事件被发送或被处理
- 等等

# jQuery

## jQuery选择器

jQuery 选择器允许您对 HTML 元素组或单个元素进行操作。

jQuery 选择器基于元素的 id、类、类型、属性、属性值等"查找"（或选择）HTML 元素。 它基于已经存在的 [CSS 选择器](https://www.runoob.com/cssref/css-selectors.html)，除此之外，它还有一些自定义的选择器。

jQuery 中所有选择器都以美元符号开头：$()。

### 元素选择器

jQuery 元素选择器基于元素名选取元素。

在页面中选取所有 <p> 元素:

$("p")

用户点击按钮后，所有 <p> 元素都隐藏：

```
$(document).ready(function(){  
    $("button").click(function(){    
        $("p").hide();  
    });
});
```

[尝试一下 »](https://www.runoob.com/try/try.php?filename=tryjquery_hide_p)

### #id 选择器

jQuery #id 选择器通过 HTML 元素的 id 属性选取指定的元素。

页面中元素的 id 应该是唯一的，所以您要在页面中选取唯一的元素需要通过 #id 选择器。

通过 id 选取元素语法如下：

$("#test")

当用户点击按钮后，有 id="test" 属性的元素将被隐藏：

```
$(document).ready(function(){  
    $("button").click(function(){    
        $("#test").hide();  
    }); 
});
```

[尝试一下 »](https://www.runoob.com/try/try.php?filename=tryjquery_hide_id)

### .class 选择器

jQuery 类选择器可以通过指定的 class 查找元素。

语法如下：

$(".test")

用户点击按钮后所有带有 class="test" 属性的元素都隐藏：

```
$(document).ready(function(){  
      $("button").click(function(){    
           $(".test").hide();  
      }); 
});
```


[尝试一下 »](https://www.runoob.com/try/try.php?filename=tryjquery_hide_class)

### 更多实例

| 语法                     | 描述                                                    | 实例                                                         |
| :----------------------- | :------------------------------------------------------ | :----------------------------------------------------------- |
| $("*")                   | 选取所有元素                                            | [在线实例](https://www.runoob.com/try/try.php?filename=tryjquery_sel_all2) |
| $(this)                  | 选取当前 HTML 元素                                      | [在线实例](https://www.runoob.com/try/try.php?filename=tryjquery_sel_this) |
| $("p.intro")             | 选取 class 为 intro 的 <p> 元素                         | [在线实例](https://www.runoob.com/try/try.php?filename=tryjquery_sel_pclass) |
| $("p:first")             | 选取第一个 <p> 元素                                     | [在线实例](https://www.runoob.com/try/try.php?filename=tryjquery_sel_pfirst) |
| $("ul li:first")         | 选取第一个 <ul> 元素的第一个 <li> 元素                  | [在线实例](https://www.runoob.com/try/try.php?filename=tryjquery_sel_ullifirst) |
| $("ul li:first-child")   | 选取每个 <ul> 元素的第一个 <li> 元素                    | [在线实例](https://www.runoob.com/try/try.php?filename=tryjquery_sel_ullifirstchild) |
| $("[href]")              | 选取带有 href 属性的元素                                | [在线实例](https://www.runoob.com/try/try.php?filename=tryjquery_sel_hrefattr) |
| $("a[target='_blank']")  | 选取所有 target 属性值等于 "_blank" 的 <a> 元素         | [在线实例](https://www.runoob.com/try/try.php?filename=tryjquery_sel_hrefattrblank) |
| $("a[target!='_blank']") | 选取所有 target 属性值不等于 "_blank" 的 <a> 元素       | [在线实例](https://www.runoob.com/try/try.php?filename=tryjquery_sel_hrefattrnotblank) |
| $(":button")             | 选取所有 type="button" 的 <input> 元素 和 <button> 元素 | [在线实例](https://www.runoob.com/try/try.php?filename=tryjquery_sel_button2) |
| $("tr:even")             | 选取偶数位置的 <tr> 元素                                | [在线实例](https://www.runoob.com/try/try.php?filename=tryjquery_sel_even) |
| $("tr:odd")              | 选取奇数位置的 <tr> 元素                                | [在线实例](https://www.runoob.com/try/try.php?filename=tryjquery_sel_odd) |

## jQuery遍历

### jQuery遍历

#### 什么是遍历？

jQuery 遍历，意为"移动"，用于根据其相对于其他元素的关系来"查找"（或选取）HTML 元素。以某项选择开始，并沿着这个选择移动，直到抵达您期望的元素为止。

下图展示了一个家族树。通过 jQuery 遍历，您能够从被选（当前的）元素开始，轻松地在家族树中向上移动（祖先），向下移动（子孙），水平移动（同胞）。这种移动被称为对 DOM 进行遍历。

![jQuery Dimensions](https://www.runoob.com/images/img_travtree.png)

图示解析：

- <div> 元素是 <ul> 的父元素，同时是其中所有内容的祖先。
- <ul> 元素是 <li> 元素的父元素，同时是 <div> 的子元素
- 左边的 <li> 元素是 <span> 的父元素，<ul> 的子元素，同时是 <div> 的后代。
- <span> 元素是 <li> 的子元素，同时是 <ul> 和 <div> 的后代。
- 两个 <li> 元素是同胞（拥有相同的父元素）。
- 右边的 <li> 元素是 <b> 的父元素，<ul> 的子元素，同时是 <div> 的后代。
- <b> 元素是右边的 <li> 的子元素，同时是 <ul> 和 <div> 的后代。

注意：祖先是父、祖父、曾祖父等等。后代是子、孙、曾孙等等。同胞拥有相同的父。

#### 遍历 DOM

jQuery 提供了多种遍历 DOM 的方法。

遍历方法中最大的种类是树遍历（tree-traversal）。

### jQuery 遍历 - 祖先

祖先是父、祖父或曾祖父等等。

通过 jQuery，您能够向上遍历 DOM 树，以查找元素的祖先。

#### 向上遍历 DOM 树

这些 jQuery 方法很有用，它们用于向上遍历 DOM 树：

- parent()
- parents()
- parentsUntil()

##### jQuery parent() 方法

parent() 方法返回被选元素的直接父元素。

该方法只会向上一级对 DOM 树进行遍历。

下面的例子返回每个 <span> 元素的直接父元素：

```
$(document).ready(function(){  
      $("span").parent(); 
});
```


[尝试一下 »](https://www.runoob.com/try/try.php?filename=tryjquery_parent)

##### jQuery parents() 方法

parents() 方法返回被选元素的所有祖先元素，它一路向上直到文档的根元素 (<html>)。

下面的例子返回所有 <span> 元素的所有祖先：

```
$(document).ready(function(){  
      $("span").parents(); 
});
```


[尝试一下 »](https://www.runoob.com/try/try.php?filename=tryjquery_parents)

您也可以使用可选参数来过滤对祖先元素的搜索。

下面的例子返回所有 <span> 元素的所有祖先，并且它是 <ul> 元素：

```
$(document).ready(function(){  
     $("span").parents("ul"); 
});
```


[尝试一下 »](https://www.runoob.com/try/try.php?filename=tryjquery_parents2)

##### jQuery parentsUntil() 方法

parentsUntil() 方法返回介于两个给定元素之间的所有祖先元素。

下面的例子返回介于 <span> 与 <div> 元素之间的所有祖先元素：

```
$(document).ready(function(){  
      $("span").parentsUntil("div"); 
});
```

[尝试一下 »](https://www.runoob.com/try/try.php?filename=tryjquery_parentsuntil)

### jQuery 遍历 - 后代

后代是子、孙、曾孙等等。

通过 jQuery，您能够向下遍历 DOM 树，以查找元素的后代。

#### 向下遍历 DOM 树

下面是两个用于向下遍历 DOM 树的 jQuery 方法：

- children()
- find()

##### jQuery children() 方法

children() 方法返回被选元素的所有直接子元素。

该方法只会向下一级对 DOM 树进行遍历。

下面的例子返回每个 <div> 元素的所有直接子元素：

```
$(document).ready(function(){ 
       $("div").children(); 
});
```

[尝试一下 »](https://www.runoob.com/try/try.php?filename=tryjquery_children)

您也可以使用可选参数来过滤对子元素的搜索。

下面的例子返回类名为 "1" 的所有 <p> 元素，并且它们是 <div> 的直接子元素：

```
$(document).ready(function(){  
     $("div").children("p.1");
});
```

[尝试一下 »](https://www.runoob.com/try/try.php?filename=tryjquery_children2)

##### jQuery find() 方法

find() 方法返回被选元素的后代元素，一路向下直到最后一个后代。

下面的例子返回属于 <div> 后代的所有 <span> 元素：

```
$(document).ready(function(){  
     $("div").find("span"); 
});
```

[尝试一下 »](https://www.runoob.com/try/try.php?filename=tryjquery_find)

下面的例子返回 <div> 的所有后代：

```
$(document).ready(function(){  
    $("div").find("*"); 
});
```

[尝试一下 »](https://www.runoob.com/try/try.php?filename=tryjquery_find2)

### jQuery 遍历 - 同胞(siblings)

同胞拥有相同的父元素。

通过 jQuery，您能够在 DOM 树中遍历元素的同胞元素。

#### 在 DOM 树中水平遍历

有许多有用的方法让我们在 DOM 树进行水平遍历：

- siblings()
- next()
- nextAll()
- nextUntil()
- prev()
- prevAll()
- prevUntil()

##### jQuery siblings() 方法

siblings() 方法返回被选元素的所有同胞元素。

下面的例子返回 <h2> 的所有同胞元素：

```
$(document).ready(function(){  
    $("h2").siblings(); 
});
```

[尝试一下 »](https://www.runoob.com/try/try.php?filename=tryjquery_siblings)

您也可以使用可选参数来过滤对同胞元素的搜索。

下面的例子返回属于 <h2> 的同胞元素的所有 <p> 元素：

```
$(document).ready(function(){  
       $("h2").siblings("p"); 
});
```

[尝试一下 »](https://www.runoob.com/try/try.php?filename=tryjquery_siblings2)

##### jQuery next() 方法

next() 方法返回被选元素的下一个同胞元素。

该方法只返回一个元素。

下面的例子返回 <h2> 的下一个同胞元素：

```
$(document).ready(function(){  
      $("h2").next(); 
});
```

[尝试一下 »](https://www.runoob.com/try/try.php?filename=tryjquery_next)

##### jQuery nextAll() 方法

nextAll() 方法返回被选元素的所有跟随的同胞元素。

下面的例子返回 <h2> 的所有跟随的同胞元素：

```
$(document).ready(function(){  
       $("h2").nextAll(); 
});
```

[尝试一下 »](https://www.runoob.com/try/try.php?filename=tryjquery_nextall)

##### jQuery nextUntil() 方法

nextUntil() 方法返回介于两个给定参数之间的所有跟随的同胞元素。

下面的例子返回介于 <h2> 与 <h6> 元素之间的所有同胞元素：

```
$(document).ready(function(){  
      $("h2").nextUntil("h6"); 
});
```

[尝试一下 »](https://www.runoob.com/try/try.php?filename=tryjquery_nextuntil)

##### jQuery prev(), prevAll() & prevUntil() 方法

prev(), prevAll() 以及 prevUntil() 方法的工作方式与上面的方法类似，只不过方向相反而已：它们返回的是前面的同胞元素（在 DOM 树中沿着同胞之前元素遍历，而不是之后元素遍历）。

### jQuery 遍历- 过滤

#### 缩小搜索元素的范围

三个最基本的过滤方法是：first(), last() 和 eq()，它们允许您基于其在一组元素中的位置来选择一个特定的元素。

其他过滤方法，比如 filter() 和 not() 允许您选取匹配或不匹配某项指定标准的元素。

##### jQuery first() 方法

first() 方法返回被选元素的首个元素。

下面的例子选取首个 <div> 元素内部的第一个 <p> 元素：

```
$(document).ready(function(){  
     $("div p").first();
});
```


[尝试一下 »](https://www.runoob.com/try/try.php?filename=tryjquery_first)

##### jQuery last() 方法

last() 方法返回被选元素的最后一个元素。

下面的例子选择最后一个 <div> 元素中的最后一个 <p> 元素：

```
$(document).ready(function(){  
     $("div p").last();  
});
```

[尝试一下 »](https://www.runoob.com/try/try.php?filename=tryjquery_last)

##### jQuery eq() 方法

eq() 方法返回被选元素中带有指定索引号的元素。

索引号从 0 开始，因此首个元素的索引号是 0 而不是 1。下面的例子选取第二个 <p> 元素（索引号 1）：

```
$(document).ready(function(){  
     $("p").eq(1);
});
```

[尝试一下 »](https://www.runoob.com/try/try.php?filename=tryjquery_eq)

##### jQuery filter() 方法

filter() 方法允许您规定一个标准。不匹配这个标准的元素会被从集合中删除，匹配的元素会被返回。

下面的例子返回带有类名 "url" 的所有 <p> 元素：

```
$(document).ready(function(){  
     $("p").filter(".url"); 
 });
```


[尝试一下 »](https://www.runoob.com/try/try.php?filename=tryjquery_filter)

##### jQuery not() 方法

not() 方法返回不匹配标准的所有元素。

提示：not() 方法与 filter() 相反。

下面的例子返回不带有类名 "url" 的所有 <p> 元素：

```
$(document).ready(function(){  
   $("p").not(".url"); 
});
```

[尝试一下 »](https://www.runoob.com/try/try.php?filename=tryjquery_not)

## HTML操作

### html([val|fn])

#### 1.概述

取得第一个匹配元素的html内容。这个函数不能用于XML文档。但可以用于XHTML文档。

在一个 HTML 文档中, 我们可以使用 .html() 方法来获取任意一个元素的内容。 如果选择器匹配多于一个的元素，那么只有第一个匹配元素的 HTML 内容会被获取。

#### 2.参数

（1）val ：  String     V1.0      用于设定HTML内容的值

（2）function(index, html) :    Function   V1.4      此函数返回一个HTML字符串。接受两个参数，index为元素在集合中的索引位置，html为原先的HTML值。

**示例**：

##### **无参数 描述:**

返回p元素的内容。

**jQuery 代码:**

```
$('p').html();
```

##### **参数val 描述:**

设置所有 p 元素的内容

**jQuery 代码:**

```
$("p").html("Hello <b>world</b>!");
```

##### **回调函数描述:**

使用函数来设置所有匹配元素的内容。

**jQuery 代码:**

```
$("p").html(function(n){
    return "这个 p 元素的 index 是：" + n;
    });
```

### text([val|fn])

#### 1.概述

取得所有匹配元素的内容。

结果是由所有匹配元素包含的文本内容组合起来的文本。这个方法对HTML和XML文档都有效。

#### 2.参数

**（1）val**：   String        *V1.0*      用于设置元素内容的文本

**（2）function(index, text)**：   Function*V1.4*       此函数返回一个字符串。接受两个参数，index为元素在集合中的索引位置，text为原先的text值。

**示例**

##### **无参数 描述:**

返回p元素的文本内容。

**jQuery 代码:**

```
$('p').text();
```

##### **参数val 描述:**

设置所有 p 元素的文本内容

**jQuery 代码:**

```
$("p").text("Hello world!");
```

##### **回调函数 描述:**

使用函数来设置所有匹配元素的文本内容。

**jQuery 代码:**

```
$("p").text(function(n){
    return "这个 p 元素的 index 是：" + n;
    });
```

### val([val|fn|arr])

#### 1.概述

获得匹配元素的当前值。

在 jQuery 1.2 中,可以返回任意元素的值了。包括select。如果多选，将返回一个数组，其包含所选的值。

#### 2.参数

**（1）val**：  String   *V1.0*    要设置的值。

**（2）function(index, value)**：   Function    *V1.4*      此函数返回一个要设置的值。接受两个参数，index为元素在集合中的索引位置，text为原先的text值。

**（3）array**：Array     <String>    *V1.0*       用于 check/select 的值

**示例**

##### 无参数 描述:

获取文本框中的值

**jQuery 代码:**

```
$("input").val();
```

##### 参数val 描述:

设定文本框的值

**jQuery 代码:**

```
$("input").val("hello world!");
```

##### 回调函数 描述:

设定文本框的值

**jQuery 代码:**

```
$('input:text.items').val(function() {
  return this.value + ' ' + this.className;
});
```

##### 参数array 描述:

设定一个select和一个多选的select的值

**HTML 代码:**

```
<select id="single">
  <option>Single</option>
  <option>Single2</option>
</select>
<select id="multiple" multiple="multiple">
  <option selected="selected">Multiple</option>
  <option>Multiple2</option>
  <option selected="selected">Multiple3</option>
</select><br/>
<input type="checkbox" value="check1"/> check1
<input type="checkbox" value="check2"/> check2
<input type="radio" value="radio1"/> radio1
<input type="radio" value="radio2"/> radio2
```

**jQuery 代码:**

```
$("#single").val("Single2");
$("#multiple").val(["Multiple2", "Multiple3"]);
$("input").val(["check2", "radio1"]);
```

### 更多

下面的表格列出了所有用于处理 HTML 和 CSS 的 jQuery 方法。

下面的方法适用于 HTML 和 XML 文档。除了：html() 方法。

| 方法                                                         | 描述                                              |
| :----------------------------------------------------------- | :------------------------------------------------ |
| [addClass()](https://www.runoob.com/jquery/html-addclass.html) | 向被选元素添加一个或多个类名                      |
| [after()](https://www.runoob.com/jquery/html-after.html)     | 在被选元素后插入内容                              |
| [append()](https://www.runoob.com/jquery/html-append.html)   | 在被选元素的结尾插入内容                          |
| [appendTo()](https://www.runoob.com/jquery/html-appendto.html) | 在被选元素的结尾插入 HTML 元素                    |
| [attr()](https://www.runoob.com/jquery/html-attr.html)       | 设置或返回被选元素的属性/值                       |
| [before()](https://www.runoob.com/jquery/html-before.html)   | 在被选元素前插入内容                              |
| [clone()](https://www.runoob.com/jquery/html-clone.html)     | 生成被选元素的副本                                |
| [css()](https://www.runoob.com/jquery/css-css.html)          | 为被选元素设置或返回一个或多个样式属性            |
| [detach()](https://www.runoob.com/jquery/html-detach.html)   | 移除被选元素（保留数据和事件）                    |
| [empty()](https://www.runoob.com/jquery/html-empty.html)     | 从被选元素移除所有子节点和内容                    |
| [hasClass()](https://www.runoob.com/jquery/html-hasclass.html) | 检查被选元素是否包含指定的 class 名称             |
| [height()](https://www.runoob.com/jquery/css-height.html)    | 设置或返回被选元素的高度                          |
| [html()](https://www.runoob.com/jquery/html-html.html)       | 设置或返回被选元素的内容                          |
| [innerHeight()](https://www.runoob.com/jquery/html-innerheight.html) | 返回元素的高度（包含 padding，不包含 border）     |
| [innerWidth()](https://www.runoob.com/jquery/html-innerwidth.html) | 返回元素的宽度（包含 padding，不包含 border）     |
| [insertAfter()](https://www.runoob.com/jquery/html-insertafter.html) | 在被选元素后插入 HTML 元素                        |
| [insertBefore()](https://www.runoob.com/jquery/html-insertbefore.html) | 在被选元素前插入 HTML 元素                        |
| [offset()](https://www.runoob.com/jquery/css-offset.html)    | 设置或返回被选元素的偏移坐标（相对于文档）        |
| [offsetParent()](https://www.runoob.com/jquery/css-offsetparent.html) | 返回第一个定位的祖先元素                          |
| [outerHeight()](https://www.runoob.com/jquery/html-outerheight.html) | 返回元素的高度（包含 padding 和 border）          |
| [outerWidth()](https://www.runoob.com/jquery/html-outerwidth.html) | 返回元素的宽度（包含 padding 和 border）          |
| [position()](https://www.runoob.com/jquery/css-position.html) | 返回元素的位置（相对于父元素）                    |
| [prepend()](https://www.runoob.com/jquery/html-prepend.html) | 在被选元素的开头插入内容                          |
| [prependTo()](https://www.runoob.com/jquery/html-prependto.html) | 在被选元素的开头插入 HTML 元素                    |
| [prop()](https://www.runoob.com/jquery/html-prop.html)       | 设置或返回被选元素的属性/值                       |
| [remove()](https://www.runoob.com/jquery/html-remove.html)   | 移除被选元素（包含数据和事件）                    |
| [removeAttr()](https://www.runoob.com/jquery/html-removeattr.html) | 从被选元素移除一个或多个属性                      |
| [removeClass()](https://www.runoob.com/jquery/html-removeclass.html) | 从被选元素移除一个或多个类                        |
| [removeProp()](https://www.runoob.com/jquery/html-removeprop.html) | 移除通过 prop() 方法设置的属性                    |
| [replaceAll()](https://www.runoob.com/jquery/html-replaceall.html) | 把被选元素替换为新的 HTML 元素                    |
| [replaceWith()](https://www.runoob.com/jquery/html-replacewith.html) | 把被选元素替换为新的内容                          |
| [scrollLeft()](https://www.runoob.com/jquery/css-scrollleft.html) | 设置或返回被选元素的水平滚动条位置                |
| [scrollTop()](https://www.runoob.com/jquery/css-scrolltop.html) | 设置或返回被选元素的垂直滚动条位置                |
| [text()](https://www.runoob.com/jquery/html-text.html)       | 设置或返回被选元素的文本内容                      |
| [toggleClass()](https://www.runoob.com/jquery/html-toggleclass.html) | 在被选元素中添加/移除一个或多个类之间切换         |
| [unwrap()](https://www.runoob.com/jquery/html-unwrap.html)   | 移除被选元素的父元素                              |
| [val()](https://www.runoob.com/jquery/html-val.html)         | 设置或返回被选元素的属性值（针对表单元素）        |
| [width()](https://www.runoob.com/jquery/css-width.html)      | 设置或返回被选元素的宽度                          |
| [wrap()](https://www.runoob.com/jquery/html-wrap.html)       | 在每个被选元素的周围用 HTML 元素包裹起来          |
| [wrapAll()](https://www.runoob.com/jquery/html-wrapall.html) | 在所有被选元素的周围用 HTML 元素包裹起来          |
| [wrapInner()](https://www.runoob.com/jquery/html-wrapinner.html) | 在每个被选元素的内容周围用 HTML 元素包裹起来      |
| [$.escapeSelector()](https://www.runoob.com/jquery/html-escapeSelector.html) | 转义CSS选择器中有特殊意义的字符或字符串           |
| [$.cssHooks](https://www.runoob.com/jquery/html-csshooks.html) | 提供了一种方法通过定义函数来获取和设置特定的CSS值 |
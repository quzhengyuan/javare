1. Number()可以把任意值转换成数值，如果要转换的字符串中有一个不是数值的字符，返回 NaN（not a number）。比如在控制台中依次输入以下代码：

```javascript
var num1 = Number(true); 
num1; // true 返回 1，false 返回 0

var num2 = Number(undefined);
num2;  // 返回 NaN

var num3 = Number(null);
num3; //返回 0

var num4 = Number("syl");
num4;  // 返回 NaN

var num5 = Number("   ");
num5; // 如果是空字符串返回 0

var num6 = Number(123);
num6; // 返回123，如果是数字型的字符，返回数字

var num7 = Number("123abc");
num7;  // 返回 NaN
```

1. parseInt() 把字符串转换成整数。比如在控制台中依次输入以下代码：

```javascript
var num1 = parseInt("12.3abc");  
num1; //返回 12，如果第一个字符是数字会解析知道遇到非数字结束,只取整，不是约等于

var num2 = parseInt("abc123");  
num2; //返回 NaN，如果第一个字符不是数字或者符号就返回 NaN

var num3 = parseInt(""); 
num3;       // 空字符串返回 NaN，但是 Number("")返回 0

var num4 = parseInt("520");
num4;      //返回 520

var num5 = parseInt("0xA"); 
num5;  //返回 10
```

另外值得注意的是，parseInt()可以传递两个参数，第一个参数是要转换的字符串，第二个参数是要转换的进制。大家可以自行尝试一下。

1. parseFloat()把字符串转换成浮点数。写法和parseInt()相似，主要有以下几个不同点：

- parseFloat不支持第二个参数，只能解析 10 进制数
- 如果解析的内容里只有整数，解析成整数

例子：

```javascript
parseFloat("10"); // returns 10
parseFloat("10.000"); // returns 10
parseFloat("10.01"); // returns 10.01
parseFloat(" 10 "); // returns 10
parseFloat("10 hours"); // returns 10
parseFloat("aaa 10 "); // returns NaN
```

1. 执行减 0 操作。比如：

```javascript
var n="10";
var m=n-0;
m; // returns 10
```

值得注意的是，如果该字符串不是纯粹的数字字符串，那么它执行减 0 操作后，虽然变成了一个数字类型，但是返回值为 NaN。比如：

```javascript
var n = "abc";
var m = n - 0;
m; // returns NaN
typeof(m); // returns "number"
```
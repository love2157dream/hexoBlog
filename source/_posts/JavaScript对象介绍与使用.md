---
title: JavaScript对象介绍与使用
tags: JavaScript对象
categories: JavaScript
date: 2017-12-06 10:42:03
---
 
# Math 对象

## Math对象属性

> - `Math.E` 返回算术常量 e，即自然对数的底数（约等于2.718）。
  
```javascript
console.log(Math.E); // 2.718281828459045
```

> - `Math.LN2` 返回 2 的自然对数（约等于0.693）。

```javascript
console.log(Math.LN2); // 0.6931471805599453
```

> - `Math.LN10` 返回 10 的自然对数（约等于2.302）。

```javascript
console.log(Math.LN10); // 2.302585092994046
```

> - `Math.LOG2E` 返回以 2 为底的 e 的对数（约等于 1.414）。

```javascript
console.log(Math.LOG2E); // 1.4426950408889634
```

> - `Math.LOG10E` 返回以 10 为底的 e 的对数（约等于0.434）。

```javascript
console.log(Math.LOG10E); // 0.4342944819032518
```

> - `Math.PI` 返回圆周率（约等于3.14159）。

```javascript
console.log(Math.PI); // 3.141592653589793
```

> - `Math.SQRT1_2` 返回返回 2 的平方根的倒数（约等于 0.707）。

```javascript
console.log(Math.SQRT1_2); // 0.7071067811865476
```

> - `Math.SQRT2` 返回 2 的平方根（约等于 1.414）。

```javascript
console.log(Math.SQRT2); // 1.4142135623730951
```

## Math对象方法

> - `Math.abs(x)` 方法返回一个数的绝对值，x必须是一个数值。如果x不是数字返回NaN，如果x为null返回0

```javascript
console.log(Math.abs(-7.25));  // 7.25
console.log(Math.abs('a')); // NaN
console.log(Math.abs({})); // NaN
console.log(Math.abs(undefined)); // NaN
console.log(Math.abs(null)); // 0
console.log(Math.abs([])); // 0
```

> - `Math.acos(x)` 方法返回x的反余弦值，返回的值是0到PI之间的弧度值。如果x的值超过-1.0~1.0的范围，返回NaN。如果x值为-1，返回PI。

```javascript
console.log(Math.acos(0.5)); // 1.0471975511965979
console.log(Math.acos(-1.02)); // NaN
console.log(Math.acos(1.02)); // NaN
console.log(Math.acos(-1)); // 3.141592653589793
console.log(Math.acos({})); // NaN
console.log(Math.acos(undefined)); // NaN
console.log(Math.acos(null)); // 1.5707963267948966
console.log(Math.acos([])); // 1.5707963267948966
```

> - `Math.acosh(x)` 返回x的反双曲余弦。 **<font color=red>ES6支持</font>**

```javascript
console.log(Math.acosh(0.5)); // NaN
console.log(Math.acosh(-1.02)); // NaN
console.log(Math.acosh(1.02)); // 0.1996681577984152
console.log(Math.acosh(-1)); // NaN
console.log(Math.acosh({})); // NaN
console.log(Math.acosh(undefined)); // NaN
console.log(Math.acosh(null)); // NaN
console.log(Math.acosh([])); // NaN
```

> - `Math.asin(x)` 方法返回一个数的反正弦值，返回的值是-P1/2~PI/2之间的弧度值。如果x超过了-1.0~1.0的范围，返回NaN。如果x值为1，返回PI/2。

```javascript
console.log(Math.asin(0.5)); // 0.5235987755982989
console.log(Math.asin(-1.02)); // NaN
console.log(Math.asin(1.02)); // NaN
console.log(Math.asin(1)); // 1.5707963267948966
console.log(Math.asin({})); // NaN
console.log(Math.asin(undefined)); // NaN
console.log(Math.asin(null)); // 0
console.log(Math.asin([])); // 0
```

> - `Math.asinh(x)` 返回x的反双曲正弦。 **<font color=red>ES6支持</font>**

```javascript
console.log(Math.asinh(0.5)); // 0.48121182505960347
console.log(Math.asinh(-1.02)); // -0.8954452493897191
console.log(Math.asinh(1.02)); // 0.8954452493897191
console.log(Math.asinh(-1)); // -0.881373587019543
console.log(Math.asinh({})); // NaN
console.log(Math.asinh(undefined)); // NaN
console.log(Math.asinh(null)); // 0
console.log(Math.asinh([])); // 0
```

> - `Math.atan(x)`  方法以介于 -PI/2 与 PI/2 弧度之间的数值来返回 x 的反正切值。x必须是数值

```javascript
console.log(Math.atan(0.5)); // 0.4636476090008061
console.log(Math.atan({})); // NaN
console.log(Math.atan(undefined)); // NaN
console.log(Math.atan(null)); // 0
console.log(Math.atan([])); // 0
```

> - `Math.atan2(y, x)` 返回从 x 轴到点 (x,y) 的角度（介于 -PI/2 与 PI/2 弧度之间）。

```javascript
指定一个坐标（x，y），坐标值（4,8），使用 atan2() 方法计算坐标与X轴之间的角度的弧度 ，如下实例：
console.log(Math.atan2(8,4));  // 1.1071487177940904
```

> - `Math.atanh(x)` 返回x的反双曲正切。 **<font color=red>ES6支持</font>**

```javascript
console.log(Math.atanh(0.5)); // 0.5493061443340548
console.log(Math.atanh(-1.02)); // NaN
console.log(Math.atanh(1.02)); // NaN
console.log(Math.atanh(1)); // Infinity
console.log(Math.atanh(-1)); // -Infinity
console.log(Math.atanh({})); // NaN
console.log(Math.atanh(undefined)); // NaN
console.log(Math.atanh(null)); // 0
console.log(Math.atanh([])); // 0
```

> - `Math.cbrt(x)` 方法用于计算一个数的立方根。 **<font color=red>ES6支持</font>**

```javascript
console.log(Math.cbrt(-1)); // -1
console.log(Math.cbrt(0));  // 0
console.log(Math.cbrt(1));  // 1
console.log(Math.cbrt(2));  // 1.2599210498948734

// 对于非数值，Math.cbrt方法内部也是先使用Number方法将其转为数值。

console.log(Math.cbrt('8')); // 2
console.log(Math.cbrt('hello')); // NaN
console.log(Math.cbrt([])); // 0
console.log(Math.cbrt({})); // NaN
console.log(Math.cbrt(null)); // 0
console.log(Math.cbrt(undefined)); // NaN
// 对于没有部署这个方法的环境，可以用下面的代码模拟。

Math.cbrt = Math.cbrt || function(x) {
  var y = Math.pow(Math.abs(x), 1/3);
  return x < 0 ? -y : y;
};
```

> - `Math.ceil(x)` 方法执行的是向上取整计算，它返回的是大于或等于函数参数，并且与之最接近的整数。
。如果参数是一个整数，该值不变。

```javascript
console.log(Math.ceil(1.4)); // 2
console.log(Math.ceil(-1.4)); // -1
console.log(Math.ceil(1.245)); // 2
console.log(Math.ceil(-1.245)); // -1
console.log(Math.ceil(0.84)); // 1
console.log(Math.ceil({})); // NaN
console.log(Math.ceil(undefined)); // NaN
console.log(Math.ceil(null)); // 0
console.log(Math.ceil([])); // 0
```

> - `Math.clz32(x)`  方法返回一个数的 32 位无符号整数形式有多少个前导 0。 **<font color=red>ES6支持</font>**

```javascript
console.log(Math.clz32(0)); // 32
console.log(Math.clz32(1)); // 31
console.log(Math.clz32(1000)); // 22
console.log(Math.clz32(0b01000000000000000000000000000000)); // 1
console.log(Math.clz32(0b00100000000000000000000000000000)); // 2
// 上面代码中，0 的二进制形式全为 0，所以有 32 个前导 0；
// 1 的二进制形式是0b1，只占 1 位，所以 32 位之中有 31 个前导 0；
// 1000 的二进制形式是0b1111101000，一共有 10 位，所以 32 位之中有 22 个前导 0。
// clz32这个函数名就来自”count leading zero bits in 32-bit binary representation of a number“
// （计算一个数的 32 位二进制形式的前导 0 的个数）的缩写。

//左移运算符（<<）与Math.clz32方法直接相关。
console.log(Math.clz32(0)); // 32
console.log(Math.clz32(1)); // 31
console.log(Math.clz32(1 << 1)); // 30
console.log(Math.clz32(1 << 2)); // 29
console.log(Math.clz32(1 << 29)); // 2

// 对于小数，Math.clz32方法只考虑整数部分。
console.log(Math.clz32(3.2)); // 30
console.log(Math.clz32(3.9)); // 30

// 对于空值或其他类型的值，Math.clz32方法会将它们先转为数值，然后再计算。
console.log(Math.clz32()); // 32
console.log(Math.clz32(NaN)); // 32
console.log(Math.clz32(Infinity)); // 32
console.log(Math.clz32(null)); // 32
console.log(Math.clz32('foo')); // 32
console.log(Math.clz32([])); // 32
console.log(Math.clz32({})); // 32
console.log(Math.clz32(true)); // 31
```

> - `Math.cos(x)` 方法可返回一个数字的余弦值。 返回的是 -1.0 到 1.0 之间的数。

```javascript
console.log(Math.cos(3)); // -0.9899924966004454
console.log(Math.cos({})); // NaN
console.log(Math.cos(undefined)); // NaN
console.log(Math.cos(null)); // 1
console.log(Math.cos([])); // 1
```

> - `Math.cosh(x)` 返回x的双曲余弦。 **<font color=red>ES6支持</font>**

```javascript
console.log(Math.cosh(0.5)); // 1.1276259652063807
console.log(Math.cosh(-1.02)); // 1.5668948520686883
console.log(Math.cosh(1.02)); // 1.5668948520686883
console.log(Math.cosh(1)); // 1.5430806348152437
console.log(Math.cosh(-1)); // 1.5430806348152437
console.log(Math.cosh({})); // NaN
console.log(Math.cosh(undefined)); // NaN
console.log(Math.cosh(null)); // 1
console.log(Math.cosh([])); // 1
```

> - `Math.exp(x)` 方法可返回 e 的 x 次幂的值。 E 为自然底数 (近似值 2.7183)。

```javascript
console.log(Math.exp(1)); // 2.718281828459045
console.log(Math.exp({})); // NaN
console.log(Math.exp(undefined)); // NaN
console.log(Math.exp(null)); // 1
console.log(Math.exp([])); // 1
```

> - `Math.expm1(x)` 返回 ex - 1，即Math.exp(x) - 1。 **<font color=red>ES6支持</font>**

```javascript
console.log(Math.expm1(-1)); // -0.6321205588285577
console.log(Math.expm1(0));  // 0
console.log(Math.expm1(1));  // 1.718281828459045

//对于没有部署这个方法的环境，可以用下面的代码模拟。
Math.expm1 = Math.expm1 || function(x) {
  return Math.exp(x) - 1;
};
```

> - `Math.floor(x)` 方法返回小于等于x的最大整数。如果传递的参数是一个整数，该值不变。

```javascript
console.log(Math.floor(1.4)); // 1
console.log(Math.floor(-1.4)); // -2
console.log(Math.floor(1.245)); // 1
console.log(Math.floor(-1.245)); // -2
console.log(Math.floor(0.84)); // 0
console.log(Math.floor({})); // NaN
console.log(Math.floor(undefined)); // NaN
console.log(Math.floor(null)); // 0
console.log(Math.floor([])); // 0
```

> - `Math.fround(x)` 方法返回一个数的单精度浮点数形式。 **<font color=red>ES6支持</font>**

```javascript
console.log(Math.fround(0));     // 0
console.log(Math.fround(1));     // 1
console.log(Math.fround(1.337)); // 1.3370000123977661
console.log(Math.fround(1.5));   // 1.5
console.log(Math.fround(NaN));   // NaN
console.log(Math.fround({})); // NaN
console.log(Math.fround(undefined)); // NaN
console.log(Math.fround(null)); // 0
console.log(Math.fround([])); // 0
//对于整数来说，Math.fround方法返回结果不会有任何不同，区别主要是那些无法用 64 个二进制位精确表示的小数。
//这时，Math.fround方法会返回最接近这个小数的单精度浮点数。

//对于没有部署这个方法的环境，可以用下面的代码模拟。
Math.fround = Math.fround || function(x) {
  return new Float32Array([x])[0];
};
```

> - `Math.hypot(x)` 方法返回所有参数x的平方和的平方根。**<font color=red>ES6支持</font>**

```javascript
Math.hypot(3, 4);        // 5
Math.hypot(3, 4, 5);     // 7.0710678118654755
Math.hypot();            // 0
Math.hypot(NaN);         // NaN
Math.hypot(3, 4, 'foo'); // NaN
Math.hypot(3, 4, '5');   // 7.0710678118654755
Math.hypot(-3);          // 3
//上面代码中，3 的平方加上 4 的平方，等于 5 的平方。

// 如果参数不是数值，Math.hypot方法会将其转为数值。只要有一个参数无法转为数值，就会返回 NaN。
```

> - `Math.imul(x, y)` 方法返回两个数以 32 位带符号整数形式相乘的结果，返回的也是一个 32 位的带符号整数。 **<font color=red>ES6支持</font>**

```javascript
console.log(Math.imul(2, 4));   // 8
console.log(Math.imul(-1, 8));  // -8
console.log(Math.imul(-2, -2)); // 4
// 如果只考虑最后 32 位，大多数情况下，Math.imul(a, b)与a * b的结果是相同的，
// 即该方法等同于(a * b)|0的效果（超过 32 位的部分溢出）。
// 之所以需要部署这个方法，是因为 JavaScript 有精度限制，超过 2 的 53 次方的值无法精确表示。
// 这就是说，对于那些很大的数的乘法，低位数值往往都是不精确的，Math.imul方法可以返回正确的低位数值。

(0x7fffffff * 0x7fffffff)|0 // 0
// 上面这个乘法算式，返回结果为 0。但是由于这两个二进制数的最低位都是 1，所以这个结果肯定是不正确的，
// 因为根据二进制乘法，计算结果的二进制最低位应该也是 1。这个错误就是因为它们的乘积超过了 2 的 53 次方，
// JavaScript 无法保存额外的精度，就把低位的值都变成了 0。Math.imul方法可以返回正确的值 1。

console.log(Math.imul(0x7fffffff, 0x7fffffff)); // 1
```

> - `Math.log(x)` 方法可返回一个数的自然对数(基于E)。如果 x 为负数，返回 NaN。 如果 x 为0，返回 -Infinity 。

```javascript
console.log(Math.log(1.4)); // 0.33647223662121284
console.log(Math.log(-1.4)); // NaN
console.log(Math.log(0)); // -Infinity
console.log(Math.log({})); // NaN
console.log(Math.log(undefined)); // NaN
console.log(Math.log(null)); // -Infinity
console.log(Math.log([])); // -Infinity
```

> - `Math.log1p(x)` 方法返回1 + x的自然对数，即Math.log(1 + x)。如果x小于-1，返回NaN。 **<font color=red>ES6支持</font>**

```javascript
console.log(Math.log1p(1));  // 0.6931471805599453
console.log(Math.log1p(0));  // 0
console.log(Math.log1p(-1)); // -Infinity
console.log(Math.log1p(-2)); // NaN

// 对于没有部署这个方法的环境，可以用下面的代码模拟。
Math.log1p = Math.log1p || function(x) {
  return Math.log(1 + x);
};
```

> - `Math.log2(x)` 返回以 2 为底的x的对数。如果x小于 0，则返回 NaN。 **<font color=red>ES6支持</font>**

```javascript
console.log(Math.log2(3));       // 1.584962500721156
console.log(Math.log2(2));       // 1
console.log(Math.log2(1));       // 0
console.log(Math.log2(0));       // -Infinity
console.log(Math.log2(-2));      // NaN
console.log(Math.log2(1024));    // 10
console.log(Math.log2(1 << 29)); // 29

// 对于没有部署这个方法的环境，可以用下面的代码模拟。
Math.log2 = Math.log2 || function(x) {
  return Math.log(x) / Math.LN2;
};
```

> - `Math.log10(x)` 返回以 10 为底的x的对数。如果x小于 0，则返回 NaN。 **<font color=red>ES6支持</font>**

```javascript
console.log(Math.log10(2));      // 0.3010299956639812
console.log(Math.log10(1));      // 0
console.log(Math.log10(0));      // -Infinity
console.log(Math.log10(-2));     // NaN
console.log(Math.log10(100000)); // 5

// 对于没有部署这个方法的环境，可以用下面的代码模拟。
Math.log10 = Math.log10 || function(x) {
  return Math.log(x) / Math.LN10;
};
```

> - `Math.max(n1,n2,n3,...,nX)` 方法可返回参数中带有较大的值的那个数。如果没有参数，则返回 -Infinity。如果有某个参数为 NaN，或是不能转换成数字的非数字值，则返回 NaN。

```javascript
console.log(Math.max(1.4,-1.4,0,'111')); // 111
console.log(Math.max(1.4,-1.4,0,{},[],undefined,null,'a')); // NaN 
console.log(Math.max()); // -Infinity
```

> - `Math.min(n1,n2,n3,...,nX)` 方法可返回参数中带有较小的值的那个数。如果没有参数，则返回 Infinity。如果有某个参数为 NaN，或是不能转换成数字的非数字值，则返回 NaN。

```javascript
console.log(Math.min(1.4,-1.4,0,'111')); // -1.4
console.log(Math.min(1.4,-1.4,0,{},[],undefined,null,'a')); // NaN 
console.log(Math.min()); // Infinity
```

> - `Math.pow(x, y)` 方法返回 x 的 y 次幂。x必需底数且是数字。x必需幂数且是数字。

```javascript
返回 4 的 3 次幂 (4*4*4):
console.log(Math.pow(4,3)); // 64
console.log(Math.pow()); // NaN
console.log(Math.pow({}, {})); // NaN
console.log(Math.pow(undefined, undefined)); // NaN
console.log(Math.pow(null, null)); //1
console.log(Math.pow([],[])); // 1
```

> - `Math.random(x)` 方法可返回介于 0（包含） ~ 1（不包含） 之间的一个随机数。

```javascript
console.log(Math.random()); // 0.496602693723625
```

> - `Math.round(x)` 方法可把一个数字舍入为最接近的整数。

```javascript
console.log(Math.round(2.5)); // 3
console.log(Math.round(-2.5)); // -2
console.log(Math.round(2.45)); // 2
console.log(Math.round(-2.45)); // -2
```

> - `Math.sign(x)` 方法用来判断一个数到底是正数、负数、还是零。对于非数值，会先将其转换为数值。  **<font color=red>ES6支持</font>**

```javascript
它会返回五种值。
    参数为正数，返回+1；
    参数为负数，返回-1；
    参数为 0，返回0；
    参数为-0，返回-0;
    其他值，返回NaN。

console.log(Math.sign(-5)); // -1
console.log(Math.sign(5)); // +1
console.log(Math.sign(0)); // +0
console.log(Math.sign(-0)); // -0
console.log(Math.sign(NaN)); // NaN 

// 如果参数是非数值，会自动转为数值。对于那些无法转为数值的值，会返回NaN。
console.log(Math.sign(''));  // 0
console.log(Math.sign(true));  // +1
console.log(Math.sign(false));  // 0
console.log(Math.sign(null));  // 0
console.log(Math.sign('9'));  // +1
console.log(Math.sign('foo'));  // NaN
console.log(Math.sign());  // NaN
console.log(Math.sign(undefined));  // NaN
console.log(Math.sign([]));  // 0
console.log(Math.sign({}));  // NaN

// 对于没有部署这个方法的环境，可以用下面的代码模拟。

Math.sign = Math.sign || function(x) {
  x = +x; // convert to a number
  if (x === 0 || isNaN(x)) {
    return x;
  }
  return x > 0 ? 1 : -1;
};
```

> - `Math.sin(x)` 方法返回参数 x 的正弦值。值在 -1.0 到 1.0 之间。

```javascript
console.log(Math.sin()); // NaN
console.log(Math.sin(0)); // 0
console.log(Math.sin({})); // NaN
console.log(Math.sin(undefined)); // NaN
console.log(Math.sin(null)); // 0
console.log(Math.sin([])); // 0
```

> - `Math.sinh(x)` 返回x的双曲正弦。 **<font color=red>ES6支持</font>**

```javascript
console.log(Math.sinh(0.5)); // 0.5210953054937474
console.log(Math.sinh(-1.02)); // -1.2062999118956097
console.log(Math.sinh(1.02)); // 1.2062999118956097
console.log(Math.sinh(1)); // 1.1752011936438014
console.log(Math.sinh(-1)); // -1.1752011936438014
console.log(Math.sinh({})); // NaN
console.log(Math.sinh(undefined)); // NaN
console.log(Math.sinh(null)); // 1
console.log(Math.sinh([])); // 1
```

> - `Math.sqrt(x)` 方法可返回一个数的平方根。x必须是大于等于 0 的数。如果 x 小于 0，则返回 NaN。

```javascript
console.log(Math.sqrt()); // NaN
console.log(Math.sqrt(9)); // 3
console.log(Math.sqrt(-9)); // NaN
console.log(Math.sqrt(0)); // 0
console.log(Math.sqrt({})); // NaN
console.log(Math.sqrt(undefined)); // NaN
console.log(Math.sqrt(null)); // 0
console.log(Math.sqrt([])); // 0
```

> - `Math.tan(x)` 方法可返回一个表示某个角的正切的数字。x是一个以弧度表示的角。将角度乘以 0.017453293 （2PI/360）即可转换为弧度。

```javascript
console.log(Math.tan()); // NaN
console.log(Math.tan(9)); // -0.45231565944180985
console.log(Math.tan(-9)); // 0.45231565944180985
console.log(Math.tan(0)); // 0
console.log(Math.tan({})); // NaN
console.log(Math.tan(undefined)); // NaN
console.log(Math.tan(null)); // 0
console.log(Math.tan([])); // 0
```

> - `Math.tanh(x)` 返回x的双曲正切。 **<font color=red>ES6支持</font>**

```javascript
console.log(Math.tanh(0.5)); // 0.46211715726000974
console.log(Math.tanh(-1.02)); // -0.7698665359089004
console.log(Math.tanh(1.02)); // 0.7698665359089004
console.log(Math.tanh(1)); // 0.7615941559557649
console.log(Math.tanh(-1)); // -0.7615941559557649
console.log(Math.tanh({})); // NaN
console.log(Math.tanh(undefined)); // NaN
console.log(Math.tanh(null)); // 0
console.log(Math.tanh([])); // 0
```

> - `Math.trunc(x)` 方法用于去除一个数的小数部分，返回整数部分。 **<font color=red>ES6支持</font>**  

```javascript
console.log(Math.trunc(4.1)); // 4
console.log(Math.trunc(4.9)); // 4
console.log(Math.trunc(-4.1)); // -4
console.log(Math.trunc(-4.9)); // -4
console.log(Math.trunc(-0.1234)); // -0

// 对于非数值，Math.trunc内部使用Number方法将其先转为数值。
console.log(Math.trunc('123.456')); // 123
console.log(Math.trunc(true)); //1
console.log(Math.trunc(false)); // 0
console.log(Math.trunc(null)); // 0
console.log(Math.trunc([])); // 0

// 对于空值和无法截取整数的值，返回NaN。
console.log(Math.trunc(NaN));      // NaN
console.log(Math.trunc('foo'));    // NaN
console.log(Math.trunc());         // NaN
console.log(Math.trunc(undefined)); // NaN
console.log(Math.trunc({})); // NaN

// 对于没有部署这个方法的环境，可以用下面的代码模拟。
Math.trunc = Math.trunc || function(x) {
  return x < 0 ? Math.ceil(x) : Math.floor(x);
};
```

------

# Number对象

## Number对象属性

> - `Number.EPSILON ` 常量，它表示 1 与大于 1 的最小浮点数之间的差。 **<font color=red>ES6支持</font>**

```javascript
// 对于 64 位浮点数来说，大于 1 的最小浮点数相当于二进制的1.00..001，小数点后面有连续 51 个零。这个值减去 1 之后，就等于 2 的-52 次方。
console.log(Number.EPSILON === Math.pow(2, -52));  // true
console.log(Number.EPSILON);  // 2.220446049250313e-16
console.log(Number.EPSILON.toFixed(20)); // "0.00000000000000022204"

// 引入一个这么小的量的目的，在于为浮点数计算，设置一个误差范围。我们知道浮点数计算是不精确的。
console.log(0.1 + 0.2);  // 0.30000000000000004
console.log(0.1 + 0.2 - 0.3); // 5.551115123125783e-17
console.log(5.551115123125783e-17.toFixed(20)); // '0.00000000000000005551'

// 同时上面代码解释了，为什么比较0.1 + 0.2与0.3得到的结果是false。
console.log(0.1 + 0.2 === 0.3); // false

//Number.EPSILON可以用来设置“能够接受的误差范围”。比如，误差范围设为 2 的-50 次方（即Number.EPSILON * Math.pow(2, 2)），即如果两个浮点数的差小于这个值，我们就认为这两个浮点数相等。
console.log(5.551115123125783e-17 < Number.EPSILON * Math.pow(2, 2)); // true

// 因此，Number.EPSILON的实质是一个可以接受的最小误差范围。下面是误差检查函数
function withinErrorMargin (left, right) {
  return Math.abs(left - right) < Number.EPSILON * Math.pow(2, 2);
}

0.1 + 0.2 === 0.3 // false
withinErrorMargin(0.1 + 0.2, 0.3) // true

1.1 + 1.3 === 2.4 // false
withinErrorMargin(1.1 + 1.3, 2.4) // true

```

> - `Number.MAX_SAFE_INTEGER` 常量，返回安全整数的最大值  **<font color=red>ES6支持</font>**

```javascript
console.log(Number.MAX_SAFE_INTEGER); // 9007199254740991
```

> - `Number.MAX_VALUE` 静态只读属性是 JavaScript 中可表示的最大的数。它的近似值为 1.7976931348623157 x 10308。大于MAX_VALUE的数表示无穷大。

```javascript
console.log(Number.MAX_VALUE); // 1.7976931348623157e+308
//MAX_VALUE 是 Javascript Number对象的静态属性，只能通过 Number.MAX_VALUE 调用。.
// 使用自定义的Number x（x.MAX_VALUE ） 将无法获取 MAX_VALUE 属性:
var x = 100;
console.log(x.MAX_VALUE); // undefined
```

> - `Number.MIN_SAFE_INTEGER` 常量，返回安全整数的最小值  **<font color=red>ES6支持</font>**

```javascript
console.log(Number.MIN_SAFE_INTEGER); // -9007199254740991
```

> - `Number.MIN_VALUE` 静态只读属性是 JavaScript 中可表示的最小的数（接近 0 ，但不是负数）。它的近似值为 5 x 10-324。
注意： 比 MIN_VALUE 属性小的数将用 0 表示。
注意： MIN_VALUE 是 JavaScript 最接近0的数,不是负值，负值属性为 MAX_NUMBER。

```javascript
console.log(Number.MIN_VALUE); // 5e-324
//MIN_VALUE 是 Javascript Number对象的静态属性，只能通过 Number.MIN_VALUE 调用。.
// 使用自定义的Number x（x.MIN_VALUE ） 将无法获取 MIN_VALUE 属性:
var x = 100;
console.log(x.MIN_VALUE); // undefined
```

> - `Number.NEGATIVE_INFINITY ` 静态只读属性表示负无穷大。小于 Number.MIN_VALUE 的值。

```javascript
console.log(Number.NEGATIVE_INFINITY); // -Infinity
// NEGATIVE_INFINITY 是 JavaScript Number 对象的静态变量。
// 调用方法为：Number.NEGATIVE_INFINITY.
// 使用 自定义 Number对象 x 调用该属性（x.NEGATIVE_INFINITY）将返回 undefined:
var x = 100;
console.log(x.NEGATIVE_INFINITY); // undefined
```

> - `Number.NaN` 静态只读属性是代表非数字值的特殊值。该属性用于指示某个值不是数字。
可以把 Number 对象设置为该值，来指示其不是数字值。
提示： 请使用 isNaN() 全局函数来判断一个值是否是 NaN 值。

```javascript
console.log(Number.NaN); // NaN
```

> - `Number.POSITIVE_INFINITY ` 静态只读属性表示正无穷大。小于 Number.MAX_VALUE  的值。

```javascript
console.log(Number.POSITIVE_INFINITY); // -Infinity
// POSITIVE_INFINITY 是 JavaScript Number 对象的静态变量。
// 调用方法为：Number.POSITIVE_INFINITY.
// 使用 自定义 Number对象 x 调用该属性（x.POSITIVE_INFINITY）将返回 undefined:
var x = 100;
console.log(x.POSITIVE_INFINITY); // undefined
// 
```

> - `Number.prototype` 属性允许您向对象添加属性和方法。
当构造一个属性, 所有的 Number 对象将被添加上该属性及值。
当构造一个方法时，所有的 Number 对象都会有这个方法。
注意： Number.prototype 不允许引用一个单独的 Number 对象，但是可以使用 Number() 对象。
注意：prototype 型是一个全局对象的构造函数，可用于所有的JavaScript对象

```javascript
// 创建一个方法，给出了数字对象的属性，返回数字的一半价值：
Number.prototype.myMet = function(){
    this.myProp = this.valueOf()/2;
}

// 创造一个 Number 对象, 调用 myMet 方法:
var n = new Number(55);
n.myMet();
var x = n.myProp;
console.log(x); // 27.5

```

## Number对象方法

> - `Number.isFinite(x)` 用来检查一个数值是否为有限的（finite）。**<font color=red>ES6支持</font>**

```javascript
console.log(Number.isFinite(15)); // true
console.log(Number.isFinite(0.8)); // true
console.log(Number.isFinite(NaN)); // false
console.log(Number.isFinite([])); // false
console.log(Number.isFinite({})); // false
console.log(Number.isFinite(undefined)); // false
console.log(Number.isFinite(null)); // false
console.log(Number.isFinite(Infinity)); // false
console.log(Number.isFinite(-Infinity)); // false
console.log(Number.isFinite('foo')); // false
console.log(Number.isFinite('15')); // false
console.log(Number.isFinite(true)); // false

// ES5 可以通过下面的代码，部署Number.isFinite方法。
(function (global) {
  var global_isFinite = global.isFinite;

  Object.defineProperty(Number, 'isFinite', {
    value: function isFinite(value) {
      return typeof value === 'number' && global_isFinite(value);
    },
    configurable: true,
    enumerable: false,
    writable: true
  });
})(this);
```


> - `Number.isNaN()` 用来检查一个值是否为NaN。 **<font color=red>ES6支持</font>**

```javascript
console.log(Number.isNaN(NaN)); // true
console.log(Number.isNaN([])); // false
console.log(Number.isNaN({})); // false
console.log(Number.isNaN(undefined)); // false
console.log(Number.isNaN(15)); // false
console.log(Number.isNaN('15')); // false
console.log(Number.isNaN(true)); // false
console.log(Number.isNaN(9/NaN)); // true
console.log(Number.isNaN('true'/0)); // true
console.log(Number.isNaN('true'/'true')); // true

// ES5 通过下面的代码，部署Number.isNaN()。
(function (global) {
  var global_isNaN = global.isNaN;

  Object.defineProperty(Number, 'isNaN', {
    value: function isNaN(value) {
      return typeof value === 'number' && global_isNaN(value);
    },
    configurable: true,
    enumerable: false,
    writable: true
  });
})(this);
```

> - `isNaN()和isFinite()`与传统的全局方法isFinite()和isNaN()的区别在于，传统方法先调用Number()将非数值的值转为数值，再进行判断。
而这两个新方法只对数值有效，Number.isFinite()对于非数值一律返回false, Number.isNaN()只有对于NaN才返回true，非NaN一律返回false。

```javascript
console.log(isFinite(25)); // true
console.log(isFinite("25")); // true
console.log(Number.isFinite(25)); // true
console.log(Number.isFinite("25")); // false

console.log(isNaN(NaN)); // true
console.log(isNaN("NaN")); // true
console.log(Number.isNaN(NaN)); // true
console.log(Number.isNaN("NaN")); // false
console.log(Number.isNaN(1)); // false
```

> - `Number.isInteger()` 用来判断一个值是否为整数。需要注意的是，在 JavaScript 内部，整数和浮点数是同样的储存方法，所以 3 和 3.0 被视为同一个值。 **<font color=red>ES6支持</font>**

```javascript
console.log(Number.isInteger(25)); // true
console.log(Number.isInteger(25.0)); // true
console.log(Number.isInteger(25.1)); // false
console.log(Number.isInteger("15")); // false
console.log(Number.isInteger(true)); // false

// ES5 可以通过下面的代码，部署Number.isInteger()。
(function (global) {
  var floor = Math.floor,
    isFinite = global.isFinite;

  Object.defineProperty(Number, 'isInteger', {
    value: function isInteger(value) {
      return typeof value === 'number' &&
        isFinite(value) &&
        floor(value) === value;
    },
    configurable: true,
    enumerable: false,
    writable: true
  });
})(this);
```

> - `Number.isSafeInteger()` 用来判断一个整数是否落在这个范围之内。准确表示的整数范围在-2^53到2^53之间（不含两个端点），超过这个范围，无法精确表示这个值。 **<font color=red>ES6支持</font>**

```javascript
console.log(Number.isSafeInteger('a')); // false
console.log(Number.isSafeInteger(null)); // false
console.log(Number.isSafeInteger(NaN)); // false
console.log(Number.isSafeInteger(Infinity)); // false
console.log(Number.isSafeInteger(-Infinity)); // false

console.log(Number.isSafeInteger(3)); // true
console.log(Number.isSafeInteger(1.2)); // false
console.log(Number.isSafeInteger(9007199254740990)); // true
console.log(Number.isSafeInteger(9007199254740992)); // false

console.log(Number.isSafeInteger(Number.MIN_SAFE_INTEGER - 1));// false
console.log(Number.isSafeInteger(Number.MIN_SAFE_INTEGER)); // true
console.log(Number.isSafeInteger(Number.MAX_SAFE_INTEGER)); // true
console.log(Number.isSafeInteger(Number.MAX_SAFE_INTEGER + 1)); // false

// 这个函数的实现很简单，就是跟安全整数的两个边界值比较一下。
Number.isSafeInteger = function (n) {
  return (typeof n === 'number' &&
    Math.round(n) === n &&
    Number.MIN_SAFE_INTEGER <= n &&
    n <= Number.MAX_SAFE_INTEGER);
}

// 实际使用这个函数时，需要注意。验证运算结果是否落在安全整数的范围内，不要只验证运算结果，而要同时验证参与运算的每个值。
console.log(Number.isSafeInteger(9007199254740993)); // false
console.log(Number.isSafeInteger(990)); // true
console.log(Number.isSafeInteger(9007199254740993 - 990)); // true
console.log(9007199254740993 - 990);
// 返回结果 9007199254740002
// 正确答案应该是 9007199254740003
// 上面代码中，9007199254740993不是一个安全整数，但是Number.isSafeInteger会返回结果，显示计算结果是安全的。这是因为，这个数超出了精度范围，导致在计算机内部，以9007199254740992的形式储存。

console.log(9007199254740993 === 9007199254740992); // true

// 所以，如果只验证运算结果是否为安全整数，很可能得到错误结果。下面的函数可以同时验证两个运算数和运算结果。
function trusty (left, right, result) {
  if (
    Number.isSafeInteger(left) &&
    Number.isSafeInteger(right) &&
    Number.isSafeInteger(result)
  ) {
    return result;
  }
  throw new RangeError('Operation cannot be trusted!');
}

trusty(9007199254740993, 990, 9007199254740993 - 990) // RangeError: Operation cannot be trusted!

trusty(1, 2, 3) // 3
```

> - `Number.parseInt()` 将字符串转换为整数并返回。ES6 将全局方法parseInt()移植到Number对象上面，行为完全保持不变。这样做的目的，是逐步减少全局性方法，使得语言逐步模块化。 **<font color=red>ES6支持</font>**

```javascript
// ES5的写法
console.log(parseInt('12.34')); // 12

// ES6的写法
console.log(Number.parseInt('12.34')); // 12

console.log(Number.parseFloat === parseFloat); // true
```


> - `Number.parseFloat()` 将字符串转换为浮点数并返回。ES6 将全局方法parseFloat()移植到Number对象上面，行为完全保持不变。这样做的目的，是逐步减少全局性方法，使得语言逐步模块化。 **<font color=red>ES6支持</font>**

```javascript
// ES5的写法
console.log(parseFloat('123.45#')); // 123.45

// ES6的写法
console.log(Number.parseFloat('123.45#')); // 123.45

console.log(Number.parseFloat === parseFloat); // true
```

> - `Number.prototype.toExponential(x)` 方法把数字转换为指数计数法表示的字符串，并具有指定的小数位数。x是可选/Number类型,指定保留的小数位数。
如果没有提供x参数，则toExponential()方法将返回足够多位数字，以便唯一指定该数字。
如果提供了参数，则参数x必须介于 [0, 20] 之间，否则将报错。
如果数字本身的小数位数大于参数x，则根据第x + 1位小数上的值进行四舍五入。

```javascript
console.log(Number(423.536).toExponential()); // 4.23536e+2
console.log(Number(562345.12456).toExponential(3)); // 5.623e+5
console.log(Number(-2651.10).toExponential(4));  // -2.6511e+3
console.log(Number(4564561.12457).toExponential(0)); // 5e+6
console.log(Number(231).toExponential(5)); // 2.31000e+2
```

> - `Number.prototype.toFixed(x)` 方法可把 Number 四舍五入为指定小数位数的数字。x值必需。
如果没有提供x参数或其参数值为undefined，则x参数将默认为0。
如果提供了参数，则参数x必须介于 [0, 20] 之间，否则将报错。
如果数字本身的小数位数多于参数x，则根据第x + 1位小数上的值进行四舍五入。

```javascript
console.log(Number(423.536).toFixed() ); // 424
console.log(Number(562345.12456).toFixed(3)); // 562345.125
console.log(Number(-2651.10).toFixed(4)); // -2651.1000
console.log(Number(4564561.12457).toFixed(0)); // 4564561
console.log(Number(231).toFixed(5)); // 231.00000
console.log(Number(1232).toFixed(undefined)); // 1232
console.log(Number(123124234).toFixed(50)); // Uncaught RangeError: toFixed() digits argument must be between 0 and 20
```

> - `Number.prototype.toPrecision(x)` 方法可在对象的值超出指定位数时将其转换为指数计数法。x值可选/Number类型指定有效数字的位数。
如果没有提供x参数或其值为undefined，则将转而调用toString()方法进行处理。而不是把数字转换成十进制的值。
如果提供了参数，则参数x必须介于 1 ~ 21 之间（且包括 1 和 21）即[1, 21] 之间，否则将报错。
如果数字的有效位数大于x，将会根据第x + 1位的有效数字进行四舍五入。

```javascript
// 调用的是toString()方法
console.log(Number(423.536).toPrecision()); // 423.536

// 由于整数部分有6位，要求只有3位有效数字，必须采用指数计数法才能表示。
console.log(Number(562345.12456).toPrecision(3)); // 5.62e+5

// 整数部分有4位，要求的有效数字为4位，采用定点表示法
console.log(Number(-2651.10).toPrecision(4)); // -2651

// 整数部分有7位，要求有效数字为1位，采用指数计数法
console.log(Number(4564561.12457).toPrecision(1)); // 5e+6

// 整数部分有3位，要求有效数字为5位，采用定点表示法，并在小数部分填充两个0
console.log(Number(231).toPrecision(5)); // 231.00
```

> - `Number.prototype.toString(x)` 把数字转换为字符串,x值可选/Number类型指定的基数(进制数)，默认为10。
规定表示数字的基数，使 2 ~ 36 之间的整数。若省略该参数，则使用基数 10。但是要注意，如果该参数是 10 以外的其他值，则 ECMAScript 标准允许实现返回任意值。
2 - 数字以二进制值显示
8 - 数字以八进制值显示
16 - 数字以十六进制值显示

```javascript
// 二进制
console.log(Number(1024).toString(2)); // 10000000000

// 默认十进制
console.log(Number(1024).toString()); // 1024

// 八进制
console.log(Number(1024).toString(8)); // 2000

// 十六进制
console.log(Number(1024).toString(16)); // 400
```


> - `Number.prototype.valueOf() ` 返回一个 Number 对象的基本数字值。可以字符串返回数字。

```javascript
console.log(Number(1024).valueOf()); // 1024
```

# Array对象

## Array对象的属性

> - `Array.length` 是Array的实例属性。返回或设置一个数组中的元素个数。该值是一个无符号 32-bit 整数，并且总是大于数组最高项的下标。值是一个 0 到 232-1 的整数。

```javascript

var items = ['shoes', 'shirts', 'socks', 'sweaters'];
console.log(items.length);  // 4 

Array.length 属性的属性特性：
    writable  true
    enumerable  false
    configurable  false
Writable ：如果设置为false，该属性值将不能被修改。
Configurable ：如果设置为false，删除或更改任何属性都将会失败。
Enumerable ：如果设置为 true ，属性可以通过迭代器for或for...in进行迭代。
```

## Array对象的方法

> - `Array.from(arrayLike, mapFn, thisArg)` 方法用于将两类对象转为真正的数组：伪数组对象（拥有一个 length 属性和若干索引属性的任意对象）
和可遍历（iterable）的对象（包括 ES6 新增的数据结构 Set 和 Map）。  **<font color=red>ES6支持</font>**

```javascript
语法：
Array.from(arrayLike, mapFn, thisArg);
参数：
  arrayLike
    想要转换成数组的伪数组对象或可迭代对象。
  mapFn (可选参数)
    如果指定了该参数，新数组中的每个元素会执行该回调函数。
  thisArg (可选参数)
    可选参数，执行回调函数 mapFn 时 this 对象。
返回值：
  一个新的数组实例

示例：

// 
var arrayLike = {
    '0': 'a',
    '1': 'b',
    '2': 'c',
    length: 3
};

// ES5的写法
console.log([].slice.call(arrayLike)); // ['a', 'b', 'c']

// ES6的写法
console.log(Array.from(arrayLike)); // ['a', 'b', 'c']


// Array from a String
console.log(Array.from('foo'));  // ["f", "o", "o"]

// Array from a Set
let s = new Set(['foo', window]); 
console.log(Array.from(s));  // ["foo", window]

// Array from a Map
let m = new Map([[1, 2], [2, 4], [4, 8]]);
console.log(Array.from(m));  // [[1, 2], [2, 4], [4, 8]]

// Array from an Array-like object (arguments)
function f() {
  return Array.from(arguments);
}

console.log(f(1, 2, 3)); // [1, 2, 3]

// Using arrow functions and Array.from
// Using an arrow function as the map function to
// manipulate the elements
console.log(Array.from([1, 2, 3], x => x + x));  // [2, 4, 6]


// Generate a sequence of numbers
// Since the array is initialized with `undefined` on each position,
// the value of `v` below will be `undefined`
console.log(Array.from({length: 5}, (v, i) => i)); // [0, 1, 2, 3, 4]

```

> - `Array.isArray(obj)` 用于确定obj是否是一个 Array,如果对象是 Array，则为true; 否则为false。当检测Array实例时, Array.isArray 优于 instanceof,因为Array.isArray能检测iframes.

```javascript
// 下面的函数调用都返回 true
console.log(Array.isArray([])); // true
console.log(Array.isArray([1])); // true
console.log(Array.isArray(new Array())); // true
// 鲜为人知的事实：其实 Array.prototype 也是一个数组。
console.log(Array.isArray(Array.prototype));  // true

// 下面的函数调用都返回 false
console.log(Array.isArray()); // false
console.log(Array.isArray({})); // false
console.log(Array.isArray(null)); // false
console.log(Array.isArray(undefined)); // false
console.log(Array.isArray(17)); // false
console.log(Array.isArray('Array')); // false
console.log(Array.isArray(true)); // false
console.log(Array.isArray(false)); // false
console.log(Array.isArray({ __proto__: Array.prototype })); // false

// 假如不存在 Array.isArray()，则在其他代码之前运行下面的代码将创建该方法。

if (!Array.isArray) {
  Array.isArray = function(arg) {
    return Object.prototype.toString.call(arg) === '[object Array]';
  };
}
```

> - `Array.of(element0[, element1[, ...[, elementN]]])`  方法创建一个具有可变数量参数的新数组实例，而不考虑参数的数量或类型。 **<font color=red>ES6支持</font>**

```javascript
// Array.of() 和 Array 构造函数之间的区别在于处理整数参数：Array.of(7) 创建一个具有单个元素 7 的数组，
// 而 Array(7) 创建一个包含 7 个 undefined 元素的数组。
// elementN 任意个参数，将按顺序成为返回数组中的元素。

console.log(Array.of(undefined)); // [undefined]
console.log(Array.of(3, 11, 8)); // [3,11,8]
console.log(Array.of(3)); // [3]
console.log(Array.of(3).length); // 1

console.log(Array()); // []
console.log(Array(3)); // [, , ,]
console.log(Array(3, 11, 8)); // [3, 11, 8]

// 如果原生不支持的话，在其他代码之前执行以下代码会创建 Array.of() 。
if (!Array.of) {
  Array.of = function() {
    return Array.prototype.slice.call(arguments);
  };
}

或者

function ArrayOf(){
  return [].slice.call(arguments);
}
```

- `Array.prototype.concat()`  方法用于合并两个或多个数组。此方法不会更改现有数组，而是返回一个新数组。

```javascript
语法
  ar new_array = old_array.concat(value1[, value2[, ...[, valueN]]])
参数
  valueN
    将数组和/或值连接成新数组。详情请参阅下文描述。
返回值
  新的 Array 实例。

描述
concat方法创建一个新的数组，它由被调用的对象中的元素组成，每个参数的顺序依次是该参数的元素（如果参数是数组）或参数本身（如果参数不是数组）。它不会递归到嵌套数组参数中。
concat方法不会改变this或任何作为参数提供的数组，而是返回一个浅拷贝，它包含与原始数组相结合的相同元素的副本。 原始数组的元素将复制到新数组中，如下所示：

  对象引用（而不是实际对象）：concat将对象引用复制到新数组中。 原始数组和新数组都引用相同的对象。 也就是说，如果引用的对象被修改，则更改对于新数组和原始数组都是可见的。 这包括也是数组的数组参数的元素。
  数据类型如字符串，数字和布尔（不是String，Number 和 Boolean 对象）：concat将字符串和数字的值复制到新数组中。
  注意：数组/值在连接时保持不变。此外，对于新数组的任何操作（仅当元素不是对象引用时）都不会对原始数组产生影响，反之亦然。

// 将两个数组合并为一个新数组：

var alpha = ['a', 'b', 'c'];
var numeric = [1, 2, 3];
console.log(alpha.concat(numeric)); // ['a', 'b', 'c', 1, 2, 3]

// 将三个数组合并为一个新数组：

var num1 = [1, 2, 3],
    num2 = [4, 5, 6],
    num3 = [7, 8, 9];

var nums = num1.concat(num2, num3);
console.log(nums);  // [1, 2, 3, 4, 5, 6, 7, 8, 9]

// 将三个值连接到数组：

var alpha = ['a', 'b', 'c'];
var alphaNumeric = alpha.concat(1, [2, 3]);
console.log(alphaNumeric);  // ['a', 'b', 'c', 1, 2, 3]

// 合并嵌套数组并保留引用：

var num11 = [[1]];
var num22 = [2, [3]];
var numss = num11.concat(num22);

console.log(numss); // [[1], 2, [3]]

// modify the first element of num1
num11[0].push(4);
console.log(numss); // [[1, 4], 2, [3]]
```

- `Array.prototype.copyWithin(target, start, end)` 方法浅复制数组的一部分到同一数组中的另一个位置，并返回它，而不修改其大小。 **<font color=red>ES6支持</font>**

```javascript
语法
  arr.copyWithin(target)

  arr.copyWithin(target, start)

  arr.copyWithin(target, start, end)

  arr.copyWithin(目标索引, [源开始索引], [结束源索引])
参数
  `target`  目标索引 
    0 为基底的索引，复制序列到该位置。如果是负数，`target` 将从末尾开始计算。
    如果 `target` 大于等于 `arr.length`，将会不发生拷贝。如果 `target` 在 `start` 之后，复制的序列将被修改以符合 arr.length。
  `start`  [源开始索引]
    0 为基底的索引，开始复制元素的起始位置。如果是负数，`start` 将从末尾开始计算。
    如果 `start` 被忽略，`copyWithin` 将会从0开始复制。
  `end`  [ 结束源索引]
    0 为基底的索引，开始复制元素的结束位置。`copyWithin` 将会拷贝到该位置，但不包括 `end` 这个位置的元素。如果是负数， `end` 将从末尾开始计算。
    如果 `end` 被忽略，`copyWithin` 将会复制到 `arr.length`。
返回值
  改变了的数组。

console.log(["alpha", "beta", "copy", "delta"].copyWithin(1)); // ["alpha", "alpha", "beta", "copy"]
console.log(["alpha", "beta", "copy", "delta"].copyWithin(1,2)); //["alpha", "copy", "delta", "delta"]
console.log(["alpha", "beta", "copy", "delta"].copyWithin(1, 2, 3)); // ["alpha", "copy", "copy", "delta"]

// 将3号位复制到0号位
[1, 2, 3, 4, 5, 6].copyWithin(0, 3, 4); // [4, 2, 3, 4, 5, 6]

// -2相当于4号位，-1相当于5号位
[1, 2, 3, 4, 5, 6].copyWithin(0, -2, -1); // [5, 2, 3, 4, 5, 6]

// 将3号位复制到0号位
[].copyWithin.call({length: 5, 3: 1}, 0, 3); // {0: 1, 3: 1, length: 5}

[1, 2, 3, 4, 5, 6].copyWithin(-2); // [1, 2, 3, 4, 1, 2]

[1, 2, 3, 4, 5, 6].copyWithin(2); //  [1, 2, 1, 2, 3, 4]

[1, 2, 3, 4, 5, 6].copyWithin(0, 3); // [4, 5, 6, 4, 5, 6]

[1, 2, 3, 4, 5, 6].copyWithin(-2, -3, -1); // [1, 2, 3, 4, 4, 5]

[1, 2, 3, 4, 5, 6].copyWithin(2, 1, 3); // [1, 2, 2, 3, 5, 6]


// 将2号位到数组结束，复制到0号位
let i32a = new Int32Array([1, 2, 3, 4, 5]);
i32a.copyWithin(0, 2); // Int32Array [3, 4, 5, 4, 5]

// 对于没有部署 TypedArray 的 copyWithin 方法的平台
// 需要采用下面的写法
[].copyWithin.call(new Int32Array([1, 2, 3, 4, 5]), 0, 3, 4); // Int32Array [4, 2, 3, 4, 5]
```

- `Array.prototype.entries()`

```javascript

```

- `Array.prototype.every()`

```javascript

```

- `Array.prototype.fill()`

```javascript

```

- `Array.prototype.filter()`

```javascript

```

- `Array.prototype.find()`

```javascript

```

- `Array.prototype.findIndex()`

```javascript

```

- `Array.prototype.forEach()`

```javascript

```

- `Array.prototype.includes()`

```javascript

```

- `Array.prototype.indexOf()`

```javascript

```

- `Array.prototype.join()`

```javascript

```

- `Array.prototype.keys()`

```javascript

```

- `Array.prototype.lastIndexOf()`

```javascript

```

- `Array.prototype.map()`

```javascript

```

- `Array.prototype.pop()`

```javascript

```

- `Array.prototype.push()`

```javascript

```

- `Array.prototype.reduce()`

```javascript

```

- `Array.prototype.reduceRight()`

```javascript

```

- `Array.prototype.reverse()`

```javascript

```

- `Array.prototype.shift()`

```javascript

```

- `Array.prototype.slice()`

```javascript

```

- `Array.prototype.some()`

```javascript

```

- `Array.prototype.sort()`

```javascript

```

- `Array.prototype.splice()`

```javascript

```

- `Array.prototype.toLocaleString()`

```javascript

```

- `Array.prototype.toSource()`

```javascript

```

- `Array.prototype.toString()`

```javascript

```

- `Array.prototype.unshift()`

```javascript

```

- `Array.prototype.values()`

```javascript

```

- `Array.`

```javascript

```

- `Array.`

```javascript

```

------

# String对象

## String对象的属性

## String对象的方法

------

# Date对象

## Date对象的属性

## Date对象的方法






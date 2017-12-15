---
title: JavaScript对象介绍之Math对象
date: 2017-12-14 08:41:45
tags: 
    - JavaScript
    - Math对象
categories: JavaScript
---

# Math对象属性

- `Math.E` 返回算术常量 e，即自然对数的底数（约等于2.718）。
  
    ```javascript
    console.log(Math.E); // 2.718281828459045
    ```

- `Math.LN2` 返回 2 的自然对数（约等于0.693）。

    ```javascript
    console.log(Math.LN2); // 0.6931471805599453
    ```

- `Math.LN10` 返回 10 的自然对数（约等于2.302）。

    ```javascript
    console.log(Math.LN10); // 2.302585092994046
    ```

- `Math.LOG2E` 返回以 2 为底的 e 的对数（约等于 1.414）。

    ```javascript
    console.log(Math.LOG2E); // 1.4426950408889634
    ```

- `Math.LOG10E` 返回以 10 为底的 e 的对数（约等于0.434）。

    ```javascript
    console.log(Math.LOG10E); // 0.4342944819032518
    ```

- `Math.PI` 返回圆周率（约等于3.14159）。

    ```javascript
    console.log(Math.PI); // 3.141592653589793
    ```

- `Math.SQRT1_2` 返回返回 2 的平方根的倒数（约等于 0.707）。

    ```javascript
    console.log(Math.SQRT1_2); // 0.7071067811865476
    ```

- `Math.SQRT2` 返回 2 的平方根（约等于 1.414）。

    ```javascript
    console.log(Math.SQRT2); // 1.4142135623730951
    ```

# Math对象方法

- `Math.abs(x)` 方法返回一个数的绝对值，x必须是一个数值。如果x不是数字返回NaN，如果x为null返回0

    ```javascript
    console.log(Math.abs(-7.25));  // 7.25
    console.log(Math.abs('a')); // NaN
    console.log(Math.abs({})); // NaN
    console.log(Math.abs(undefined)); // NaN
    console.log(Math.abs(null)); // 0
    console.log(Math.abs([])); // 0
    ```

- `Math.acos(x)` 方法返回x的反余弦值，返回的值是0到PI之间的弧度值。如果x的值超过-1.0~1.0的范围，返回NaN。如果x值为-1，返回PI。

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

- `Math.acosh(x)` 返回x的反双曲余弦。 **<font color=red>ES6支持</font>**

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

- `Math.asin(x)` 方法返回一个数的反正弦值，返回的值是-P1/2~PI/2之间的弧度值。如果x超过了-1.0~1.0的范围，返回NaN。如果x值为1，返回PI/2。

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

- `Math.asinh(x)` 返回x的反双曲正弦。 **<font color=red>ES6支持</font>**

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

- `Math.atan(x)`  方法以介于 -PI/2 与 PI/2 弧度之间的数值来返回 x 的反正切值。x必须是数值

    ```javascript
    console.log(Math.atan(0.5)); // 0.4636476090008061
    console.log(Math.atan({})); // NaN
    console.log(Math.atan(undefined)); // NaN
    console.log(Math.atan(null)); // 0
    console.log(Math.atan([])); // 0
    ```

- `Math.atan2(y, x)` 返回从 x 轴到点 (x,y) 的角度（介于 -PI/2 与 PI/2 弧度之间）。

    ```javascript
    指定一个坐标（x，y），坐标值（4,8），使用 atan2() 方法计算坐标与X轴之间的角度的弧度 ，如下实例：
    console.log(Math.atan2(8,4));  // 1.1071487177940904
    ```

- `Math.atanh(x)` 返回x的反双曲正切。 **<font color=red>ES6支持</font>**

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

- `Math.cbrt(x)` 方法用于计算一个数的立方根。 **<font color=red>ES6支持</font>**

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

- `Math.ceil(x)` 方法执行的是向上取整计算，它返回的是大于或等于函数参数，并且与之最接近的整数。
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

- `Math.clz32(x)`  方法返回一个数的 32 位无符号整数形式有多少个前导 0。 **<font color=red>ES6支持</font>**

    ```javascript
    console.log(Math.clz32(0)); // 32
    console.log(Math.clz32(1)); // 31
    console.log(Math.clz32(1000)); // 22
    console.log(Math.clz32(0b01000000000000000000000000000000)); // 1
    console.log(Math.clz32(0b00100000000000000000000000000000)); // 2
    /**
     * 上面代码中，0 的二进制形式全为 0，所以有 32 个前导 0；
     * 1 的二进制形式是0b1，只占 1 位，所以 32 位之中有 31 个前导 0；
     * 1000 的二进制形式是0b1111101000，一共有 10 位，所以 32 位之中有 22 个前导 0。
     * clz32这个函数名就来自”count leading zero bits in 32-bit binary representation of a number“
     *（计算一个数的 32 位二进制形式的前导 0 的个数）的缩写。
     */


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

- `Math.cos(x)` 方法可返回一个数字的余弦值。 返回的是 -1.0 到 1.0 之间的数。

    ```javascript
    console.log(Math.cos(3)); // -0.9899924966004454
    console.log(Math.cos({})); // NaN
    console.log(Math.cos(undefined)); // NaN
    console.log(Math.cos(null)); // 1
    console.log(Math.cos([])); // 1
    ```

- `Math.cosh(x)` 返回x的双曲余弦。 **<font color=red>ES6支持</font>**

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

- `Math.exp(x)` 方法可返回 e 的 x 次幂的值。 E 为自然底数 (近似值 2.7183)。

    ```javascript
    console.log(Math.exp(1)); // 2.718281828459045
    console.log(Math.exp({})); // NaN
    console.log(Math.exp(undefined)); // NaN
    console.log(Math.exp(null)); // 1
    console.log(Math.exp([])); // 1
    ```

- `Math.expm1(x)` 返回 ex - 1，即Math.exp(x) - 1。 **<font color=red>ES6支持</font>**

    ```javascript
    console.log(Math.expm1(-1)); // -0.6321205588285577
    console.log(Math.expm1(0));  // 0
    console.log(Math.expm1(1));  // 1.718281828459045

    //对于没有部署这个方法的环境，可以用下面的代码模拟。
    Math.expm1 = Math.expm1 || function(x) {
      return Math.exp(x) - 1;
    };
    ```

- `Math.floor(x)` 方法返回小于等于x的最大整数。如果传递的参数是一个整数，该值不变。

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

- `Math.fround(x)` 方法返回一个数的单精度浮点数形式。 **<font color=red>ES6支持</font>**

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

- `Math.hypot(x)` 方法返回所有参数x的平方和的平方根。**<font color=red>ES6支持</font>**

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

- `Math.imul(x, y)` 方法返回两个数以 32 位带符号整数形式相乘的结果，返回的也是一个 32 位的带符号整数。 **<font color=red>ES6支持</font>**

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

- `Math.log(x)` 方法可返回一个数的自然对数(基于E)。如果 x 为负数，返回 NaN。 如果 x 为0，返回 -Infinity 。

    ```javascript
    console.log(Math.log(1.4)); // 0.33647223662121284
    console.log(Math.log(-1.4)); // NaN
    console.log(Math.log(0)); // -Infinity
    console.log(Math.log({})); // NaN
    console.log(Math.log(undefined)); // NaN
    console.log(Math.log(null)); // -Infinity
    console.log(Math.log([])); // -Infinity
    ```

- `Math.log1p(x)` 方法返回1 + x的自然对数，即Math.log(1 + x)。如果x小于-1，返回NaN。 **<font color=red>ES6支持</font>**

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

- `Math.log2(x)` 返回以 2 为底的x的对数。如果x小于 0，则返回 NaN。 **<font color=red>ES6支持</font>**

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

- `Math.log10(x)` 返回以 10 为底的x的对数。如果x小于 0，则返回 NaN。 **<font color=red>ES6支持</font>**

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

- `Math.max(n1,n2,n3,...,nX)` 方法可返回参数中带有较大的值的那个数。如果没有参数，则返回 -Infinity。如果有某个参数为 NaN，或是不能转换成数字的非数字值，则返回 NaN。

    ```javascript
    console.log(Math.max(1.4,-1.4,0,'111')); // 111
    console.log(Math.max(1.4,-1.4,0,{},[],undefined,null,'a')); // NaN 
    console.log(Math.max()); // -Infinity
    ```

- `Math.min(n1,n2,n3,...,nX)` 方法可返回参数中带有较小的值的那个数。如果没有参数，则返回 Infinity。如果有某个参数为 NaN，或是不能转换成数字的非数字值，则返回 NaN。

    ```javascript
    console.log(Math.min(1.4,-1.4,0,'111')); // -1.4
    console.log(Math.min(1.4,-1.4,0,{},[],undefined,null,'a')); // NaN 
    console.log(Math.min()); // Infinity
    ```

- `Math.pow(x, y)` 方法返回 x 的 y 次幂。x必需底数且是数字。x必需幂数且是数字。

    ```javascript
    返回 4 的 3 次幂 (4*4*4):
    console.log(Math.pow(4,3)); // 64
    console.log(Math.pow()); // NaN
    console.log(Math.pow({}, {})); // NaN
    console.log(Math.pow(undefined, undefined)); // NaN
    console.log(Math.pow(null, null)); //1
    console.log(Math.pow([],[])); // 1
    ```

- `Math.random(x)` 方法可返回介于 0（包含） ~ 1（不包含） 之间的一个随机数。

    ```javascript
    console.log(Math.random()); // 0.496602693723625
    ```

- `Math.round(x)` 方法可把一个数字舍入为最接近的整数。

    ```javascript
    console.log(Math.round(2.5)); // 3
    console.log(Math.round(-2.5)); // -2
    console.log(Math.round(2.45)); // 2
    console.log(Math.round(-2.45)); // -2
    ```

- `Math.sign(x)` 方法用来判断一个数到底是正数、负数、还是零。对于非数值，会先将其转换为数值。  **<font color=red>ES6支持</font>**
   
    > 它会返回五种值。
    
        参数为正数，返回+1；
        参数为负数，返回-1；
        参数为 0，返回0；
        参数为-0，返回-0;
        其他值，返回NaN。

    ```javascript
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

- `Math.sin(x)` 方法返回参数 x 的正弦值。值在 -1.0 到 1.0 之间。

    ```javascript
    console.log(Math.sin()); // NaN
    console.log(Math.sin(0)); // 0
    console.log(Math.sin({})); // NaN
    console.log(Math.sin(undefined)); // NaN
    console.log(Math.sin(null)); // 0
    console.log(Math.sin([])); // 0
    ```

- `Math.sinh(x)` 返回x的双曲正弦。 **<font color=red>ES6支持</font>**

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

- `Math.sqrt(x)` 方法可返回一个数的平方根。x必须是大于等于 0 的数。如果 x 小于 0，则返回 NaN。

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

- `Math.tan(x)` 方法可返回一个表示某个角的正切的数字。x是一个以弧度表示的角。将角度乘以 0.017453293 （2PI/360）即可转换为弧度。

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

- `Math.tanh(x)` 返回x的双曲正切。 **<font color=red>ES6支持</font>**

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

- `Math.trunc(x)` 方法用于去除一个数的小数部分，返回整数部分。 **<font color=red>ES6支持</font>**  

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

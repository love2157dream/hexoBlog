---
title: JavaScript对象介绍之Number对象
date: 2017-12-14 08:41:55
tags: 
    - JavaScript
    - Number对象
categories: JavaScript
---

# Number对象属性

- `Number.EPSILON ` 常量，它表示 1 与大于 1 的最小浮点数之间的差。 **<font color=red>ES6支持</font>**

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

    //Number.EPSILON可以用来设置“能够接受的误差范围”。比如，误差范围设为 2 的-50 次方（即Number.EPSILON * Math.pow(2, 2)），
    //即如果两个浮点数的差小于这个值，我们就认为这两个浮点数相等。
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

- `Number.MAX_SAFE_INTEGER` 常量，返回安全整数的最大值  **<font color=red>ES6支持</font>**

    ```javascript
    console.log(Number.MAX_SAFE_INTEGER); // 9007199254740991
    ```

- `Number.MAX_VALUE` 静态只读属性是 JavaScript 中可表示的最大的数。它的近似值为 1.7976931348623157 x 10308。大于MAX_VALUE的数表示无穷大。

    ```javascript
    console.log(Number.MAX_VALUE); // 1.7976931348623157e+308
    //MAX_VALUE 是 Javascript Number对象的静态属性，只能通过 Number.MAX_VALUE 调用。.
    // 使用自定义的Number x（x.MAX_VALUE ） 将无法获取 MAX_VALUE 属性:
    var x = 100;
    console.log(x.MAX_VALUE); // undefined
    ```

- `Number.MIN_SAFE_INTEGER` 常量，返回安全整数的最小值  **<font color=red>ES6支持</font>**

    ```javascript
    console.log(Number.MIN_SAFE_INTEGER); // -9007199254740991
    ```

- `Number.MIN_VALUE` 静态只读属性是 JavaScript 中可表示的最小的数（接近 0 ，但不是负数）。它的近似值为 5 x 10-324。
    > 注意： 比 MIN_VALUE 属性小的数将用 0 表示。
    > 注意： MIN_VALUE 是 JavaScript 最接近0的数,不是负值，负值属性为 MAX_NUMBER。

    ```javascript
    console.log(Number.MIN_VALUE); // 5e-324
    //MIN_VALUE 是 Javascript Number对象的静态属性，只能通过 Number.MIN_VALUE 调用。.
    // 使用自定义的Number x（x.MIN_VALUE ） 将无法获取 MIN_VALUE 属性:
    var x = 100;
    console.log(x.MIN_VALUE); // undefined
    ```

- `Number.NEGATIVE_INFINITY ` 静态只读属性表示负无穷大。小于 Number.MIN_VALUE 的值。

    ```javascript
    console.log(Number.NEGATIVE_INFINITY); // -Infinity
    // NEGATIVE_INFINITY 是 JavaScript Number 对象的静态变量。
    // 调用方法为：Number.NEGATIVE_INFINITY.
    // 使用 自定义 Number对象 x 调用该属性（x.NEGATIVE_INFINITY）将返回 undefined:
    var x = 100;
    console.log(x.NEGATIVE_INFINITY); // undefined
    ```

- `Number.NaN` 静态只读属性是代表非数字值的特殊值。该属性用于指示某个值不是数字。
    > 可以把 Number 对象设置为该值，来指示其不是数字值。
    > 提示： 请使用 isNaN() 全局函数来判断一个值是否是 NaN 值。

    ```javascript
    console.log(Number.NaN); // NaN
    ```

- `Number.POSITIVE_INFINITY ` 静态只读属性表示正无穷大。小于 Number.MAX_VALUE  的值。

    ```javascript
    console.log(Number.POSITIVE_INFINITY); // -Infinity
    // POSITIVE_INFINITY 是 JavaScript Number 对象的静态变量。
    // 调用方法为：Number.POSITIVE_INFINITY.
    // 使用 自定义 Number对象 x 调用该属性（x.POSITIVE_INFINITY）将返回 undefined:
    var x = 100;
    console.log(x.POSITIVE_INFINITY); // undefined
    // 
    ```

- `Number.prototype` 属性允许您向对象添加属性和方法。
    > 当构造一个属性, 所有的 Number 对象将被添加上该属性及值。
    > 当构造一个方法时，所有的 Number 对象都会有这个方法。
    > 注意： Number.prototype 不允许引用一个单独的 Number 对象，但是可以使用 Number() 对象。
    > 注意：prototype 型是一个全局对象的构造函数，可用于所有的JavaScript对象

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

# Number对象方法

- `Number.isFinite(x)` 用来检查一个数值是否为有限的（finite）。**<font color=red>ES6支持</font>**

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


- `Number.isNaN()` 用来检查一个值是否为NaN。 **<font color=red>ES6支持</font>**

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

- `isNaN()和isFinite()`与传统的全局方法isFinite()和isNaN()的区别在于，传统方法先调用Number()将非数值的值转为数值，再进行判断。
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

- `Number.isInteger()` 用来判断一个值是否为整数。需要注意的是，在 JavaScript 内部，整数和浮点数是同样的储存方法，所以 3 和 3.0 被视为同一个值。 **<font color=red>ES6支持</font>**

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

- `Number.isSafeInteger()` 用来判断一个整数是否落在这个范围之内。准确表示的整数范围在-2^53到2^53之间（不含两个端点），超过这个范围，无法精确表示这个值。 **<font color=red>ES6支持</font>**

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

- `Number.parseInt()` 将字符串转换为整数并返回。ES6 将全局方法parseInt()移植到Number对象上面，行为完全保持不变。这样做的目的，是逐步减少全局性方法，使得语言逐步模块化。 **<font color=red>ES6支持</font>**

    ```javascript
    // ES5的写法
    console.log(parseInt('12.34')); // 12

    // ES6的写法
    console.log(Number.parseInt('12.34')); // 12

    console.log(Number.parseFloat === parseFloat); // true
    ```


- `Number.parseFloat()` 将字符串转换为浮点数并返回。ES6 将全局方法parseFloat()移植到Number对象上面，行为完全保持不变。这样做的目的，是逐步减少全局性方法，使得语言逐步模块化。 **<font color=red>ES6支持</font>**

    ```javascript
    // ES5的写法
    console.log(parseFloat('123.45#')); // 123.45

    // ES6的写法
    console.log(Number.parseFloat('123.45#')); // 123.45

    console.log(Number.parseFloat === parseFloat); // true
    ```

- `Number.prototype.toExponential(x)` 方法把数字转换为指数计数法表示的字符串，并具有指定的小数位数。x是可选/Number类型,指定保留的小数位数。
    
    > 如果没有提供x参数，则toExponential()方法将返回足够多位数字，以便唯一指定该数字。
    > 如果提供了参数，则参数x必须介于 [0, 20] 之间，否则将报错。
    > 如果数字本身的小数位数大于参数x，则根据第x + 1位小数上的值进行四舍五入。

    ```javascript
    console.log(Number(423.536).toExponential()); // 4.23536e+2
    console.log(Number(562345.12456).toExponential(3)); // 5.623e+5
    console.log(Number(-2651.10).toExponential(4));  // -2.6511e+3
    console.log(Number(4564561.12457).toExponential(0)); // 5e+6
    console.log(Number(231).toExponential(5)); // 2.31000e+2
    ```

- `Number.prototype.toFixed(x)` 方法可把 Number 四舍五入为指定小数位数的数字。x值必需。
   
    > 如果没有提供x参数或其参数值为undefined，则x参数将默认为0。
    > 如果提供了参数，则参数x必须介于 [0, 20] 之间，否则将报错。
    > 如果数字本身的小数位数多于参数x，则根据第x + 1位小数上的值进行四舍五入。

```javascript
console.log(Number(423.536).toFixed() ); // 424
console.log(Number(562345.12456).toFixed(3)); // 562345.125
console.log(Number(-2651.10).toFixed(4)); // -2651.1000
console.log(Number(4564561.12457).toFixed(0)); // 4564561
console.log(Number(231).toFixed(5)); // 231.00000
console.log(Number(1232).toFixed(undefined)); // 1232
console.log(Number(123124234).toFixed(50)); // Uncaught RangeError: toFixed() digits argument must be between 0 and 20
```

- `Number.prototype.toPrecision(x)` 方法可在对象的值超出指定位数时将其转换为指数计数法。x值可选/Number类型指定有效数字的位数。

    > 如果没有提供x参数或其值为undefined，则将转而调用toString()方法进行处理。而不是把数字转换成十进制的值。
    > 如果提供了参数，则参数x必须介于 1 ~ 21 之间（且包括 1 和 21）即[1, 21] 之间，否则将报错。
    > 如果数字的有效位数大于x，将会根据第x + 1位的有效数字进行四舍五入。

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

- `Number.prototype.toString(x)` 把数字转换为字符串,x值可选/Number类型指定的基数(进制数)，默认为10。
    
    > 规定表示数字的基数，使 2 ~ 36 之间的整数。若省略该参数，则使用基数 10。但是要注意，如果该参数是 10 以外的其他值，则 ECMAScript 标准允许实现返回任意值。
    > 2 - 数字以二进制值显示
    > 8 - 数字以八进制值显示
    > 16 - 数字以十六进制值显示

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


- `Number.prototype.valueOf() ` 返回一个 Number 对象的基本数字值。可以字符串返回数字。

    ```javascript
    console.log(Number(1024).valueOf()); // 1024
    ```


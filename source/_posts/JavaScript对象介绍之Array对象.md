---
title: JavaScript对象介绍之Array对象
date: 2017-12-14 08:42:14
tags: 
    - JavaScript
    - Array对象
categories: JavaScript
---

# 扩展运算符

含义：扩展运算符（spread）是三个点（...）。它好比 rest 参数的逆运算，将一个数组转为用逗号分隔的参数序列。

    ```javascript
    console.log(...[1, 2, 3]); // 1 2 3
    console.log(1, ...[2, 3, 4], 5) // 1 2 3 4 5
    console.loog([...document.querySelectorAll('div')]);

    // 函数调用
    function push(array, ...items) {
      array.push(...items);
    }

    function add(x, y) {
      return x + y;
    }

    const numbers = [4, 38];
    add(...numbers) // 42

    // 复制数组
    const a1 = [1, 2];
    // 写法一
    const a2 = [...a1];
    // 写法二
    const [...a2] = a1;

    // ES5只能通过方法复制数组
    const a1 = [1, 2];
    const a2 = a1.concat();

    a2[0] = 2;
    a1 // [1, 2]

    // 合并数组
    // ES5
    [1, 2].concat(more)
    // ES6
    [1, 2, ...more]

    var arr1 = ['a', 'b'];
    var arr2 = ['c'];
    var arr3 = ['d', 'e'];

    // ES5的合并数组
    arr1.concat(arr2, arr3);
    // [ 'a', 'b', 'c', 'd', 'e' ]

    // ES6的合并数组
    [...arr1, ...arr2, ...arr3]
    // [ 'a', 'b', 'c', 'd', 'e' ]
    ```










# Array对象的属性

- `Array.length` 是Array的实例属性。返回或设置一个数组中的元素个数。该值是一个无符号 32-bit 整数，并且总是大于数组最高项的下标。值是一个 0 到 232-1 的整数。

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

# Array对象的方法

- `Array.from(arrayLike, mapFn, thisArg)` 方法用于将两类对象转为真正的数组：伪数组对象（拥有一个 length 属性和若干索引属性的任意对象）
和可遍历（iterable）的对象（包括 ES6 新增的数据结构 Set 和 Map）。  **<font color=red>ES6支持</font>**

    > **语法**
      
        Array.from(arrayLike, mapFn, thisArg)

    > **参数**
    
          arrayLike
            想要转换成数组的伪数组对象或可迭代对象。
          mapFn (可选参数)
            如果指定了该参数，新数组中的每个元素会执行该回调函数。
          thisArg (可选参数)
            可选参数，执行回调函数 mapFn 时 this 对象。
    
    > **返回值**
    
        一个新的数组实例

    ```javascript
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

- `Array.isArray(obj)` 用于确定obj是否是一个 Array,如果对象是 Array，则为true; 否则为false。当检测Array实例时, Array.isArray 优于 instanceof,因为Array.isArray能检测iframes.

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

- `Array.of(element0[, element1[, ...[, elementN]]])`  方法创建一个具有可变数量参数的新数组实例，而不考虑参数的数量或类型。 **<font color=red>ES6支持</font>**

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

    // 或者

    function ArrayOf(){
      return [].slice.call(arguments);
    }
    ```

- `Array.prototype.concat()`  方法用于合并两个或多个数组。此方法不会更改现有数组，而是返回一个新数组。

    > **语法**
    
        ar new_array = old_array.concat(value1[, value2[, ...[, valueN]]])
    
    > **参数**
          
        valueN
            将数组和/或值连接成新数组。详情请参阅下文描述。
        返回值
            新的 Array 实例。

    > **描述**
      
        concat方法创建一个新的数组，它由被调用的对象中的元素组成，每个参数的顺序依次是该参数的元素（如果参数是数组）或参数本身（如果参数不是数组）。
        它不会递归到嵌套数组参数中。concat方法不会改变this或任何作为参数提供的数组，而是返回一个浅拷贝，它包含与原始数组相结合的相同元素的副本。 
        原始数组的元素将复制到新数组中，如下所示：
        对象引用（而不是实际对象）：concat将对象引用复制到新数组中。 原始数组和新数组都引用相同的对象。 
        也就是说，如果引用的对象被修改，则更改对于新数组和原始数组都是可见的。 这包括也是数组的数组参数的元素。
        数据类型如字符串，数字和布尔（不是String，Number 和 Boolean 对象）：concat将字符串和数字的值复制到新数组中。
        注意：数组/值在连接时保持不变。此外，对于新数组的任何操作（仅当元素不是对象引用时）都不会对原始数组产生影响，反之亦然。
     
    ```javascript

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

    > **语法**
        
        arr.copyWithin(target)
        arr.copyWithin(target, start)
        arr.copyWithin(target, start, end)
        arr.copyWithin(目标索引, [源开始索引], [结束源索引])

    > **参数**
      
        target  目标索引 
            0 为基底的索引，复制序列到该位置。如果是负数，target 将从末尾开始计算。
            如果 target 大于等于 arr.length，将会不发生拷贝。如果 target 在 start 之后，复制的序列将被修改以符合 arr.length。
        start  [源开始索引]
            0 为基底的索引，开始复制元素的起始位置。如果是负数，start 将从末尾开始计算。
            如果 start 被忽略，copyWithin 将会从0开始复制。
        end  [ 结束源索引]
            0 为基底的索引，开始复制元素的结束位置。copyWithin 将会拷贝到该位置，但不包括 end 这个位置的元素。如果是负数， end 将从末尾开始计算。
            如果 end 被忽略，copyWithin 将会复制到 arr.length。
    
    > **返回值**
      
      改变了的数组。

    ```javascript
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

- `Array.prototype.entries()` 方法返回一个新的Array Iterator对象，该对象包含数组中每个索引的键/值对。对键值对的遍历。 **<font color=red>ES6支持</font>**

    ```javascript
    var arr = ["a", "b", "c"];
    var iterator = arr.entries(); // undefined

    console.log(iterator); // Array Iterator {}

    console.log(iterator.next().value); // [0, "a"]
    console.log(iterator.next().value);  // [1, "b"]
    console.log(iterator.next().value);  // [2, "c"]
    ```

- `Array.prototype.every(callback[, thisArg])`  方法测试数组的所有元素是否都通过了指定函数的测试。

    > **语法**
        
        arr.every(callback[, thisArg])
    
    > **参数**
        
        callback    用来测试每个元素的函数。
        thisArg 执行 callback 时使用的 this 值。
    
    > **描述**
        
        every 方法为数组中的每个元素执行一次 callback 函数，直到它找到一个使 callback 返回 false（表示可转换为布尔值 false 的值）的元素。
        如果发现了一个这样的元素，every 方法将会立即返回 false。否则，callback 为每一个元素返回 true，every 就会返回 true。
        callback 只会为那些已经被赋值的索引调用。不会为那些被删除或从来没被赋值的索引调用。
        callback 被调用时传入三个参数：元素值，元素的索引，原数组。
        如果为 every 提供一个 thisArg 参数，则该参数为调用 callback 时的 this 值。如果省略该参数，则 callback 被调用时的 this 值，
        在非严格模式下为全局对象，在严格模式下传入 undefined。every 不会改变原数组。
        every 遍历的元素范围在第一次调用 callback 之前就已确定了。在调用 every 之后添加到数组中的元素不会被 callback 访问到。
        如果数组中存在的元素被更改，则他们传入 callback 的值是 every 访问到他们那一刻的值。那些被删除的元素或从来未被赋值的元素将不会被访问到。

    ```javascript
    // 例子：检测所有数组元素的大小
    // 下例检测数组中的所有元素是否都大于 10。

    function isBigEnough(element, index, array) {
      return (element >= 10);
    }
    var passed = [12, 5, 8, 130, 44].every(isBigEnough);
    console.log(passed); // passed is false
    passed = [12, 54, 18, 130, 44].every(isBigEnough);
    console.log(passed); // passed is true
    ```

- `Array.prototype.fill()` 方法用一个固定值填充一个数组中从起始索引到终止索引内的全部元素。

    > **语法**
      
        arr.fill(value) 
        arr.fill(value, start) 
        arr.fill(value, start, end)
    
    > **参数**
        
        value 用来填充数组元素的值。
        start 可选 起始索引，默认值为0。
        end 可选 终止索引，默认值为 this.length。
    
    > **返回值**
        
        修改后的数组。

    > **描述**
        
        具体要填充的元素区间是 [start, end) , 一个半开半闭区间.
        fill 方法接受三个参数 value, start 以及 end. start 和 end 参数是可选的, 其默认值分别为 0 和 this 对象的 length 属性值.
        如果 start 是个负数, 则开始索引会被自动计算成为 length+start, 其中 length 是 this 对象的 length 属性值. 
        如果 end 是个负数, 则结束索引会被自动计算成为 length+end.
        fill 方法故意被设计成通用方法,它需要this值是个对象，类数组对象调用会报错
        fill 方法是个可变方法, 它会改变调用它的 this 对象本身, 然后返回它, 而并不是返回一个副本.

    ```javascript
    console.log([1, 2, 3].fill(4));            // [4, 4, 4]
    console.log([1, 2, 3].fill(4, 1));         // [1, 4, 4]
    console.log([1, 2, 3].fill(4, 1, 2));      // [1, 4, 3]
    console.log([1, 2, 3].fill(4, 1, 1));      // [1, 2, 3]
    console.log([1, 2, 3].fill(4, -3, -2));    // [4, 2, 3]
    console.log([1, 2, 3].fill(4, NaN, NaN));  // [1, 2, 3]
    console.log(Array(3).fill(4));            // [4, 4, 4]
    console.log([].fill.call({length: 3}, 4)); // {0: 4, 1: 4, 2: 4, length: 3}
    ```

- `Array.prototype.filter()` 检测数值元素，并返回符合条件所有元素的数组。

    > **语法**
        
        var new_array = arr.filter(callback[, thisArg])
    
    > **参数**
        
        callback 用来测试数组的每个元素的函数。调用时使用参数 (element, index, array)。
                返回true表示保留该元素（通过测试），false则不保留。
        thisArg 可选。执行 callback 时的用于 this 的值。
    
    > **返回值**
         
          一个新的通过测试的元素的集合的数组
    > **ES6**
        
        let [...spraed]= [12, 5, 8, 130, 44];
        等同于：let spraed = 浅克隆([12, 5, 8, 130, 44])
    
    > **描述**
        
        filter 为数组中的每个元素调用一次 callback 函数，并利用所有使得 callback 返回 true 或 等价于 true 的值 的元素创建一个新数组。
        callback 只会在已经赋值的索引上被调用，对于那些已经被删除或者从未被赋值的索引不会被调用。
        那些没有通过 callback 测试的元素会被跳过，不会被包含在新数组中。
        callback 被调用时传入三个参数：元素的值, 元素的索引, 被遍历的数组
        如果为 filter 提供一个 thisArg 参数，则它会被作为 callback 被调用时的 this 值。
        否则，callback 的 this 值在非严格模式下将是全局对象，严格模式下为 undefined。
        filter 不会改变原数组。
        filter 遍历的元素范围在第一次调用 callback 之前就已经确定了。在调用 filter 之后被添加到数组中的元素不会被 filter 遍历到。
        如果已经存在的元素被改变了，则他们传入 callback 的值是 filter 遍历到它们那一刻的值。被删除或从来未被赋值的元素不会被遍历到。

    ```javascript
    // 筛选排除掉所有的小值
    function isBigEnough(value) {
      return value >= 10;
    }

    var filtered = [12, 5, 8, 130, 44].filter(isBigEnough);

    console.log(filtered); // filtered is [12, 130, 44]

    // ES6 way

    const isBigEnough = value => value >= 10;
    let [...spraed]= [12, 5, 8, 130, 44];
    let filtered = spraed.filter(isBigEnough);

    console.log(filtered); // filtered is [12, 130, 44]
    ```

- `Array.prototype.find()`  方法返回数组中满足提供的测试函数的第一个元素的值。否则返回 undefined。

    > **语法**
        
        arr.find(callback[, thisArg])
    
    > **参数**
        
        callback 在数组每一项上执行的函数，接收 3 个参数：
            element 当前遍历到的元素。
            index 当前遍历到的索引。
            array 数组本身。
        thisArg  可选，指定 callback 的 this 参数。
    
    > **返回值**
        
        当某个元素通过 callback 的测试时，返回数组中的一个值，否则返回 undefined。

    > **描述**
        
        find 方法对数组中的每一项元素执行一次 callback 函数，直至有一个 callback 返回 true。
        当找到了这样一个元素后，该方法会立即返回这个元素的值，否则返回 undefined。
        注意 callback 函数会为数组中的每个索引调用即从 0 到 lengh - 1，而不仅仅是那些被赋值的索引，
        这意味着对于稀疏数组来说，该方法的效率要低于那些只遍历有值的索引的方法。
        callback 函数带有3个参数：当前元素的值、当前元素的索引，以及数组本身。
        如果提供了 thisArg 参数，那么它将作为每次 callback 函数执行时的上下文对象，否则上下文对象为 undefined。
        find 方法不会改变数组。
        在第一次调用 callback 函数时会确定元素的索引范围，因此在 find 方法开始执行之后添加到数组的新元素将不会被 callback 函数访问到。
        如果数组中一个尚未被callback函数访问到的元素的值被callback函数所改变，那么当callback函数访问到它时，
        它的值是将是根据它在数组中的索引所访问到的当前值。被删除的元素仍旧会被访问到。

    ```javascript

    function isBigEnough(element) {
      return element >= 15;
    }

    console.log([12, 5, 8, 130, 44].find(isBigEnough)); // 130

    // 用对象的属性查找数组里的对象
    var inventory = [
        {name: 'apples', quantity: 2},
        {name: 'bananas', quantity: 0},
        {name: 'cherries', quantity: 5}
    ];

    function findCherries(fruit) { 
        return fruit.name === 'cherries';
    }

    console.log(inventory.find(findCherries)); // { name: 'cherries', quantity: 5 }

    // 寻找数组中的质数
    // 下面的例子展示了如何从一个数组中寻找质数（如果找不到质数则返回undefined）

    function isPrime(element, index, array) {
      var start = 2;
      while (start <= Math.sqrt(element)) {
        if (element % start++ < 1) {
          return false;
        }
      }
      return element > 1;
    }

    console.log([4, 6, 8, 12].find(isPrime)); // undefined, not found
    console.log([4, 5, 8, 12].find(isPrime)); // 5

    // 当在回调中删除数组中的一个值时，当访问到这个位置时，其传入的值时 undefiend：

    // Declare array with no element at index 2, 3 and 4
    var a = [0,1,,,,5,6];

    // Shows all indexes, not just those that have been assigned values
    a.find(function(value, index) {
      console.log('Visited index ' + index + ' with value ' + value); 
    });

    // Shows all indexes, including deleted
    a.find(function(value, index) {

      // Delete element 5 on first iteration
      if (index == 0) {
        console.log('Deleting a[5] with value ' + a[5]);
        delete a[5];
      }
      // Element 5 is still visited even though deleted
      console.log('Visited index ' + index + ' with value ' + value); 
    });
    ```

- `Array.prototype.findIndex()`  返回符合传入测试（函数）条件的数组元素索引。

    > **语法**
        
        arr.findIndex(callback[, thisArg])
    
    > **参数**
       
       callback
            针对数组中的每个元素, 都会执行该回调函数, 执行时会自动传入下面三个参数:
            element 当前元素。
            index 当前元素的索引。
            array 调用findIndex的数组。
        thisArg
            可选。执行callback时作为this对象的值.
   
   > **描述**
        
        findIndex方法对数组中的每个数组索引0..length-1（包括）执行一次callback函数，直到找到一个callback函数返回真实值（强制为true）的值。
        如果找到这样的元素，findIndex会立即返回该元素的索引。如果回调从不返回真值，或者数组的length为0，则findIndex返回-1。 
        与某些其他数组方法（如Array#some）不同，在稀疏数组中，即使对于数组中不存在的条目的索引也会调用回调函数。
        回调函数调用时有三个参数：元素的值，元素的索引，以及被遍历的数组。
        如果一个 thisArg 参数被提供给 findIndex, 它将会被当作this使用在每次回调函数被调用的时候。如果没有被提供，将会使用undefined。
        findIndex不会修改所调用的数组。
        在第一次调用callback函数时会确定元素的索引范围，因此在findIndex方法开始执行之后添加到数组的新元素将不会被callback函数访问到。
        如果数组中一个尚未被callback函数访问到的元素的值被callback函数所改变，那么当callback函数访问到它时，
        它的值是将是根据它在数组中的索引所访问到的当前值。被删除的元素不会被访问到。

    ```javascript
    function isBigEnough(element) {
      return element >= 15;
    }

    console.log([12, 5, 8, 130, 44].findIndex(isBigEnough));  // 3

    // 查找数组中素数的元素的索引（如果不存在素数，则返回-1）。

    function isPrime(element, index, array) {
      var start = 2;
      while (start <= Math.sqrt(element)) {
        if (element % start++ < 1) {
          return false;
        }
      }
      return element > 1;
    }

    console.log([4, 6, 8, 12].findIndex(isPrime)); // -1, not found
    console.log([4, 6, 7, 12].findIndex(isPrime)); // 2
    ```

- `Array.prototype.forEach()` 方法对数组的每个元素执行一次提供的函数

    > **语法**
    
        ```javascript
          array.forEach(callback(currentValue, index, array){
              //do something
          }, this)
          array.forEach(callback[, thisArg])
        ```

    > **参数**
        
        callback
            为数组中每个元素执行的函数，该函数接收三个参数：
            currentValue(当前值)   数组中正在处理的当前元素。
            index(索引)   数组中正在处理的当前元素的索引。
            array  forEach()方法正在操作的数组。
        thisArg可选
            可选参数。当执行回调 函数时用作this的值(参考对象)。
        返回值
            undefined.

    > **描述**
        
        forEach 方法按升序为数组中含有效值的每一项执行一次callback 函数，那些已删除（使用delete方法等情况）
        或者未初始化的项将被跳过（但不包括那些值为 undefined 的项）（例如在稀疏数组上）。
        callback 函数会被依次传入三个参数： 数组当前项的值 , 数组当前项的索引 , 数组对象本身
        如果给forEach传递了thisArg参数，当调用时，它将被传给callback 函数，作为它的this值。
        否则，将会传入 undefined 作为它的this值。callback函数最终可观察到this值，这取决于 函数观察到this的常用规则。
        forEach 遍历的范围在第一次调用 callback 前就会确定。调用forEach 后添加到数组中的项不会被 callback 访问到。
        如果已经存在的值被改变，则传递给 callback 的值是 forEach 遍历到他们那一刻的值。已删除的项不会被遍历到。
        如果已访问的元素在迭代时被删除了(例如使用 shift()) ，之后的元素将被跳过 - 参见下面的示例。
        forEach() 为每个数组元素执行callback函数；不像map() 或者reduce() ，它总是返回 undefined值，并且不可链式调用。
        典型用例是在一个链的最后执行副作用。
        注意： 没有办法中止或者跳出 forEach 循环，除了抛出一个异常。如果你需要这样，使用forEach()方法是错误的，你可以用一个简单的循环作为替代。
        如果您正在测试一个数组里的元素是否符合某条件，且需要返回一个布尔值，那么可使用 Array.every 或 Array.some。
        如果可用，新方法 find() 或者findIndex() 也可被用于真值测试的提早终止。

    ```javascript
    // 下面的代码会为每一个数组元素输出一行记录：

    function logArrayElements(element, index, array) {
        console.log("a[" + index + "] = " + element);
    }

    // 注意索引2被跳过了，因为在数组的这个位置没有项
    [2, 5, ,9].forEach(logArrayElements);

    // a[0] = 2
    // a[1] = 5
    // a[3] = 9

    [2, 5,"" ,9].forEach(logArrayElements);
    // a[0] = 2
    // a[1] = 5
    // a[2] = 
    // a[3] = 9

    [2, 5, undefined ,9].forEach(logArrayElements);
    // a[0] = 2
    // a[1] = 5
    // a[2] = undefined
    // a[3] = 9


    let xxx;
    // undefined

    [2, 5, xxx ,9].forEach(logArrayElements);
    // a[0] = 2
    // a[1] = 5
    // a[2] = undefined
    // a[3] = 9
     
    // 如果数组在迭代时被修改了，则其他元素会被跳过。
    // 下面的例子输出"one", "two", "four"。当到达包含值"two"的项时，整个数组的第一个项被移除了，这导致所有剩下的项上移一个位置。
    // 因为元素 "four"现在在数组更前的位置，"three"会被跳过。 forEach()不会在迭代之前创建数组的副本。

    var words = ["one", "two", "three", "four"];
    words.forEach(function(word) {
      console.log(word);
      if (word === "two") {
        words.shift();
      }
    });
    // one
    // two
    // four
    ```

- `Array.prototype.includes()`  方法用来判断一个数组是否包含一个指定的值，如果是返回 true，否则false。  **<font color=red>ES6支持</font>**

    > **语法**
        
        arr.includes(searchElement)
        arr.includes(searchElement, fromIndex)
    
    > **参数**
        
        searchElement 需要查找的元素值。
        fromIndex 可选 从该索引处开始查找 searchElement。如果为负值，则按升序从 array.length + fromIndex 的索引开始搜索。默认为 0。
    
    > **返回值**
        一个 Boolean。

    ```javascript
    [1, 2, 3].includes(2);     // true
    [1, 2, 3].includes(4);     // false
    [1, 2, 3].includes(3, 3);  // false
    [1, 2, 3].includes(3, -1); // true
    [1, 2, NaN].includes(NaN); // true

    // 如果fromIndex 大于等于数组长度 ，则返回 false 。该数组不会被搜索。
    var arr = ['a', 'b', 'c'];
    arr.includes('c', 3);   //false
    arr.includes('c', 100); // false

    // 计算出的索引小于 0
    // 如果 fromIndex 为负值，计算出的索引将作为开始搜索searchElement的位置。如果计算出的索引小于 0，则整个数组都会被搜索。
    // 数组长度是3
    // fromIndex 是 -100
    // computed index 是 3 + (-100) = -97

    var arr = ['a', 'b', 'c'];
    arr.includes('a', -100); // true
    arr.includes('b', -100); // true
    arr.includes('c', -100); // true

    // includes() 作为一个通用方法
    // includes() 方法有意设计为通用方法。它不要求this值是数组对象，所以它可以被用于其他类型的对象 (比如类数组对象)。
    // 下面的例子展示了 在函数的arguments对象上调用的includes() 方法。

    (function() {
      console.log([].includes.call(arguments, 'a')); // true
      console.log([].includes.call(arguments, 'd')); // false
    })('a','b','c');
    ```

- `Array.prototype.indexOf()` 方法返回在数组中可以找到一个给定元素的第一个索引，如果不存在，则返回-1。

    > **语法**
        
        arr.indexOf(searchElement)
        arr.indexOf(searchElement[, fromIndex = 0])
    
    > **参数**
        
        searchElement
            要查找的元素
        fromIndex
            开始查找的位置。如果该索引值大于或等于数组长度，意味着不会在数组里查找，返回-1。
            如果参数中提供的索引值是一个负值，则将其作为数组末尾的一个抵消，即-1表示从最后一个元素开始查找，-2表示从倒数第二个元素开始查找 ，以此类推。 
            注意：如果参数中提供的索引值是一个负值，仍然从前向后查询数组。如果抵消后的索引值仍小于0，则整个数组都将会被查询。其默认值为0.
    
    > **返回值**
        
        首个被找到的元素在数组中的索引位置; 若没有找到则返回 -1

    ```javascript
    // 使用indexOf方法确定多个值在数组中的位置。
    var array = [2, 5, 9];
    array.indexOf(2);     // 0
    array.indexOf(7);     // -1
    array.indexOf(9, 2);  // 2
    array.indexOf(2, -1); // -1
    array.indexOf(2, -3); // 0

    // 找出指定元素出现的所有位置
    var indices = [];
    var array = ['a', 'b', 'a', 'c', 'a', 'd'];
    var element = 'a';
    var idx = array.indexOf(element);
    while (idx != -1) {
      indices.push(idx);
      idx = array.indexOf(element, idx + 1);
    }
    console.log(indices); // [0, 2, 4]

    // 判断一个元素是否在数组里，不在则更新数组
    function updateVegetablesCollection (veggies, veggie) {
        if (veggies.indexOf(veggie) === -1) {
            veggies.push(veggie);
            console.log('New veggies collection is : ' + veggies);
        } else if (veggies.indexOf(veggie) > -1) {
            console.log(veggie + ' already exists in the veggies collection.');
        }
    }

    var veggies = ['potato', 'tomato', 'chillies', 'green-pepper'];

    // New veggies collection is : potato,tomato,chillies,green-papper,spinach
    updateVegetablesCollection(veggies, 'spinach'); 
    // spinach already exists in the veggies collection.
    updateVegetablesCollection(veggies, 'spinach');
    ```

- `Array.prototype.join()` 方法将数组（或一个类数组对象）的所有元素连接到一个字符串中。join() 方法，不会改变数组！

    > **语法**

        ```javascript
        str = arr.join()
        // 默认为 ","

        str = arr.join("")
        // 分隔符 === 空字符串 ""

        str = arr.join(separator)
        // 分隔符
        ```

    > **参数**
        
        separator
            指定一个字符串来分隔数组的每个元素。
            如果需要(separator)，将分隔符转换为字符串。
            如果省略()，数组元素用逗号分隔。默认为 ","。
            如果separator是空字符串("")，则所有元素之间都没有任何字符。
    
    > **返回值**
        
        一个所有数组元素连接的字符串。如果 arr.length 为0，则返回空字符串

    > **描述**
        
        所有的数组元素被转换成字符串，再用一个分隔符将这些字符串连接起来。如果元素是undefined 或者null， 则会转化成空字符串。


    ```javascript
    let a = ['Wind', 'Rain', 'Fire'];

    a.join(); 
    // 默认为 ","
    // 'Wind,Rain,Fire'

    a.join(""); 
    // 分隔符 === 空字符串 ""
    // "WindRainFire"

    a.join("-"); 
    // 分隔符 "-"
    // 'Wind-Rain-Fire'

    console.log(a);
    // ['Wind', 'Rain', 'Fire']
    ```

- `Array.prototype.keys()`  方法返回一个新的Array迭代器，它包含数组中每个索引的键。对键名的遍历。  **<font color=red>ES6支持</font>**

    > **语法**
    
        arr.keys()
    
    > **返回值** 
    
        一个新的 Array 迭代器对象。

    ```javascript
    var arr = ["a", "b", "c"];
    var iterator = arr.keys();

    console.log(iterator.next()); // { value: 0, done: false }
    console.log(iterator.next()); // { value: 1, done: false }
    console.log(iterator.next()); // { value: 2, done: false }
    console.log(iterator.next()); // { value: undefined, done: true }

    // 索引迭代器会包含那些没有对应元素的索引
    var arr = ["a", , "c"];
    var sparseKeys = Object.keys(arr);
    var denseKeys = [...arr.keys()];
    console.log(sparseKeys); // ['0', '2']
    console.log(denseKeys);  // [0, 1, 2]
    ```

- `Array.prototype.lastIndexOf()` 方法返回指定元素（也即有效的 JavaScript 值或变量）在数组中的最后一个的索引，如果不存在则返回 -1。从数组的后面向前查找，从 fromIndex 处开始。

    > **语法**
   
        arr.lastIndexOf(searchElement[, fromIndex = arr.length - 1])
    
    > **参数**
        
        searchElement
            被查找的元素。
        fromIndex
            从此位置开始逆向查找。默认为数组的长度减 1，即整个数组都被查找。如果该值大于或等于数组的长度，则整个数组会被查找。
            如果为负值，将其视为从数组末尾向前的偏移。即使该值为负，数组仍然会被从后向前查找。
            如果该值为负时，其绝对值大于数组长度，则方法返回 -1，即数组不会被查找。
   
    > **描述**
        
        lastIndexOf 使用严格相等（strict equality，即 ===）比较 searchElement 和数组中的元素。

    ```javascript
    // 使用 lastIndexOf 定位数组中的值。
    var array = [2, 5, 9, 2];
    var index = array.lastIndexOf(2); // 3
    index = array.lastIndexOf(7); // -1
    index = array.lastIndexOf(2, 3); // 3
    index = array.lastIndexOf(2, 2); // 0
    index = array.lastIndexOf(2, -2); // 0
    index = array.lastIndexOf(2, -1); // 3

    // 查找所有元素
    // 下例使用 lastIndexOf 查找到一个元素在数组中所有的索引（下标），并使用 push 将所有添加到另一个数组中。

    var indices = [];
    var array = ['a', 'b', 'a', 'c', 'a', 'd'];
    var element = 'a';
    var idx = array.lastIndexOf(element);
    while (idx != -1) {
      indices.push(idx);
      idx = (idx > 0 ? array.lastIndexOf(element, idx - 1) : -1);
    }
    console.log(indices); // [4, 2, 0];

    // 注意，必须单独处理 idx == 0 时的情况，因为如果元素是数组中的第一个元素，则总会被查找，忽略了 fromIndex 参数。 
    // 这点和 indexOf 方法不同。（译注：个人觉得这句话解释有问题，idx == 0 时，array.lastIndexOf(element, idx - 1) 会从最后一个元素向前查找，
    // 这样就重复查找，且死循环了，所以要做一个判断，而且已经查找到第一个元素了，就该结束了）。
    ```

- `Array.prototype.map()` 方法创建一个新数组，其结果是该数组中的每个元素都调用一个提供的函数后返回的结果。

    > **语法**

        ```javascript
        let new_array = arr.map(function callback(currentValue, index, array) { 
            // Return element for new_array 
        }[, thisArg])
        ```

    > **参数**
        
        callback
            生成新数组元素的函数，使用三个参数：
                currentValue    callback 的第一个参数，数组中正在处理的当前元素。
                index   callback 的第二个参数，数组中正在处理的当前元素的索引。
                array   callback 的第三个参数，map 方法被调用的数组。
        thisArg
            可选的。执行 callback 函数时 使用的this 值。
    
    > **返回值**
    
        一个新数组，每个元素都是回调函数的结果。

    > **描述**
        
        map 方法会给原数组中的每个元素都按顺序调用一次  callback 函数。callback 每次执行后的返回值（包括 undefined）组合起来形成一个新数组。 
        callback 函数只会在有值的索引上被调用；那些从来没被赋过值或者使用 delete 删除的索引则不会被调用。
        callback 函数会被自动传入三个参数：数组元素，元素索引，原数组本身。
        如果 thisArg 参数有值，则每次 callback 函数被调用的时候，this 都会指向 thisArg 参数上的这个对象。
        如果省略了 thisArg 参数,或者赋值为 null 或 undefined，则 this 指向全局对象 。
        map 不修改调用它的原数组本身（当然可以在 callback 执行时改变原数组）。
        使用 map 方法处理数组时，数组元素的范围是在 callback 方法第一次调用之前就已经确定了。
        在 map 方法执行的过程中：原数组中新增加的元素将不会被 callback 访问到；
        若已经存在的元素被改变或删除了，则它们的传递到 callback 的值是 map 方法遍历到它们的那一时刻的值；而被删除的元素将不会被访问到。
     

    ```javascript
    // ES6
    let numbers = [1, 5, 10, 15];
    let doubles = numbers.map( x => x ** 2);
    // doubles is now [1, 25, 100, 225]
    // numbers is still [1, 5, 10, 15]
    const numbers = [2, 4, 8, 10];
    let halves = numbers.map(x => x / 2);

    let numbers = [1, 4, 9];
    let roots = numbers.map(Math.sqrt);
    // roots is now [1, 2, 3]
    // numbers is still [1, 4, 9]

    // 数组中每个元素的平方根
    var numbers = [1, 4, 9];
    var roots = numbers.map(Math.sqrt);
    // roots的值为[1, 2, 3], numbers的值仍为[1, 4, 9]

    // 将一个包含对象的数组用以创建一个包含新重新格式化对象的新数组。
    var kvArray = [{key: 1, value: 10}, 
                   {key: 2, value: 20}, 
                   {key: 3, value: 30}];

    var reformattedArray = kvArray.map(function(obj) { 
       var rObj = {};
       rObj[obj.key] = obj.value;
       return rObj;
    });

    // reformattedArray 数组为： [{1: 10}, {2: 20}, {3: 30}], 

    // kvArray 数组未被修改: 
    // [{key: 1, value: 10}, 
    //  {key: 2, value: 20}, 
    //  {key: 3, value: 30}]

    // 通常情况下，map 方法中的 callback 函数只需要接受一个参数，就是正在被遍历的数组元素本身。但这并不意味着 map 只给 callback 传了一个参数。
    // 这个思维惯性可能会让我们犯一个很容易犯的错误。

    // 下面的语句返回什么呢:
    ["1", "2", "3"].map(parseInt);
    // 你可能觉的会是[1, 2, 3]
    // 但实际的结果是 [1, NaN, NaN]

    // 通常使用parseInt时,只需要传递一个参数.
    // 但实际上,parseInt可以有两个参数.第二个参数是进制数.
    // 可以通过语句"alert(parseInt.length)===2"来验证.
    // map方法在调用callback函数时,会给它传递三个参数:当前正在遍历的元素, 元素索引, 原数组本身.
    // 第三个参数parseInt会忽视, 但第二个参数不会,也就是说,
    // parseInt把传过来的索引值当成进制数来使用.从而返回了NaN.

    function returnInt(element) {
      return parseInt(element, 10);
    }

    ['1', '2', '3'].map(returnInt); // [1, 2, 3]
    // 意料之中的结果

    // 也可以使用简单的箭头函数，结果同上
    ['1', '2', '3'].map( str => parseInt(str) );

    // 一个更简单的方式:
    ['1', '2', '3'].map(Number); // [1, 2, 3]
    // 与`parseInt` 不同，下面的结果会返回浮点数或指数:
    ['1.1', '2.2e2', '3e300'].map(Number); // [1.1, 220, 3e+300]

    ```

- `Array.prototype.pop()` 方法从数组中删除最后一个元素，并返回该元素的值。此方法更改数组的长度。

    > **语法**
    
        arr.pop()
    
    > **返回值**
    
        从数组中删除的元素(当数组为空时返回undefined)。
    
    > **描述**
    
        pop 方法从一个数组中删除并返回最后一个元素。
        pop 方法有意具有通用性。该方法和 call() 或 apply() 一起使用时，可应用在类似数组的对象上。
        pop方法根据 length属性来确定最后一个元素的位置。
        如果不包含length属性或length属性不能被转成一个数值，会将length置为0，并返回undefined。
        如果你在一个空数组上调用 pop()，它返回  undefined。

    ```javascript
    let myFish = ["angel", "clown", "mandarin", "surgeon"];

    let popped = myFish.pop();

    console.log(myFish); 
    // ["angel", "clown", "mandarin"]

    console.log(popped); 
    // surgeon
    ```

- `Array.prototype.push()` 方法将一个或多个元素添加到数组的末尾，并返回新数组的长度。

    > **语法**
    
        arr.push(element1, ..., elementN)
    
    > **参数**
        
        elementN
            被添加到数组末尾的元素。
    
    > **返回值**
        
        当调用该方法时，新的 length 属性值将被返回。

    > **描述**
        
        push方法将值追加到数组中。
        push 方法有意具有通用性。该方法和 call() 或 apply() 一起使用时，可应用在类似数组的对象上。
        push 方法根据 length 属性来决定从哪里开始插入给定的值。如果 length 不能被转成一个数值，则插入的元素索引为 0，包括 length 不存在时。
        当 length 不存在时，将会创建它。
        唯一的原生类数组（array-like）对象是 Strings，尽管如此，它们并不适用该方法，因为字符串是不可改变的。

    ```javascript
    // 添加元素到数组
    var sports = ["soccer", "baseball"];
    var total = sports.push("football", "swimming");
    console.log(sports); // ["soccer", "baseball", "football", "swimming"]
    console.log(total);   // 4

    // 合并两个数组
    // 该示例使用 apply() 添加第二个数组的所有元素。
    // 注意当第二个数组(如示例中的moreVegs)太大时不要使用这个方法来合并数组，因为事实上一个函数能够接受的参数个数是有限制的。具体可以参考 apply() 。

    var vegetables = ['parsnip', 'potato'];
    var moreVegs = ['celery', 'beetroot'];
    // 将第二个数组融合进第一个数组
    // 相当于 vegetables.push('celery', 'beetroot');
    Array.prototype.push.apply(vegetables, moreVegs);
    console.log(vegetables); 
    // ['parsnip', 'potato', 'celery', 'beetroot']
    // 
    // 
    // 
    ```

- `Array.prototype.reduce()`  将数组元素计算为一个值（从左到右）。

    > **语法**
    
        arr.reduce(callback[, initialValue])
    
    > **参数**
    
        callback
        执行数组中每个值的函数，包含四个参数：
            accumulator
                累加器累加回调的返回值; 它是上一次调用回调时返回的累积值，或initialValue（如下所示）。
            currentValue
                数组中正在处理的元素。
            currentIndex
                数组中正在处理的当前元素的索引。 如果提供了initialValue，则索引号为0，否则为索引为1。
            array
                调用reduce的数组
        initialValue
            [可选] 用作第一个调用 callback的第一个参数的值。 如果没有提供初始值，则将使用数组中的第一个元素。 在没有初始值的空数组上调用 reduce 将报错。
    
    > **返回值**
    
        函数累计处理的结果

    > **描述**
     
        reduce为数组中的每一个元素依次执行callback函数，不包括数组中被删除或从未被赋值的元素，接受四个参数：
        accumulator , currentValue , currentIndex , array
        回调函数第一次执行时，accumulator 和currentValue的取值有两种情况：调用reduce时提供initialValue，accumulator取值为initialValue，
        currentValue取数组中的第一个值；没有提供 initialValue，accumulator取数组中的第一个值，currentValue取数组中的第二个值。
        注意：如果没有提供initialValue，reduce 会从索引1的地方开始执行 callback 方法，跳过第一个索引。如果提供initialValue，从索引0开始。
        如果数组为空且没有提供initialValue，会抛出TypeError 。如果数组仅有一个元素（无论位置如何）并且没有提供initialValue， 
        或者有提供initialValue但是数组为空，那么此唯一值将被返回并且callback不会被执行。
        提供初始值通常更安全，正如下面的例子，如果没有提供initialValue，则可能有三种输出：

    ```javascript
    var maxCallback = ( pre, cur ) => Math.max( pre.x, cur.x );
    var maxCallback2 = ( max, cur ) => Math.max( max, cur );

    // reduce() without initialValue
    [ { x: 22 }, { x: 42 } ].reduce( maxCallback ); // 42
    [ { x: 22 }            ].reduce( maxCallback ); // { x: 22 }
    [                      ].reduce( maxCallback ); // TypeError

    // map/reduce; better solution, also works for empty arrays
    [ { x: 22 }, { x: 42 } ].map( el => el.x )
                            .reduce( maxCallback2, -Infinity );
    ```

    **reduce如何运行**
    假如运行下段代码：

    ```javascript
    [0, 1, 2, 3, 4].reduce(function(accumulator, currentValue, currentIndex, array){
      return accumulator + currentValue;
    });
    ```

    callback 被调用四次，每次调用的参数和返回值如下表：

    | callback  | accumulator | currentValue  | currentIndex  | array | return value | 
    | :-: | :-: | :-: | :-: | :-: | :-: |
    | first call  | 0 | 1 | 1 | [0, 1, 2, 3, 4] | 1 |
    | second call | 1 | 2 | 2 | [0, 1, 2, 3, 4] | 3 |
    | third call  | 3 | 3 | 3 | [0, 1, 2, 3, 4] | 6 |
    | fourth call | 6 | 4 | 4 | [0, 1, 2, 3, 4] | 10 |

    由`reduce`返回的值将是上次回调调用的值（10）。

    你同样可以使用箭头函数的形式，下面的代码会输出跟前面一样的结果
    您还可以提供Arrow Function 代替完整功能。 下面的代码将产生与上面的代码中相同的输出：
    ```javascript
    [0, 1, 2, 3, 4].reduce((prev, curr) => prev + curr );
    ```

    如果你打算提供一个初始值作为reduce方法的第二个参数，以下是运行过程及结果：
    ```javascript
    [0, 1, 2, 3, 4].reduce((accumulator, currentValue, currentIndex, array) => { return accumulator + currentValue; }, 10 );
    ```

    | callback  | accumulator | currentValue  | currentIndex  | array | return value | 
    | :-: | :-: | :-: | :-: | :-: | :-: |
    | first call  | 10  | 0 | 0 | [0, 1, 2, 3, 4] | 10 |
    | second call | 10  | 1 | 1 | [0, 1, 2, 3, 4] | 11 |
    | third call  | 11  | 2 | 2 | [0, 1, 2, 3, 4] | 13 |
    | fourth call | 13  | 3 | 3 | [0, 1, 2, 3, 4] | 16 |
    | fifth call  | 16  | 4 | 4 | [0, 1, 2, 3, 4] | 20 |

    这种情况下`reduce`返回的值是20。


    ```javascript
    var sum = [0, 1, 2, 3].reduce(function (a, b) {
      return a + b;
    }, 0);
    // sum is 6
    // 你也可以写成箭头函数的形式：

    var total = [ 0, 1, 2, 3 ].reduce(
      ( acc, cur ) => acc + cur,
      0
    );

    // 将二维数组转化为一维
    var flattened = [[0, 1], [2, 3], [4, 5]].reduce(
      function(a, b) {
        return a.concat(b);
      },
      []
    );
    // flattened is [0, 1, 2, 3, 4, 5]
    ```

- `Array.prototype.reduceRight()` 方法接受一个函数作为累加器（accumulator）和数组的每个值（从右到左）将其减少为单个值。

    > **语法**
    arr.reduceRight(callback[, initialValue])
    > **参数**
      `callback`
      一个回调函数，用来操作数组中的每个元素，可接受四个参数：
        `previousValue`
        上一次调用回调的返回值，或提供的 `initialValue`
        `currentValue`
        当前被处理的元素
        `index`
        当前处理元素的索引
        `array`
        调用 `reduce` 的数组
      `initialValue`
      可作为第一次调用回调 `callback` 的第一个参数
    > **返回值**
    执行之后的返回值

    > **描述**
    reduceRight 为数组中每个元素调用一次 callback 回调函数，但是数组中被删除的索引或从未被赋值的索引会跳过。
    回调函数接受四个参数：初始值（或上次调用回调的返回值）、当前元素值、当前索引，以及调用 reduce 的数组。
    可以像下面这样调用 reduceRight 的回调函数 callback：  

    ```javascript
    array.reduceRight(function(previousValue, currentValue, index, array) {
        // ...
    });
    ```

    首次调用回调函数时，previousValue 和 currentValue 可以是两个值之一。
    如果调用 reduceRight 时提供了 initialValue 参数，则 previousValue 等于 initialValue，currentValue 等于数组中的最后一个值。
    如果没有提供 initialValue 参数，则 previousValue 等于数组最后一个值， currentValue 等于数组中倒数第二个值。
    如果数组为空，且没有提供 initialValue 参数，将会抛出一个 TypeError 错误。
    如果数组只有一个元素且没有提供 initialValue 参数，或者提供了 initialValue 参数，
    但是数组为空将会直接返回数组中的那一个元素或 initialValue 参数，而不会调用 callback。

    该函数的完整执行过程见下例：

    ```javascript
    [0, 1, 2, 3, 4].reduceRight(function(previousValue, currentValue, index, array) {
        return previousValue + currentValue;
    });
    ```

    回调将会被调用四次，每次调用的参数及返回值如下：

    | | previousValue | currentValue | index | array | return value |
    | :-: | :-: | :-: | :-: | :-: | :-: |
    | first call | 4 | 3 | 3 | [0,1,2,3,4] | 7 |
    | second call | 7  | 2 | 2 | [0,1,2,3,4] | 9 |
    | third call | 9 | 1 | 1 | [0,1,2,3,4] | 10 |
    | fourth call | 10 | 0 | 0 | [0,1,2,3,4] | 10 |

    `reduceRight` 返回值是最后一次调用回调的返回值（10）。

    如果提供了一个 `initialValue` 参数，则结果如下：
    ```javascript
    [0, 1, 2, 3, 4].reduceRight(function(previousValue, currentValue, index, array) {
        return previousValue + currentValue;
    }, 10);
    ```
      
    | | previousValue | currentValue | index | array | return value |
    | :-: | :-: | :-: | :-: | :-: | :-: |
    | first call  | 10 | 4 | 4 | [0,1,2,3,4] | 14 |
    | second call | 14 | 3 | 3 | [0,1,2,3,4] | 17 |
    | third call  | 17 | 2 | 2 | [0,1,2,3,4] | 19 |
    | fourth call | 19 | 1 | 1 | [0,1,2,3,4] | 20 |
    | fifth call  | 20 | 0 | 0 | [0,1,2,3,4] | 20 |

    `reduceRight` 返回值为 20。

    ```javascript
    //求一个数组中所有值的和
    var total = [0, 1, 2, 3].reduceRight(function(a, b) {
        return a + b;
    });
    // total == 6

    //扁平化（flatten）一个元素为数组的数组
    var flattened = [[0, 1], [2, 3], [4, 5]].reduceRight(function(a, b) {
        return a.concat(b);
    }, []);
    // flattened is [4, 5, 2, 3, 0, 1]

    //reduce 与 reduceRight 之间的区别
    var a = ['1', '2', '3', '4', '5']; 
    var left  = a.reduce(function(prev, cur)      { return prev + cur; }); 
    var right = a.reduceRight(function(prev, cur) { return prev + cur; }); 

    console.log(left);  // "12345"
    console.log(right); // "54321"
    ```

    - `Array.prototype.reverse()` 方法将数组中元素的位置颠倒。第一个数组元素成为最后一个数组元素，最后一个数组元素成为第一个。

    ```javascript
    var myArray = ['one', 'two', 'three'];
    myArray.reverse(); 

    console.log(myArray) // ['three', 'two', 'one']
    ```

    - `Array.prototype.shift()` 方法从数组中删除第一个元素，并返回该元素的值。此方法更改数组的长度。如果 length 属性的值为 0 (长度为 0)，则返回 undefined。

    ```javascript
    let myFish = ['angel', 'clown', 'mandarin', 'surgeon'];

    console.log('调用 shift 之前: ' + myFish);
    // "调用 shift 之前: angel,clown,mandarin,surgeon"

    var shifted = myFish.shift(); 

    console.log('调用 shift 之后: ' + myFish); 
    // "调用 shift 之后: clown,mandarin,surgeon" 

    console.log('被删除的元素: ' + shifted); 
    // "被删除的元素: angel"
    ```

- `Array.prototype.slice()` 方法返回一个从开始到结束（不包括结束）选择的数组的一部分浅拷贝到一个新数组对象。原始数组不会被修改。
 
    > **语法**

        ```javascript
        arr.slice(); // [0, end]
        arr.slice(begin); // [begin, end]
        arr.slice(begin, end); // [begin, end)
        ```

    > **参数**
        
        begin 可选
            从该索引处开始提取原数组中的元素（从0开始）。
            如果该参数为负数，则表示从原数组中的倒数第几个元素开始提取，slice(-2)表示提取原数组中的倒数第二个元素到最后一个元素（包含最后一个元素）。
            如果省略 begin，则 slice 从索引 0 开始。
        end可选
            在该索引处结束提取原数组元素（从0开始）。slice会提取原数组中索引从 begin 到 end 的所有元素（包含begin，但不包含end）。
            slice(1,4) 提取原数组中的第二个元素开始直到第四个元素的所有元素 （索引为 1, 2, 3的元素）。
            如果该参数为负数， 则它表示在原数组中的倒数第几个元素结束抽取。 slice(-2,-1)表示抽取了原数组中的倒数第二个元素到最后一个元素（不包含最后一个元素，也就是只有倒数第二个元素）。
            如果 end 被省略，则slice 会一直提取到原数组末尾。
            如果 end 大于数组长度，slice 也会一直提取到原数组末尾。
   
    > **返回值**
    
        一个含有提取元素的新数组

    > **描述**
    
        slice 不修改原数组，只会返回一个浅复制了原数组中的元素的一个新数组。原数组的元素会按照下述规则拷贝：
        如果该元素是个对象引用 （不是实际的对象），slice 会拷贝这个对象引用到新的数组里。两个对象引用都引用了同一个对象。
        如果被引用的对象发生改变，则新的和原来的数组中的这个元素也会发生改变。
        对于字符串、数字及布尔值来说（不是 String、Number 或者 Boolean 对象），slice 会拷贝这些值到新的数组里。
        在别的数组里修改这些字符串或数字或是布尔值，将不会影响另一个数组。
        如果向两个数组任一中添加了新元素，则另一个不会受到影响。
     
    ```javascript
    // 返回现有数组的一部分
    var fruits = ['Banana', 'Orange', 'Lemon', 'Apple', 'Mango'];
    console.log(fruits.slice(1, 3)); //  ['Orange','Lemon']



    // 使用 slice 在下例中, slice从myCar中创建了一个新数组newCar.两个数组都包含了一个myHonda对象的引用. 
    // 当myHonda的color属性改变为purple, 则两个数组中的对应元素都会随之改变.
    // 使用slice方法从myCar中创建一个newCar.
    var myHonda = { color: 'red', wheels: 4, engine: { cylinders: 4, size: 2.2 } };
    var myCar = [myHonda, 2, "cherry condition", "purchased 1997"];
    var newCar = myCar.slice(0, 2);

    // 输出myCar, newCar,以及各自的myHonda对象引用的color属性.
    console.log('myCar = ' + JSON.stringify(myCar));
    console.log('newCar = ' + JSON.stringify(newCar));
    console.log('myCar[0].color = ' + JSON.stringify(myCar[0].color));
    console.log('newCar[0].color = ' + JSON.stringify(newCar[0].color));

    // 改变myHonda对象的color属性.
    myHonda.color = 'purple';
    console.log('The new color of my Honda is ' + myHonda.color);

    //输出myCar, newCar中各自的myHonda对象引用的color属性.
    console.log('myCar[0].color = ' + myCar[0].color);
    console.log('newCar[0].color = ' + newCar[0].color);
    上述代码输出:

    myCar = [{color: 'red', wheels: 4, engine: {cylinders: 4, size: 2.2}}, 2,
           'cherry condition', 'purchased 1997']
    newCar = [{color: 'red', wheels: 4, engine: {cylinders: 4, size: 2.2}}, 2]
    myCar[0].color = red 
    newCar[0].color = red
    The new color of my Honda is purple
    myCar[0].color = purple
    newCar[0].color = purple



    // 类似数组（Array-like）对象
    slice 方法可以用来将一个类数组（Array-like）对象/集合转换成一个数组。你只需将该方法绑定到这个对象上。下述代码中 list 函数中的 arguments 就是一个类数组对象。

    function list() {
      return Array.prototype.slice.call(arguments);
    }

    var list1 = list(1, 2, 3); // [1, 2, 3]
    // 除了使用 Array.prototype.slice.call(arguments)，你也可以简单的使用 [].slice.call(arguments) 来代替。
    // 另外，你可以使用 bind 来简化该过程。

    var unboundSlice = Array.prototype.slice;
    var slice = Function.prototype.call.bind(unboundSlice);

    function list() {
      return slice(arguments);
    }

    var list1 = list(1, 2, 3); // [1, 2, 3]
    ```

- `Array.prototype.some()` 检测数组元素中是否有元素符合指定条件。

    > **语法**
    
        arr.some(callback[, thisArg])
    
    > **参数**
        
        callback 用来测试每个元素的函数。
        thisArg 执行 callback 时使用的 this 值。
    
    > **描述**
    
        some 为数组中的每一个元素执行一次 callback 函数，直到找到一个使得 callback 返回一个“真值”（即可转换为布尔值 true 的值）。
        如果找到了这样一个值，some 将会立即返回 true。否则，some 返回 false。callback 只会在那些”有值“的索引上被调用，不会在那些被删除或从来未被赋值的索引上调用。
        callback 被调用时传入三个参数：元素的值，元素的索引，被遍历的数组。
        如果为 some 提供了一个 thisArg 参数，将会把它传给被调用的 callback，作为 this 值。否则，在非严格模式下将会是全局对象，严格模式下是 undefined。
        some 被调用时不会改变数组。
        some 遍历的元素的范围在第一次调用 callback. 时就已经确定了。在调用 some 后被添加到数组中的值不会被 callback 访问到。
        如果数组中存在且还未被访问到的元素被 callback 改变了，则其传递给 callback 的值是 some 访问到它那一刻的值。

    ```javascript
    // 检测在数组中是否有元素大于 10。

    function isBigEnough(element, index, array) {
      return (element >= 10);
    }
    var passed = [2, 5, 8, 1, 4].some(isBigEnough); // passed is false
    passed = [12, 5, 8, 1, 4].some(isBigEnough); // passed is true
    ```
 
- `Array.prototype.sort()` 方法在适当的位置对数组的元素进行排序，并返回数组。 sort 排序不一定是稳定的。默认排序顺序是根据字符串Unicode码点。

    > **语法**
        
        arr.sort()
        arr.sort(compareFunction)
    
    > **参数**
    
        compareFunction
            可选。用来指定按某种顺序进行排列的函数。如果省略，元素按照转换为的字符串的诸个字符的Unicode位点进行排序。
    
    > **返回值**
     
        返回排序后的数组。原数组已经被排序后的数组代替。

    > **描述**
    
        如果没有指明 compareFunction ，那么元素会按照转换为的字符串的诸个字符的Unicode位点进行排序。
        例如 "Banana" 会被排列到 "cherry" 之前。数字比大小时，9 出现在 80 之前，
        但这里比较时数字会先被转换为字符串，所以 "80" 比 "9" 要靠前。

        如果指明了 compareFunction ，那么数组会按照调用该函数的返回值排序。即 a 和 b 是两个将要被比较的元素：
        如果 compareFunction(a, b) 小于 0 ，那么 a 会被排列到 b 之前；
        如果 compareFunction(a, b) 等于 0 ， a 和 b 的相对位置不变。备注： ECMAScript 标准并不保证这一行为，
        而且也不是所有浏览器都会遵守（例如 Mozilla 在 2003 年之前的版本）；
        如果 compareFunction(a, b) 大于 0 ， b 会被排列到 a 之前。
        compareFunction(a, b) 必须总是对相同的输入返回相同的比较结果，否则排序的结果将是不确定的。

    所以，比较函数格式如下：

    ```javascript
    function compare(a, b) {
      if (a is less than b by some ordering criterion) {
        return -1;
      }
      if (a is greater than b by the ordering criterion) {
        return 1;
      }
      // a must be equal to b
      return 0;
    }
    ```

    希望比较数字而非字符串，比较函数可以简单的以 a 减 b，如下的函数将会将数组升序排列

    ```javascript
    function compareNumbers(a, b) {
      return a - b;
    }
    ```

    sort 方法可以使用 函数表达式 方便地书写：

    ```javascript
    var numbers = [4, 2, 5, 1, 3];
    numbers.sort(function(a, b) {
      return a - b;
    });
    console.log(numbers);

    // [1, 2, 3, 4, 5]
    ```

    对象可以按照某个属性排序：

    ```javascript
    var items = [
      { name: 'Edward', value: 21 },
      { name: 'Sharpe', value: 37 },
      { name: 'And', value: 45 },
      { name: 'The', value: -12 },
      { name: 'Magnetic' },
      { name: 'Zeros', value: 37 }
    ];

    items.sort(function (a, b) {
      if (a.value > b.value) {
        return 1;
      }
      if (a.value < b.value) {
        return -1;
      }
      // a 必须等于 b
      return 0;
    });
    ```

    ```javascript
    // 创建、显示及排序数组
    // 下述示例创建了四个数组，并展示原数组。之后对数组进行排序。对比了数字数组分别指定与不指定比较函数的结果。

    var stringArray = ["Blue", "Humpback", "Beluga"];
    var numericStringArray = ["80", "9", "700"];
    var numberArray = [40, 1, 5, 200];
    var mixedNumericArray = ["80", "9", "700", 40, 1, 5, 200];

    function compareNumbers(a, b)
    {
      return a - b;
    }

    console.log('stringArray:' + stringArray.join()); // Blue,Humpback,Beluga
    console.log('Sorted:' + stringArray.sort()); // Beluga,Blue,Humpback

    console.log('numberArray:' + numberArray.join()); // 40,1,5,200
    console.log('Sorted without a compare function:'+ numberArray.sort()); // 1,200,40,5
    console.log('Sorted with compareNumbers:'+ numberArray.sort(compareNumbers)); // 1,5,40,200

    console.log('numericStringArray:'+ numericStringArray.join()); // 80,9,700
    console.log('Sorted without a compare function:'+ numericStringArray.sort()); // 700,80,9
    console.log('Sorted with compareNumbers:'+ numericStringArray.sort(compareNumbers)); // 9,80,700

    console.log('mixedNumericArray:'+ mixedNumericArray.join());// 80,9,700,40,1,5,200
    console.log('Sorted without a compare function:'+ mixedNumericArray.sort()); // 1,200,40,5,700,80,9
    console.log('Sorted with compareNumbers:'+ mixedNumericArray.sort(compareNumbers)); // 1,5,9,40,80,200,700


    //使用映射改善排序
    //compareFunction 可能需要对元素做多次映射以实现排序，尤其当 compareFunction 较为复杂，
    //且元素较多的时候，某些 compareFunction 可能会导致很高的负载。使用 map 辅助排序将会是一个好主意。
    //基本思想是首先将数组中的每个元素比较的实际值取出来，排序后再将数组恢复。

    // 需要被排序的数组
    var list = ['Delta', 'alpha', 'CHARLIE', 'bravo'];

    // 对需要排序的数字和位置的临时存储
    var mapped = list.map(function(el, i) {
      return { index: i, value: el.toLowerCase() };
    })

    // 按照多个值排序数组
    mapped.sort(function(a, b) {
      return +(a.value > b.value) || +(a.value === b.value) - 1;
    });

    // 根据索引得到排序的结果
    var result = mapped.map(function(el){
      return list[el.index];
    });
    ```

- `Array.prototype.splice()` 方法通过删除现有元素和/或添加新元素来更改一个数组的内容。

    > **语法**
        
        array.splice(start)
        array.splice(start, deleteCount)
        array.splice(start, deleteCount, item1, item2, ...)

    > **参数**
        
        start​
            指定修改的开始位置（从0计数）。如果超出了数组的长度，则从数组末尾开始添加内容；
            如果是负值，则表示从数组末位开始的第几位（从1计数）；若只使用start参数而不使用deleteCount、item，
            如：array.splice(start) ，表示删除[start，end]的元素。
        deleteCount 可选
            整数，表示要移除的数组元素的个数。如果 deleteCount 是 0，则不移除元素。这种情况下，至少应添加一个新元素。
            如果 deleteCount 大于start 之后的元素的总数，则从 start 后面的元素都将被删除（含第 start 位）。
            如果deleteCount被省略，则其相当于(arr.length - start)。
            item1, item2, ... 可选
            要添加进数组的元素,从start 位置开始。如果不指定，则 splice() 将只删除数组元素。

    > **返回值**
    
        由被删除的元素组成的一个数组。如果只删除了一个元素，则返回只包含一个元素的数组。如果没有删除元素，则返回空数组。

    ```javascript
    var myFish = ["angel", "clown", "mandarin", "surgeon"];

    //从第 2 位开始删除 0 个元素，插入 "drum"
    var removed = myFish.splice(2, 0, "drum");
    //运算后的 myFish:["angel", "clown", "drum", "mandarin", "surgeon"]
    //被删除元素数组：[]，没有元素被删除

    //从第 3 位开始删除 1 个元素
    removed = myFish.splice(3, 1);
    //运算后的myFish：["angel", "clown", "mandarin",]
    //被删除元素数组：["surgeon"]

    //从第 2 位开始删除 1 个元素，然后插入 "trumpet"
    removed = myFish.splice(2, 1, "trumpet");
    //运算后的myFish: ["angel", "clown", "trumpet", "surgeon"]
    //被删除元素数组：["drum"]

    //从第 0 位开始删除 2 个元素，然后插入 "parrot", "anemone" 和 "blue"
    removed = myFish.splice(0, 2, "parrot", "anemone", "blue");
    //运算后的myFish：["parrot", "anemone", "blue", "trumpet", "surgeon"]
    //被删除元素的数组：["angel", "clown"]

    //从第 3 位开始删除 2 个元素
    removed = myFish.splice(3, Number.MAX_VALUE);
    //运算后的myFish: ["parrot", "anemone", "blue"]
    //被删除元素的数组：["trumpet", "surgeon"]

    //从第1位开始删除其后所有即[1，end]的元素
    removed = myFish.splice(1);
    //运算后的myFish: ["parrot"]
    //被删除元素的数组：["anemone","blue"]
    ```

- `Array.prototype.unshift()`  方法将一个或多个元素添加到数组的开头，并返回新数组的长度。

    > **语法**
    
        arr.unshift(element1, ..., elementN)
    
    > **参数列表**
      
        element1, ..., elementN 要添加到数组开头的元素。
    
    > **返回值**
    
        当一个对象调用该方法时，返回其 length 属性值。

    > **描述**
        
        unshift 方法会在调用它的类数组（array-like）对象的开始位置插入给定的参数。
        unshift 特意被设计成具有通用性；这个方法能够通过 call 或 apply 方法作用于类似数组的对象上。
        不过对于没有 length 属性（代表从0开始的一系列连续的数字属性的最后一个）的对象，调用该方法可能没有任何意义。

    ```javascript
    var arr = [1, 2];

    arr.unshift(0); //result of call is 3, the new array length
    //arr is [0, 1, 2]

    arr.unshift(-2, -1); // = 5
    //arr is [-2, -1, 0, 1, 2]

    arr.unshift( [-3] );
    //arr is [[-3], -2, -1, 0, 1, 2]
    ```

- `Array.prototype.values()` 对键值的遍历

    ```javascript
    // 使用 for...of 循环进行迭代
    let arr = ['w', 'y', 'k', 'o', 'p'];
    let eArr = arr.values();
    // 您的浏览器必须支持 for..of 循环
    // 以及 let —— 将变量作用域限定在 for 循环中
    for (let letter of eArr) {
      console.log(letter);
    }

    // 另一种迭代方式
    let arr = ['w', 'y', 'k', 'o', 'p'];
    let eArr = arr.values();
    console.log(eArr.next().value); // w
    console.log(eArr.next().value); // y
    console.log(eArr.next().value); // k
    console.log(eArr.next().value); // o
    console.log(eArr.next().value); // p
    ```
 






 

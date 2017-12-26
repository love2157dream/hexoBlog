---
title: JavaScript对象介绍之String对象
date: 2017-12-14 08:42:04
tags: 
    - JavaScript
    - String对象
categories: JavaScript
---

 
# String对象的方法

- `String.fromCharCode()` 方法返回使用指定的Unicode值序列创建的字符串。但是这个方法不能识别 32 位的 UTF-16 字符（Unicode 编号大于0xFFFF）。

    > **语法**

        String.fromCharCode(num1, ..., numN) 

    > **参数**

        num1, ..., numN  一组序列数字，表示 Unicode 值。

    > **描述**

        该方法返回一个字符串，而不是一个 String 对象。
        由于 fromCharCode 是 String 的静态方法，
        所以应该像这样使用：String.fromCharCode()，而不是作为你创建的 String 对象的方法。

    ```javascript
    console.log(String.fromCharCode(65,66,67)); // "ABC"
    ```


- `String.fromCodePoint()` 静态方法返回使用指定的代码点序列创建的字符串。可以识别大于0xFFFF的字符。**<font color=red>ES6支持</font>**

    > **语法**

        String.fromCodePoint(num1[, ...[, numN]])

    > **参数**

        num1, ..., numN     一串 Unicode 编码。

    > **返回值**

        使用 Unicode 编码创建的字符串。

    > **异常**

        RangeError
        如果传入无效的 Unicode 编码，将会抛出一个RangeError (例如： "RangeError: NaN is not a valid code point")。

    ```javascript
    console.log(String.fromCodePoint(42));       // "*"
    console.log(String.fromCodePoint(65, 90));   // "AZ"
    console.log(String.fromCodePoint(0x404));    // "\u0404"
    console.log(String.fromCodePoint(0x2F804));  // "\uD87E\uDC04"
    console.log(String.fromCodePoint(194564));   // "\uD87E\uDC04"
    console.log(String.fromCodePoint(0x1D306, 0x61, 0x1D307))； // "\uD834\uDF06a\uD834\uDF07"

    console.log(String.fromCodePoint('_'));      // RangeError
    console.log(String.fromCodePoint(Infinity)); // RangeError
    console.log(String.fromCodePoint(-1));       // RangeError
    console.log(String.fromCodePoint(3.14));     // RangeError
    console.log(String.fromCodePoint(3e-2));     // RangeError
    console.log(String.fromCodePoint(NaN));      // RangeError
    // String.fromCharCode() 方法不能单独获取在高代码点位上的字符
    // 另一方面，下列的示例中，可以返回 4 字节，也可以返回 2 字节的字符
    // (即，它可以返回单独的字符，使用长度 2 代替 1!） 
    console.log(String.fromCodePoint(0x2F804)); // or 194564 in decimal
    ```

- `String.prototype.charAt()` 返回在指定位置的字符。

    > **语法**
    
        str.charAt(index)
    
    > **参数**
    
        index 一个介于0 和字符串长度减1之间的整数。 (0~length-1) ,如果没有提供索引，charAt() 将使用0。
     
    > **描述**
    
    字符串中的字符从左向右索引，第一个字符的索引值为 0，最后一个字符（假设该字符位于字符串 stringName 中）的索引值为 stringName.length - 1。 
    如果指定的 index 值超出了该范围，则返回一个空字符串

    ```javascript
    var anyString = "Brave new world";

    console.log(anyString.charAt(0)); // 'B'
    console.log(anyString.charAt(1)); // 'r'
    console.log(anyString.charAt(2)); // 'a'
    console.log(anyString.charAt(3)); // 'v'
    console.log(anyString.charAt(4)); // 'e'
    console.log(anyString.charAt(999)); // ''
    ```

- `String.prototype.charCodeAt(index)` 返回在指定的位置的字符的 Unicode 编码。
    
    index的之是一个大于等于 0，小于字符串长度的整数。如果不是一个数值，则默认为 0。
    如果指定的 index 小于 0 或不小于字符串的长度，则 charCodeAt 返回 NaN。
    该方法只能分别返回前两个字节和后两个字节的值。

    ```javascript
    "ABC".charCodeAt(0); // returns 65:"A"

    "ABC".charCodeAt(1); // returns 66:"B"

    "ABC".charCodeAt(2); // returns 67:"C"

    "ABC".charCodeAt(3); // returns NaN
    ```

- `String.prototype.codePointAt(pos)` 方法返回 一个 Unicode 编码点值的非负整数。 **<font color=red>ES6支持</font>**
    
    该方法能够正确处理 4 个字节储存的字符，返回一个字符的码点。
    pos的值是字符在字符串中的位置（从 0 开始）。
    总之方法会正确返回 32 位的 UTF-16 字符的码点。对于那些两个字节储存的常规字符，它的返回结果与charCodeAt方法相同。
    
    ```javascript
    'ABC'.codePointAt(1);          // 66
    '\uD800\uDC00'.codePointAt(0); // 65536
    'XYZ'.codePointAt(42); // undefined

    let s = '𠮷a';
    s.codePointAt(0); // 134071
    s.codePointAt(1); // 57271
    s.codePointAt(2); // 97

    // codePointAt方法返回的是码点的十进制值，如果想要十六进制的值，
    // 可以使用toString方法转换一下。

    s.codePointAt(0).toString(16); // "20bb7"
    s.codePointAt(2).toString(16); // "61"
    ```

- `String.prototype.concat(string2, string3[, ..., stringN])`  方法将一个或多个字符串与原字符串连接合并，形成一个新的字符串并返回。

    ```javascript
    var hello = "Hello, ";
    console.log(hello.concat("Kevin", " have a nice day.")); // Hello, Kevin have a nice day. 
    ```

- `String.prototype.endsWith(searchString [, position])` 方法用来判断当前字符串是否是以另外一个给定的子字符串“结尾”的，根据判断结果返回 true 或 false。 **<font color=red>ES6支持</font>**

    `searchString` 要搜索的子字符串。
    `position` 在 str 中搜索 searchString 的结束位置，默认值为 str.length，也就是真正的字符串结尾处。

    ```javascript
    var str = "To be, or not to be, that is the question.";

    console.log(str.endsWith("question."));  // true
    console.log(str.endsWith("to be"));      // false
    console.log(str.endsWith("to be", 19));  // true
    console.log(str.endsWith("To be", 5));   // true
    ```

- `String.prototype.includes(searchString[, position])` 方法用于判断一个字符串是否包含在另一个字符串中，根据情况返回true或false。 **<font color=red>ES6支持</font>**

    `searchString` 要在此字符串中搜索的字符串。。
    `position` 可选。从当前字符串的哪个索引位置开始搜寻子字符串；默认值为0。

    ```javascript
    // includes() 方法是区分大小写的。
    'Blue Whale'.includes('blue'); // false

    var str = 'To be, or not to be, that is the question.';

    console.log(str.includes('To be'));       // true
    console.log(str.includes('question'));    // true
    console.log(str.includes('nonexistent')); // false
    console.log(str.includes('To be', 1));    // false
    console.log(str.includes('TO BE'));       // false
    ```

- `String.prototype.indexOf(searchValue[, fromIndex])` 方法返回调用  String 对象中第一次出现的指定值的索引，开始在 fromIndex进行搜索。如果没有找到 -1。

    `searchValue` 一个字符串表示被查找的值。
    `fromIndex` 可选
    表示调用该方法的字符串中开始查找的位置。可以是任意整数。默认值为 0。如果 fromIndex < 0 则查找整个字符串（如同传进了 0）。
    如果 fromIndex >= str.length，则该方法返回 -1，除非被查找的字符串是一个空字符串，此时返回 str.length
    
    ```javascript
    "Blue Whale".indexOf("Blue");     // returns  0
    "Blue Whale".indexOf("Blute");    // returns -1
    "Blue Whale".indexOf("Whale", 0); // returns  5
    "Blue Whale".indexOf("Whale", 5); // returns  5
    "Blue Whale".indexOf("", 9);      // returns  9
    "Blue Whale".indexOf("", 10);     // returns 10
    "Blue Whale".indexOf("", 11);     // returns 10

    // indexOf 方法区分大小写。例如，下面的表达式返回 -1：
    "Blue Whale".indexOf("blue"); // returns -1

    // 当检测某个字符串是否存在于另一个字符串中时，可使用下面的方法：
    "Blue Whale".indexOf("Blue") !== -1; // true
    "Blue Whale".indexOf("Bloe") !== -1; // false

    // 使用 indexOf 统计一个字符串中某个字母出现的次数
    var str = 'To be, or not to be, that is the question.';
    var count = 0;
    var pos = str.indexOf('e');

    while (pos !== -1) {
      count++;
      pos = str.indexOf('e', pos + 1);
    }

    console.log(count); // displays 4

    ```

- `String.prototype.lastIndexOf(searchValue[, fromIndex])` 方法返回指定值在调用该方法的字符串中最后出现的位置，如果没找到则返回 -1。从该字符串的后面向前查找，从 fromIndex 处开始。

    `searchValue` 一个字符串，表示被查找的值。
    `fromIndex` 从调用该方法字符串的此位置处开始查找。可以是任意整数。默认值为 str.length。
    如果为负值，则被看作 0。如果 fromIndex > str.length，则 fromIndex 被看作 str.length。

    ```javascript
    "canal".lastIndexOf("a");   // returns 3
    "canal".lastIndexOf("a",2); // returns 1
    "canal".lastIndexOf("a",0); // returns -1
    "canal".lastIndexOf("x");   // returns -1
    
    // lastIndexOf 方法区分大小写。例如，下面的表达式返回 -1：
    "Blue Whale, Killer Whale".lastIndexOf("blue"); // returns -1

    // 使用 indexOf 和 lastIndexOf 方法来定位字符串 "Brave new world" 中的值。
    var anyString = "Brave new world";
    console.log(anyString.indexOf("w")); // 8
    console.log(anyString.lastIndexOf("w"));  // 10
    console.log(anyString.indexOf("new"));  // 6
    console.log(anyString.lastIndexOf("new")); // 6
    ```

- `String.prototype.localeCompare()` 方法返回一个数字来指示一个参考字符串是否在排序顺序前面或之后或与给定字符串相同。
 
    > **语法**
    
        referenceStr.localeCompare(compareString[, locales[, options]])
    
    > **参数**

        compareString
            用来比较的字符串
        locales
            可选。 用来表示一种或多种语言或区域的一个符合 BCP 47 标准的字符串或一个字符串数组。 
            locales参数的一般形式与解释， 详情请参考 Intl page。 下列的 Unicode 扩展关键词是允许的：
        co
            为了某些地域多样的排序规则。可能的值包括： "big5han", "dict", "direct", "ducet", "gb2312", "phonebk", "phonetic", 
            "pinyin", "reformed", "searchjl", "stroke", "trad", "unihan"。 "standard" 和"search" 这两个值是被忽略的; 
            它们被 options 的属性 usage 代替(往下看)。
        kn
            指定数值排序是否应该被使用， 像是这样 "1" < "2" < "10"。 可能的值是 "true" 和 "false"。 
            这个选项能被通过options 属性设置或通过 Unicode 扩展。 假如两个都被设置了， 则 options 优先。（"language-region-u-kn-true|false"）
        kf
            指定是否优先对大写字母或小写字母排序。 可能的值有 "upper", "lower", 或 "false" (use the locale's default)。
            这个选项能被通过options 属性设置或通过 Unicode 扩展。假如两个都被设置了， 则 options 优先。（"language-region-u-kf-upper|lower|false"）
        options
            可选。 支持下列的一些或全部属性的一个对象:

            localeMatcher
                地域匹配算法的使用. 可能的值是 "lookup" 和 "best fit"; 默认的值是 "best fit"。
            usage
                指定比较的目标是排序或者是搜索. 可能的值是 "sort" 和 "search"; 默认是 "sort".
            sensitivity
                指定排序程序的敏感度可能的有:

                "base": 只有不同的字母字符串比较是不相等的. 举个例子: a ≠ b, a = á, a = A.
                "accent": 只有不同的字母或读音比较是不相等的. 举个例子: a ≠ b, a ≠ á, a = A.
                "case": 只有不同的字母或大小写比较是不相等的. 举个例子: a ≠ b, a = á, a ≠ A.
                "variant": 不同的字母或读音及其它有区别的标志或大小写都是不相等的， 还有其它的差异可能也会考虑到. 举个例子: a ≠ b, a ≠ á, a ≠ A.

            ignorePunctuation
                指定是否忽略标点. 可能的值是 true and false; 默认为 false.
            numeric
                是否指定使用数字排序, 像这样 "1" < "2" < "10". 可能的值是 true 和 false; 默认为 false. 
                这个选项能被通过options 属性设置或通过 Unicode 扩展。假如两个都被设置了， 则 options 优先。 实现不用必须支持这个属性.
            caseFirst
                指定大小写有限排序. 可能的值有 "upper", "lower", or "false" (use the locale's default); 默认为 "false". 
                这个选项能被通过options 属性设置或通过 Unicode 扩展。假如两个都被设置了， 则 options 优先。 实现不用必须支持这个属性.
        
    > **返回值**
        
        如果引用字符存在于比较字符之前则为负数; 如果比较字符存在于引用字符之后则为正数; 相等的时候返回 0 .
     
    > **描述**

        返回一个数字表示是否 引用字符串 在排序中位于 比较字符串 的前面，后面，或者二者相同。
        当 引用字符串 在 比较字符串 前面时返回 -1
        当 引用字符串 在 比较字符串 后面时返回 1
        相同位置时返回 0   
    
    ```javascript
    'a'.localeCompare('c');  // -1
    'check'.localeCompare('against');  // 1
    'a'.localeCompare('a');  // 0

    // 在不同的语言下 localeCompare() 所提供的结果是不一致的。 为了能让用户得到正确的比较值， 通过使用 locales 参数来提供要比较的语言:

    console.log('ä'.localeCompare('z', 'de')); // -1
    console.log('ä'.localeCompare('z', 'sv')); // 1
    
    // 使用 options 参数 ,localeCompare() 所提供的结果可以通过 options 参数来制定:
    console.log('ä'.localeCompare('a', 'de', { sensitivity: 'base' })); // 0
    console.log('ä'.localeCompare('a', 'sv', { sensitivity: 'base' })); // 1

    ```

- `String.prototype.match(regexp)` 查找找到一个或多个正则表达式的匹配。

    regexp 一个正则表达式对象。如果传入一个非正则表达式对象，则会隐式地使用 new RegExp(obj) 将其转换为一个 RegExp 。
    如果你未提供任何参数，直接使用 match() ，那么你会得到一个包含空字符串的 Array ：[""] 。
    返回一个数组array，一个包含了整个匹配结果以及任何括号捕获的匹配结果的 Array ；如果没有匹配项，则返回 null 。
    
    ```javascript
    /**
     * 在下例中，使用 match 查找 "Chapter" 紧跟着 1 个或多个数值字符，再紧跟着一个小数点和数值字符 0 次或多次。
     * 正则表达式包含 i 标志，因此大小写会被忽略。
     */

    var str = 'For more information, see Chapter 3.4.5.1';
    var re = /see (chapter \d+(\.\d)*)/i;
    var found = str.match(re);
    console.log(found);

    /**
     * match 使用全局（global）和忽略大小写（ignore case）标志 
     * 下例展示了 match 使用 global 和 ignore case 标志。A-E、a-e 的所有字母将会作为一个数组的元素返回。
     */
    var str = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz';
    var regexp = /[A-E]/gi;
    var matches_array = str.match(regexp);
    console.log(matches_array); // ['A', 'B', 'C', 'D', 'E', 'a', 'b', 'c', 'd', 'e']

    // 使用match()，不传参数
    var str = "Nothing will come of nothing.";
    str.match();   // returns [""]

    /**
     * 一个非正则表达式对象作为参数,
     * 当参数是一个字符串或一个数字，它会使用new RegExp(obj)来隐式转换成一个 RegExp。如果它是一个有正号的正数，RegExp() 方法将忽略正号。
     */
    
    var str1 = "NaN means not a number. Infinity contains -Infinity and +Infinity in JavaScript.",
    str2 = "My grandfather is 65 years old and My grandmother is 63 years old.",
    str3 = "The contract was declared null and void.";
    str1.match("number");   // "number" 是字符串。返回["number"]
    str1.match(NaN);        // NaN的类型是number。返回["NaN"]
    str1.match(Infinity);   // Infinity的类型是number。返回["Infinity"]
    str1.match(+Infinity);  // 返回["Infinity"]
    str1.match(-Infinity);  // 返回["-Infinity"]
    str2.match(65);         // 返回["65"]
    str2.match(+65);        // 有正号的number。返回["65"]
    str3.match(null);       // 返回["null"]
    ```

- `String.prototype.normalize([form])` 方法会按照指定的一种 Unicode 正规形式将当前字符串正规化.  **<font color=red>ES6支持</font>**

    `form`
        四种 Unicode 正规形式 "NFC", "NFD", "NFKC", 以及 "NFKD" 其中的一个, 默认值为 "NFC".
        NFC - 默认参数，表示“标准等价合成”(Normalization Form Canonical Composition.），返回多个简单字符的合成字符。
            所谓“标准等价”指的是视觉和语义上的等价。
        NFD，表示“标准等价分解”（Normalization Form Canonical Decomposition），即在标准等价的前提下，返回合成字符分解的多个简单字符。
        NFKC，表示“兼容等价合成”（Normalization Form Compatibility Composition），返回合成字符。所谓“兼容等价”指的是语义上存在等价，
            但视觉上不等价，比如“囍”和“喜喜”。（这只是用来举例，normalize方法不能识别中文。）
        NFKD，表示“兼容等价分解”（Normalization Form Compatibility Decomposition），即在兼容等价的前提下，返回合成字符分解的多个简单字符。

    ```javascript
    // Initial string

    // U+1E9B: LATIN SMALL LETTER LONG S WITH DOT ABOVE
    // U+0323: COMBINING DOT BELOW
    var str = "\u1E9B\u0323";


    // Canonically-composed form (NFC)

    // U+1E9B: LATIN SMALL LETTER LONG S WITH DOT ABOVE
    // U+0323: COMBINING DOT BELOW
    str.normalize("NFC"); // "\u1E9B\u0323"
    str.normalize(); // same as above


    // Canonically-decomposed form (NFD)

    // U+017F: LATIN SMALL LETTER LONG S
    // U+0323: COMBINING DOT BELOW
    // U+0307: COMBINING DOT ABOVE
    str.normalize("NFD"); // "\u017F\u0323\u0307"


    // Compatibly-composed (NFKC)

    // U+1E69: LATIN SMALL LETTER S WITH DOT BELOW AND DOT ABOVE
    str.normalize("NFKC"); // "\u1E69"


    // Compatibly-decomposed (NFKD)

    // U+0073: LATIN SMALL LETTER S
    // U+0323: COMBINING DOT BELOW
    // U+0307: COMBINING DOT ABOVE
    str.normalize("NFKD"); // "\u0073\u0323\u0307"
    ```

- `String.prototype.padEnd(targetLength [, padString])` 方法会用一个字符串填充当前字符串（如果需要的话则重复填充），返回填充后达到指定长度的字符串。从当前字符串的末尾（右侧）开始填充。 **<font color=red>ES6支持</font>**

    `targetLength` 
        当前字符串需要填充到的目标长度。如果这个数值小于当前字符串的长度，则返回当前字符串本身。
    `padString 可选`
        填充字符串。如果字符串太长，使填充后的字符串长度超过了目标长度，则只保留最左侧的部分，其他部分会被截断。此参数的缺省值为 " "（U+0020）。

    ```javascript
    'abc'.padEnd(10);          // "abc       "
    'abc'.padEnd(10, "foo");   // "abcfoofoof"
    'abc'.padEnd(6, "123456"); // "abc123"
    'abc'.padEnd(1);           // "abc"
    ```

- `String.prototype.padStart(targetLength [, padString])` 方法会用一个字符串填充当前字符串（如果需要的话则重复填充），返回填充后达到指定长度的字符串。从当前字符串的开头（左侧）开始填充。 **<font color=red>ES6支持</font>**

    `targetLength`
        当前字符串需要填充到的目标长度。如果这个数值小于当前字符串的长度，则返回当前字符串本身。
    `padString 可选`
        填充字符串。如果字符串太长，使填充后的字符串长度超过了目标长度，则只保留最左侧的部分，其他部分会被截断。此参数的缺省值为 " "（U+0020）。
    
    ```javascript
    'abc'.padStart(10);         // "       abc"
    'abc'.padStart(10, "foo");  // "foofoofabc"
    'abc'.padStart(6,"123465"); // "123abc"
    'abc'.padStart(8, "0");     // "00000abc"
    'abc'.padStart(1);          // "abc"
    ```

- `String.prototype.repeat(count)`  构造并返回一个新字符串，该字符串包含被连接在一起的指定数量的字符串的副本。 **<font color=red>ES6支持</font>**

    count 介于0和正无穷大之间的整数 : [0, +∞) 。表示在新构造的字符串中重复了多少遍原字符串。
    返回值： 包含指定字符串的指定数量副本的新字符串。
    RangeError: 重复次数不能为负数。
    RangeError: 重复次数必须小于 infinity，且长度不会大于最长的字符串。

    ```javascript
    "abc".repeat(-1)     // RangeError: repeat count must be positive and less than inifinity
    "abc".repeat(0)      // ""
    "abc".repeat(1)      // "abc"
    "abc".repeat(2)      // "abcabc"
    "abc".repeat(3.5)    // "abcabcabc" 参数count将会被自动转换成整数.
    "abc".repeat(1/0)    // RangeError: repeat count must be positive and less than inifinity

    ({toString : () => "abc", repeat : String.prototype.repeat}).repeat(2)   
    //"abcabc",repeat是一个通用方法,也就是它的调用者可以不是一个字符串对象.
    ```

- `String.prototype.replace(regexp|substr, newSubStr|function)` 方法返回一个由替换值替换一些或所有匹配的模式后的新字符串。模式可以是一个字符串或者一个正则表达式, 替换值可以是一个字符串或者一个每次匹配都要调用的函数。原字符串不会改变。

    `regexp (pattern)`
        一个RegExp 对象或者其字面量。该正则所匹配的内容会被第二个参数的返回值替换掉。
    `substr (pattern)`
        一个要被 newSubStr 替换的字符串。其被视为一整个字符串，而不是一个正则表达式。仅仅是第一个匹配会被替换。
    `newSubStr (replacement)`
        用于替换掉第一个参数在原字符串中的匹配部分的字符串。该字符串中可以内插一些特殊的变量名。参考下面的使用字符串作为参数。
    `function (replacement)`
        一个用来创建新子字符串的函数，该函数的返回值将替换掉第一个参数匹配到的结果。

    ```javascript
    /**
     * 在 replace() 中使用正则表达式 
     * 在下面的例子中，replace() 中使用了正则表达式及忽略大小写标示。
     */
    var str = 'Twas the night before Xmas...';
    var newstr = str.replace(/xmas/i, 'Christmas');
    console.log(newstr);  // Twas the night before Christmas...

    /**
     * 在 replace() 中使用 global 和 ignore 选项 
     * 下面的例子中,正则表达式包含有全局替换(g)和忽略大小写(i)的选项,这使得replace方法用'oranges'替换掉了所有出现的"apples".
     */
    var re = /apples/gi;
    var str = "Apples are round, and apples are juicy.";
    var newstr = str.replace(re, "oranges");

    // oranges are round, and oranges are juicy.
    console.log(newstr);

    /**
     * 交换字符串中的两个单词 
     * 下面的例子演示了如何交换一个字符串中两个单词的位置，这个脚本使用$1 和 $2 代替替换文本。
     */
    var re = /(\w+)\s(\w+)/;
    var str = "John Smith";
    var newstr = str.replace(re, "$2, $1");
    console.log(newstr);  // Smith, John
    ```

- `String.prototype.search(regexp)`  方法用于检索字符串中指定的子字符串，或检索与正则表达式相匹配的子字符串.如果没有找到任何匹配的子串，则返回 -1。

    regexp
        一个正则表达式（regular expression）对象。如果传入一个非正则表达式对象，则会使用 new RegExp(obj) 隐式地将其转换为正则表达式对象。
    如果匹配成功，则 search() 返回正则表达式在字符串中首次匹配项的索引。否则，返回 -1。

    ```javascript
    var str="Mr. Blue has a blue house";
    console.log(str.search("blue")); // 15

    var str="Mr. Blue has a blue house";
    console.log(str.search(/blue/i)); // 4
    ```

- `String.prototype.slice(beginSlice[, endSlice])` 提取字符串的片断，并在新的字符串中返回被提取的部分。

    `beginSlice`
        从该索引（以 0 为基数）处开始提取原字符串中的字符。如果值为负数，会被当做 sourceLength + beginSlice 看待，
        这里的sourceLength 是字符串的长度 (例如， 如果beginSlice 是 -3 则看作是: sourceLength - 3)
    `endSlice`
        可选。在该索引（以 0 为基数）处结束提取字符串。如果省略该参数，slice会一直提取到字符串末尾。如果该参数为负数，
        则被看作是 sourceLength + endSlice，这里的 sourceLength 就是字符串的长度(例如，如果 endSlice 是 -3，则是, sourceLength - 3)。

    slice() 从一个字符串中提取字符串并返回新字符串。在一个字符串中的改变不会影响另一个字符串。也就是说，slice 不修改原字符串，只会返回一个包含了原字符串中部分字符的新字符串。
    注意：slice() 提取的新字符串包括beginSlice但不包括 endSlice。
    例1：str.slice(1, 4) 提取新字符串从第二个字符到第四个 (字符索引值为 1, 2, 和 3)。
    例2：str.slice(2, -1) 提取第三个字符到倒数第二个字符。

    ```javascript
    var str1 = 'The morning is upon us.';
    var str2 = str1.slice(4, -2);
    console.log(str2); // OUTPUT: morning is upon u

    var str = 'The morning is upon us.';
    str.slice(-3);     // returns 'us.'
    str.slice(-3, -1); // returns 'us'
    str.slice(0, -1);  // returns 'The morning is upon us'
    ```

- `String.prototype.split([separator[, limit]] )` 方法使用指定的分隔符字符串将一个String对象分割成字符串数组，以将字符串分隔为子字符串，以确定每个拆分的位置。
    如果空字符串("")被用作分隔符，则字符串会在每个字符之间分割。

    `separator`
        指定表示每个拆分应发生的点的字符串。separator 可以是一个字符串或正则表达式。 
        如果纯文本分隔符包含多个字符，则必须找到整个字符串来表示分割点。
        如果在str中省略或不出现分隔符，则返回的数组包含一个由整个字符串组成的元素。
        如果分隔符为空字符串，则将str原字符串中每个字符的数组形式返回。
    `limit`
        一个整数，限定返回的分割片段数量。当提供此参数时，split 方法会在指定分隔符的每次出现时分割该字符串，
        但在限制条目已放入数组时停止。如果在达到指定限制之前达到字符串的末尾，它可能仍然包含少于限制的条目。
        新数组中不返回剩下的文本。

    ```javascript
    "Webkit Moz O ms Khtml".split(" ");   // ["Webkit", "Moz", "O", "ms", "Khtml"]
    
    /**
     * 根据指定的分隔符将一个字符串分割成一个字符串数组。
     * 分隔字符串后，该函数依次输出原始字符串信息，被使用的分隔符，返回数组元素的个数，以及返回数组中所有的元素。
     * @param  {[type]} stringToSplit [description]
     * @param  {[type]} separator     [description]
     * @return {[type]}               [description]
     */
    function splitString(stringToSplit, separator) {
      var arrayOfStrings = stringToSplit.split(separator);

      console.log('The original string is: "' + stringToSplit + '"');
      console.log('The separator is: "' + separator + '"');
      console.log("The array has " + arrayOfStrings.length + " elements: ");

      for (var i=0; i < arrayOfStrings.length; i++)
        console.log(arrayOfStrings[i] + " / ");
    }

    var tempestString = "Oh brave new world that has such people in it.";
    var monthString = "Jan,Feb,Mar,Apr,May,Jun,Jul,Aug,Sep,Oct,Nov,Dec";

    var space = " ";
    var comma = ",";

    splitString(tempestString, space);
    splitString(tempestString);
    splitString(monthString, comma);

    // The original string is: "Oh brave new world that has such people in it."
    // The separator is: " "
    // The array has 10 elements: Oh / brave / new / world / that / has / such / people / in / it. /

    // The original string is: "Oh brave new world that has such people in it."
    // The separator is: "undefined"
    // The array has 1 elements: Oh brave new world that has such people in it. /

    // The original string is: "Jan,Feb,Mar,Apr,May,Jun,Jul,Aug,Sep,Oct,Nov,Dec"
    // The separator is: ","
    // The array has 12 elements: Jan / Feb / Mar / Apr / May / Jun / Jul / Aug / Sep / Oct / Nov / Dec /
    
    /**
     * 下例中，split 方法会查找“0 或多个空白符接着的分号，再接着 0 或多个空白符”模式的字符串，
     * 找到后，就将空白符从字符串中移除，nameList 是 split 的返回数组。
     */
    var names = "Harry Trump ;Fred Barney; Helen Rigby ; Bill Abel ;Chris Hand ";
    console.log(names); // Harry Trump ;Fred Barney; Helen Rigby ; Bill Abel ;Chris Hand
    var re = /\s*;\s*/;
    var nameList = names.split(re);
    console.log(nameList); // Harry Trump,Fred Barney,Helen Rigby,Bill Abel,Chris Hand

    //下例中，split 查找字符串中的 0 或多个空格，并返回找到的前 3 个分割元素（splits）。

    var myString = "Hello World. How are you doing?";
    var splits = myString.split(" ", 3);
    console.log(splits); // ["Hello", "World.", "How"]

    // 如果 separator 包含捕获括号（capturing parentheses），则其匹配结果将会包含在返回的数组中。
    var myString = "Hello 1 word. Sentence number 2.";
    var splits = myString.split(/(\d)/);
    console.log(splits); // [ "Hello ", "1", " word. Sentence number ", "2", "." ]

    ```

- `String.prototype.startsWith(searchString [, position])` 方法用来判断当前字符串是否是以另外一个给定的子字符串“开头”的，根据判断结果返回 true 或 false。  **<font color=red>ES6支持</font>**

    `searchString` 要搜索的子字符串。
   
    `position`  在 str 中搜索 searchString 的开始位置，默认值为 0，也就是真正的字符串开头处。

    ```javascript
    var str = "To be, or not to be, that is the question.";
    console.log(str.startsWith("To be"));         // true
    console.log(str.startsWith("not to be"));     // false
    console.log(str.startsWith("not to be", 10)); // true
    ```

- `String.prototype.substr()`  方法返回一个字符串中从指定位置开始到指定字符数的字符。

    > **语法**
    
        str.substr(start[, length])
   
    > **参数**
        
        start 
            开始提取字符的位置。如果为负值，则被看作 strLength - start，
            其中 strLength 为字符串的长度（例如，如果 start 为 -3，则被看作 strLength-3）。
        length 
            可选。提取的字符数。
   
    > **描述**
    
        start 是一个字符的索引。首字符的索引为 0，最后一个字符的索引为 字符串的长度减去1。
        substr 从 start 位置开始提取字符，提取 length 个字符（或直到字符串的末尾）。
        如果 start 为正值，且大于或等于字符串的长度，则 substr 返回一个空字符串。
        如果 start 为负值，则 substr 把它作为从字符串末尾开始的一个字符索引。
        如果 start 为负值且 abs(start) 大于字符串的长度，则 substr 使用 0 作为开始提取的索引。
        注意负的 start 参数不被 Microsoft JScript 所支持。
        如果 length 为 0 或负值，则 substr 返回一个空字符串。如果忽略 length，则 substr 提取字符，直到字符串末尾。

    ```javascript
    var str = "abcdefghij";
    console.log("(1,2): "    + str.substr(1,2));   // (1,2): bc
    console.log("(-3,2): "   + str.substr(-3,2));  // (-3,2): hi
    console.log("(-3): "     + str.substr(-3));    // (-3): hij
    console.log("(1): "      + str.substr(1));     // (1): bcdefghij
    console.log("(-20, 2): " + str.substr(-20,2)); // (-20, 2): ab
    console.log("(20, 2): "  + str.substr(20,2));  // (20, 2):
    ```

- `String.prototype.substring()` 方法返回一个字符串在开始索引到结束索引之间的一个子集, 或从开始索引直到字符串的末尾的一个子集。

    > **语法**
    
        str.substring(indexStart[, indexEnd])
    
    > **参数**
        
        indexStart
            一个 0 到字符串长度之间的整数。
        indexEnd
            可选。一个 0 到字符串长度之间的整数。
    
    > **描述**
    
        substring 提取从 indexStart 到 indexEnd（不包括）之间的字符。特别地：
        如果 indexStart 等于 indexEnd，substring 返回一个空字符串。
        如果省略 indexEnd，substring 提取字符一直到字符串末尾。
        如果任一参数小于 0 或为 NaN，则被当作 0。
        如果任一参数大于 stringName.length，则被当作 stringName.length。
        如果 indexStart 大于 indexEnd，则 substring 的执行效果就像两个参数调换了一样。例如，str.substring(1, 0) == str.substring(0, 1)。
       
    ```javascript
    var anyString = "Mozilla";

    // 输出 "Moz"
    console.log(anyString.substring(0,3));
    console.log(anyString.substring(3,0));
    console.log(anyString.substring(3,-3));
    console.log(anyString.substring(3,NaN));
    console.log(anyString.substring(-2,3));
    console.log(anyString.substring(NaN,3));

    // 输出 "lla"
    console.log(anyString.substring(4,7));
    console.log(anyString.substring(7,4));

    // 输出 ""
    console.log(anyString.substring(4,4));

    // 输出 "Mozill"
    console.log(anyString.substring(0,6));

    // 输出 "Mozilla"
    console.log(anyString.substring(0,7));
    console.log(anyString.substring(0,10));

    /**
     * 运用 length 属性来使用 substring() 
     * 下面一个例子运用了    String.length 属性去获取指定字符串的倒数元素。
     * 显然这个办法更容易记住，因为你不再像上面那个例子那样去记住起始位置和最终位置。
     */
    // Displays 'illa' the last 4 characters
    var anyString = 'Mozilla';
    var anyString4 = anyString.substring(anyString.length - 4);
    console.log(anyString4);

    // Displays 'zilla' the last 5 characters
    var anyString = 'Mozilla';
    var anyString5 = anyString.substring(anyString.length - 5);
    console.log(anyString5);


    /**
     * 下例替换了一个字符串中的子字符串。可以替换单个字符和子字符串。
     * 该例结尾调用的函数将 "Brave New World" 变成了 "Brave New Web"。
     */
    function replaceString(oldS, newS, fullS) {
    // Replaces oldS with newS in the string fullS
      for (var i = 0; i < fullS.length; i++) {
        if (fullS.substring(i, i + oldS.length) == oldS) {
         fullS = fullS.substring(0, i) + newS + fullS.substring(i + oldS.length, fullS.length);
        }
      }
      return fullS;
    }

    replaceString("World", "Web", "Brave New World");

    // 需要注意的是，如果 oldS 是 newS 的子字符串将会导致死循环。例如，尝试把 "World" 替换成 "OtherWorld"。一个更好的方法如下：

    function replaceString(oldS, newS,fullS){
      return fullS.split(oldS).join(newS);
    }
    // 上面的代码只是子字符串操作的一个例子。如果你需要替换子字符串，更多时候会用到 String.prototype.replace()。
    ```

- `String.prototype.toLocaleLowerCase()`  方法根据任何特定于语言环境的案例映射，返回调用字符串值转换为小写的值。

    ```javascript
        console.log('ALPHABET'.toLocaleLowerCase());  // 'alphabet'
        console.log('中文简体 zh-CN || zh-Hans'.toLocaleLowerCase()); // '中文简体 zh-cn || zh-hans'
    ```

- `String.prototype.toLocaleUpperCase()` 使用本地化（locale-specific）的大小写映射规则将输入的字符串转化成大写形式并返回结果字符串。

    ```javascript
        console.log('alphabet'.toLocaleUpperCase()); // 'ALPHABET'
    ```
    
- `String.prototype.toLowerCase()`  会将调用该方法的字符串值转为小写形式，并返回。

    ```javascript
    console.log('中文简体 zh-CN || zh-Hans'.toLowerCase()); // 中文简体 zh-cn || zh-hans
    ​console.log( "ALPHABET".toLowerCase() );  // "alphabet"
    ```

- `String.prototype.toString()`  方法返回指定对象的字符串形式。

    ```javascript
    var x = new String("Hello world");
    console.log(x.toString());      // 输出 "Hello world"
    ```

- `String.prototype.toUpperCase()`  将调用该方法的字符串值转换为大写形式，并返回。

    ```javascript
    ​console.log( "alphabet".toUpperCase() ); // "ALPHABET"
    ```

- `String.prototype.trim()`  方法会从一个字符串的两端删除空白字符。在这个上下文中的空白字符是所有的空白字符 (space, tab, no-break space 等) 以及所有行终止符字符（如 LF，CR）。

    ```javascript
    var orig = '   foo  ';
    console.log(orig.trim()); // 'foo'

    // 另一个.trim()例子，只从一边删除
    var orig = 'foo    ';
    console.log(orig.trim()); // 'foo'
    ```

- `String.prototype.trimLeft()`  方法从一个字符串的左端移除空白字符。

    ```javascript
    var str = "   foo  ";
    console.log(str.length); // 8
    str = str.trimLeft();
    console.log(str.length); // 5
    console.log( str ); //'foo  '
    ```

- `String.prototype.trimRight()` 方法从一个字符串的右端移除空白字符。

    ```javascript
    var str = "   foo  ";
    console.log(str.length); // 8
    str = str.trimRight();
    console.log(str.length); // 6
    console.log( str ); // '   foo'
    ```

- `String.prototype.valueOf()` 方法返回一个String对象的原始值

    ```javascript
    var str="Hello world!";
    console.log(str.valueOf()); // 'Hello world!'
    ```

- `String.raw()` 是一个模板字符串的标签函数，它的作用类似于 Python 中的字符串前缀 r 和 C# 中的字符串前缀 @，是用来获取一个模板字符串的原始字面量值的。**<font color=red>ES6支持</font>**

    > **语法**
        
        String.raw(callSite, ...substitutions)
        String.raw`templateString`
    
    > **参数**
        
        callSite
            一个模板字符串的“调用点对象”。类似{ raw: ['foo', 'bar', 'baz'] }。
        ...substitutions
            任意个可选的参数，表示任意个内插表达式对应的值。
        templateString
            模板字符串。
    
    > **返回**
        
        给定模板字符串的原始字面量值。

    > **异常**
    
        TypeError
        如果第一个参数没有传入一个格式良好的调用点对象，则会抛出 TypeError 异常。
    
    > **描述**
    
        不要被上面复杂的参数要求吓到，因为像所有的标签函数一样，你通常不需要把它看成一个普通函数，
        你只需要把它放在模板字符串前面就可以了，而不是在它后面加个括号和一堆参数来调用它，引擎会替你去调用它。
        String.raw() 是唯一一个内置的模板字符串标签函数，因为它太常用了。不过它并没有什么特殊能力，
        你自己也可以实现一个和它功能一模一样的标签函数。
        
    ```javascript
    String.raw `Hi\n!`;  // "Hi\\n!"，这里得到的不是 Hi 后面跟个换行符，而是跟着 \ 和 n 两个字符

    String.raw `Hi\u000A!`;             
    // "Hi\\u000A!"，同上，这里得到的会是 \、u、0、0、0、A 6个字符，
    // 任何类型的转义形式都会失效，保留原样输出，不信你试试.length

    let name = "Bob";
    String.raw `Hi\n${name}!`;             
    // "Hi\\nBob!"，内插表达式还可以正常运行

    String.raw({raw: "test"}, 0, 1, 2); 
    // "t0e1s2t"，我认为你通常不需要把它当成普通函数来调用
    
    // String.raw方法也可以作为正常的函数使用。这时，它的第一个参数，应该是一个具有raw属性的对象，且raw属性的值应该是一个数组。

    String.raw({ raw: 'test' }, 0, 1, 2);
    // 't0e1s2t'

    // 等同于
    String.raw({ raw: ['t','e','s','t'] }, 0, 1, 2);
    ```

# String HTML 包装方法

- `String.prototype.anchor()` 方法创建一个 `a` HTML 锚元素，

    ```javascript
    var myString = "Table of Contents";
    console.log(myString.anchor("contents_anchor")); // <a name="contents_anchor">Table of Contents</a>
    ```

- `String.prototype.big()` 方法的作用是创建一个使字符串显示大号字体的 `big` 标签。**<font color=red>已废弃</font>**

    ```javascript
    var worldString = 'Hello, world';
    console.log(worldString.small());     // <small>Hello, world</small>
    ```

- `String.prototype.blink()` 方法创建使字符串闪烁的 `blink` HTML 元素。闪烁文本被多种普及标准否决。 **<font color=red>已废弃</font>**

    ```javascript
    var worldString = 'Hello, world';
    console.log(worldString.blink());   // <blink>Hello, world</blink>
    ```

- `String.prototype.bold()`  使用粗体显示字符串。

    ```javascript
    var worldString = 'Hello, world';
    console.log(worldString.bold());    // <b>Hello, world</b>
    ```

- `String.prototype.fixed()`  方法创建了一个 `tt` 标签元素将字符串包裹起来，从而让这个字符串里面的内容具有固定间距。**<font color=red>已废弃</font>**

    ```javascript
    var worldString = 'Hello, world';
    console.log(worldString.fixed()); // "<tt>Hello, world</tt>"
    ```

- `String.prototype.fontcolor()` 方法创建一个 `font` 的HTML元素让字符串被显示成指定的字体颜色。**<font color=red>已废弃</font>**

    ```javascript
    var worldString = "Hello, world"

    console.log(worldString.fontcolor('red') + ' is red in this line');
    // <font color="red">Hello, world </font> is red in this line"

    console.log（worldString.fontcolor('FF00') + ' is red in hexadecimal'
    // <font color="FF00">Hello，world </font> is red in hexadecimal
    ```

- `String.prototype.fontsize()` 使用指定的尺寸来显示字符串。**<font color=red>已废弃</font>**

    ```javascript
    var worldString = 'Hello, world';
    console.log(worldString.fontsize(7)); // <font size="7">Hello, world</fontsize>
    ```

- `String.prototype.italics()`  使用斜体显示字符串。**<font color=red>已废弃</font>**

    ```javascript
    var worldString = 'Hello, world';  
    console.log(worldString.italics()); //Hello, world
    ```

- `String.prototype.link()` 方法创建一个 a HTML 元素，用该字符串作为超链接的显示文本，参数作为指向另一个 URL 的超链接。

    ```javascript
    var hotText = "MDN";
    var URL = "https://developer.mozilla.org/";
    console.log("Click to return to " + hotText.link(URL)); // Click to return to <a href="https://developer.mozilla.org/">MDN</a> 
    ```

- `String.prototype.small()`  方法的作用是创建一个使字符串显示小号字体的 `small` 标签。 **<font color=red>已废弃</font>**

    ```javascript
    var worldString = 'Hello, world';
    console.log(worldString.small());     // <small>Hello, world</small>
    ```

- `String.prototype.strike()` 方法创建 `strike` HTML 元素，使字符串展示为被删除的文本。**<font color=red>已废弃</font>**

    ```javascript
    var worldString = 'Hello, world'; 
    console.log(worldString.strike()); // <strike>Hello, world</strike>
    ```

- `String.prototype.sub()` 方法创建一个 `sub` HTML 元素，使字符串展示为下标。**<font color=red>已废弃</font>**

    ```javascript
    var subText = 'subscript'; 
    console.log('This is what a ' + subText.sub() + ' looks like.');  // This is what a <sub>subscript</sub> looks like.。
    ```

- `String.prototype.sup()` 方法创建 一个 `sup` HTML 元素，使字符串显示为上标。**<font color=red>已废弃</font>**

    ```javascript
    var superText = 'superscript'; 
    console.log('This is what a ' + superText.sup() + ' looks like.');  // This is what a <sup>superscript</sup> looks like.。
    ```

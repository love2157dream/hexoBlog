---
title: JavaScript对象介绍之Date对象
date: 2017-12-14 08:42:20
tags: 
    - JavaScript
    - Date对象
categories: JavaScript
---

# Date对象方法

- `Date.UTC()` 根据世界时返回 1970 年 1 月 1 日 到指定日期的毫秒数。 UTC时间与GMT(格林尼治时间)相同。
    **提示**: 协调世界时，又称世界统一时间，世界标准时间，国际协调时间，简称UTC( Universal Coordinated Time ) 。

    > **语法**

        Date.UTC(year,month,day,hours,minutes,seconds,millisec)

    > **参数**

        year    必需。表示年份的四位数字。
        month   必需。表示月份的整数，介于 0 ~ 11。
        day 必需。表示日期的整数，介于 1 ~ 31。
        hours   可选。表示小时的整数，介于 0 ~ 23。
        minutes 可选。表示分钟的整数，介于 0 ~ 59。
        seconds 可选。表示秒的整数，介于 0 ~ 59。
        ms  可选。表示毫秒的整数，介于 0 ~ 999。

    > **返回值**

        Number  返回指定的时间距 GMT 时间 1970 年 1 月 1 日午夜的毫秒数。

    ```javascript
        new Date(Date.UTC(2017, 12, 14, 10, 39)); // Sun Jan 14 2018 18:39:00 GMT+0800 (中国标准时间)
    ```

- `Date.now()` 方法返回自1970年1月1日 00:00:00 UTC到当前时间的毫秒数。

    ```javascript
    // now()方法返回自1970年1月1日 00:00:00 UTC到当前时间的毫秒数，类型为Number。
    // 因为 now() 是Date的一个静态函数，所以必须以 Date.now() 的形式来使用。
    // 通过下面的代码来兼容那些不支持该方法的引
    if (!Date.now) {
      Date.now = function now() {
        return new Date().getTime();
      };
    }

    Date.now(); // 1513219457449
    ```


- `Date.parse()` 方法解析一个表示某个日期的字符串，并返回从1970-1-1 00:00:00 UTC 到该日期对象（该日期对象的UTC时间）的毫秒数，
如果该字符串无法识别，或者一些情况下，包含了不合法的日期数值（如：2015-02-31），则返回值为NaN。

    > **语法**

        显示调用： Date.parse(dateString)
        隐式调用： new Date(dateString)

    > **参数**
    
        dateString 一个符合 RFC2822 或 ISO 8601 日期格式的字符串（其他格式也许也支持，但结果可能与预期不符）。
    
    > **返回值**
    
        一个表示从1970-1-1 00:00:00 UTC到给定日期字符串所表示时间的毫秒数的数值。如果参数不能解析为一个有效的日期，则返回NaN。
    
    > **描述**
    
        parse 方法接受一个日期字符串（例如 "Dec 25, 1995"），并返回从1970-1-1 00:00:00 UTC到该日期字符串所表示日期的毫秒数。
        该方法在基于字符串值设置日期值时很有用，例如结合使用setTime() 方法和 Date() 构造函数。
        parse 方法接受一个表示时间的字符串，返回相应的时间值。该方法可以接受符合 RFC2822 / IETF 日期语法 (RFC2822 Section 3.3) 的字符串，
        如 "Mon, 25 Dec 1995 13:30:00 GMT"。该方法能够理解美国大陆时区的缩写，但是为了更通用，应该使用时区偏移，
        如 "Mon, 25 Dec 1995 13:30:00 +0430" （格林威治的子午线向东偏移4小时30分钟）。如果没有指定时区，默认使用本地时区。

    ```javascript
    // 包含无效值的非 ISO 格式字符串
    new Date('23/25/2014');
    ```

- `Date.prototype.getDate()` 根据本地时间，返回一个指定的日期对象为一个月中的第几天。

    ```javascript
    var d = new Date(); // Thu Dec 14 2017 13:23:42 GMT+0800 (中国标准时间)
    console.log(d.getDate()); //  14
    ```

- `Date.prototype.getDay()` 方法根据本地时间，返回一个具体日期中一周的第几天，0 表示星期天。1 代表星期一，2 代表星期二， 依次类推。

    ```javascript
    var d = new Date(); // Thu Dec 14 2017 13:23:42 GMT+0800 (中国标准时间)
    console.log(d.getDay()); //  4
    ```
 
- `Date.prototype.getFullYear()` 方法根据本地时间返回指定日期的年份。此方法替代 getYear() 。

    ```javascript
    var d = new Date(); // Thu Dec 14 2017 13:23:42 GMT+0800 (中国标准时间)
    console.log(d.getFullYear()); //  2017
    ```

- `Date.prototype.getHours()` 方法根据本地时间，返回一个指定的日期对象的小时。返回一个0 到 23之间的整数值。

    ```javascript
    var d = new Date(); // Thu Dec 14 2017 13:23:42 GMT+0800 (中国标准时间)
    console.log(d.getHours()); //  13
    ```

- `Date.prototype.getMilliseconds()`  方法，根据本地时间，返回一个指定的日期对象的毫秒数。返回一个0 到 999的整数。

    ```javascript
    var d = new Date(); // Thu Dec 14 2017 13:23:42 GMT+0800 (中国标准时间)
    console.log(d.getMilliseconds()); //  603
    ```

- `Date.prototype.getMinutes()` 方法根据本地时间，返回一个指定的日期对象的分钟数。返回一个0 到 59的整数值。

    ```javascript
    var d = new Date(); // Thu Dec 14 2017 13:23:42 GMT+0800 (中国标准时间)
    console.log(d.getMinutes()); //  23
    ```

- `Date.prototype.getMonth()` 根据本地时间，返回一个指定的日期对象的月份，为基于0的值（0表示一年中的第一月）。返回一个0 到 11的整数值： 0 代表一月份，1 代表二月分， 2 代表三月份，依次类

    ```javascript
    var d = new Date(); // Thu Dec 14 2017 13:23:42 GMT+0800 (中国标准时间)
    console.log(d.getMonth()); //  11
    ```

- `Date.prototype.getSeconds()`  方法根据本地时间，返回一个指定的日期对象的秒数。

    ```javascript
    var d = new Date(); // Thu Dec 14 2017 13:23:42 GMT+0800 (中国标准时间)
    console.log(d.getSeconds()); //  28
    ```

- `Date.prototype.getTime()` 方法的返回值一个数值，表示从1970年1月1日0时0分0秒（UTC，即协调世界时）距离该日期对象所代表时间的毫秒数。

    ```javascript
    var d = new Date(); // Thu Dec 14 2017 13:23:42 GMT+0800 (中国标准时间)
    console.log(d.getSeconds()); //  1513229008603
    ```

- `Date.prototype.getTimezoneOffset()` 方法返回协调世界时（UTC）相对于当前时区的时间差值，单位为分钟。
时区偏差（time-zone offset）表示协调世界时（UTC）与本地时区之间的差值，单位为分钟。
需要注意的是如果本地时区晚于协调世界时，则该差值为正值，如果早于协调世界时则为负值。
例如你所在时区为 UTC+10（澳大利亚东部标准时间），将会返回 -600。对于同一个时区，夏令时（Daylight Saving Time）将会改变这个值。
    ```javascript
    var d = new Date(); // Thu Dec 14 2017 13:23:42 GMT+0800 (中国标准时间)
    console.log(d.getTimezoneOffset()); //  -480
    ```

- `Date.prototype.getUTCDate()` 方法以世界时为标准，返回一个指定的日期对象为一个月中的第几天.返回一个 1 到 31 的整数值

    ```javascript
    var d = new Date(); // Thu Dec 14 2017 13:23:42 GMT+0800 (中国标准时间)
    console.log(d.getUTCDate()); //  14
    ```

- `Date.prototype.getUTCDay()` 方法返回一个对应一星期中第几天的整数：0 代表星期天，1 代表星期一，2 代表星期二，依次类推。

    ```javascript
    var d = new Date(); // Thu Dec 14 2017 13:23:42 GMT+0800 (中国标准时间)
    console.log(d.getUTCDay()); //  4
    ```
 
- `Date.prototype.getUTCFullYear()` 以世界时为标准，返回一个指定的日期对象的年份。

    ```javascript
    var d = new Date(); // Thu Dec 14 2017 13:23:42 GMT+0800 (中国标准时间)
    console.log(d.getUTCFullYear()); //  2017
    ```

- `Date.prototype.getUTCHours()` 方法以世界时为标准，返回一个指定的日期对象的小时数。 返回一个 0 到 23 的整数。

    ```javascript
    var d = new Date(); // Thu Dec 14 2017 13:23:42 GMT+0800 (中国标准时间)
    console.log(d.getUTCHours()); //  5
    ```

- `Date.prototype.getUTCMilliseconds()` 方法以世界时为标准，返回一个指定的日期对象的毫秒数。返回一个 0 到 999 的整数。

    ```javascript
    var d = new Date(); // Thu Dec 14 2017 13:23:42 GMT+0800 (中国标准时间)
    console.log(d.getUTCMilliseconds()); //  603
    ```

- `Date.prototype.getUTCMinutes()` 方法以世界时为标准，返回一个指定的日期对象的分钟数。返回一个 0 到 59 的整数。

    ```javascript
    var d = new Date(); // Thu Dec 14 2017 13:23:42 GMT+0800 (中国标准时间)
    console.log(d.getUTCMinutes()); //  23
    ```

- `Date.prototype.getUTCMonth()` 返回一个 0 到 11 的整数，分别对应以下月份：0 代表一月，1 代表二月，2 代表三月，依次类推。

    ```javascript
    var d = new Date(); // Thu Dec 14 2017 13:23:42 GMT+0800 (中国标准时间)
    console.log(d.getUTCMonth()); //  11
    ```

- `Date.prototype.getUTCSeconds()` 方法以世界时为标准，返回一个指定的日期对象的秒数。返回一个 0 到 59 的整数。

    ```javascript
    var d = new Date(); // Thu Dec 14 2017 13:23:42 GMT+0800 (中国标准时间)
    console.log(d.getUTCSeconds()); //  28
    ```

- `Date.prototype.getYear()` 方法返回指定的本地日期的年份。因为 getYear 不返回千禧年`[full years]("year 2000 problem")`，所以这个方法不再被使用，现在替换为 `getFullYear` .

- `Date.prototype.setDate()` 方法根据本地时间来指定一个日期对象的天数。 一个整数，表示该月的第几天。

    ```javascript
    var d = new Date();
    console.log(d); // Thu Dec 14 2017 15:04:59 GMT+0800 (中国标准时间)
    console.log(d.setDate(20)); //  1513753499372
    console.log(d); // Wed Dec 20 2017 15:04:59 GMT+0800 (中国标准时间)
    ```

- `Date.prototype.setFullYear()` 

    > **语法**

        dateObj.setFullYear(yearValue[, monthValue[, dayValue]])
    
    > **参数**
    
        yearValue   指定年份的整数值，例如1995。
        monthValue  一个0到11之间的整数值，表示从一月到十二月。
        dayValue    一个1到31之间的整数值，表示月份中的第几天。如果你指定了 dayValue 参数，就必须同时指定 monthValue。
    
    > **描述**
    
        如果没有指定 monthValue 和dayValue 参数，将会使用 getMonth 和getDate 方法的返回值。
        如果有一个参数超出了合理的范围，setFullYear 方法会更新其他参数值，日期对象的日期值也会被相应更新。 
        例如，为 monthValue 指定 15， 则年份会加1，月份值会为3。

    ```javascript
    var d = new Date(); 
    console.log(d); // Thu Dec 14 2017 15:05:39 GMT+0800 (中国标准时间)
    console.log(d.setFullYear(2018)); //  1544771139176
    console.log(d); // Fri Dec 14 2018 15:05:39 GMT+0800 (中国标准时间)
    console.log(d.setFullYear(2018, 4, 3)); //  1525331139176
    console.log(d); // Thu May 03 2018 15:05:39 GMT+0800 (中国标准时间)
    ```

- `Date.prototype.setHours()` 方法根据本地时间为一个日期对象设置小时数，返回从1970-01-01 00:00:00 UTC 到更新后的 日期 对象实例所表示时间的毫秒数。

    > **语法**
    
        dateObj.setHours(hoursValue[, minutesValue[, secondsValue[, msValue]]])
    
    > **JavaScript 1.3版本之前
    
        dateObj.setHours(hoursValue)

    > **参数**
        
        hoursValue  一个 0 到 23 的整数，表示小时。
        minutesValue    一个 0 到 59 的整数，表示分钟。
        secondsValue    一个 0 到 59 的整数，表示秒数。如果指定了 secondsValue 参数，则必须同时指定 minutesValue 参数。
        msValue     一个 0 到 999 的数字，表示微秒数，如果指定了 msValue 参数，则必须同时指定 minutesValue 和 secondsValue 参数。
       
    > **描述**
    
        如果不指定 minutesValue，secondsValue 和 msValue 参数，则会使用getMinutes()，getSeconds() 和getMilliseconds() 方法的返回值。
        如果有一个参数超出了合理范围，setHours 会相应地更新日期对象中的日期信息。例如，如果为 secondsValue 指定了 100，则分钟会加 1，然后秒数使用 40。

    ```javascript
    var d = new Date();  
    console.log(d); // Thu Dec 14 2017 15:07:01 GMT+0800 (中国标准时间)
    console.log(d.setHours(22)); //  1513260421525
    console.log(d); // Thu Dec 14 2017 22:07:01 GMT+0800 (中国标准时间)
    console.log(d.setHours(22, 10, 12)); //  1513260612525
    console.log(d); // Thu Dec 14 2017 22:10:12 GMT+0800 (中国标准时间)
    ```

- `Date.prototype.setMilliseconds()` 方法会根据本地时间设置一个日期对象的豪秒数。一个 0 到 999 的数字，表示豪秒数。
如果指定的数字超出了合理范围，则日期对象的时间信息会被相应地更新。例如，如果指定了 1005，则秒数加 1，豪秒数为 5。

    ```javascript
    var d = new Date(); 
    console.log(d); // Thu Dec 14 2017 15:07:44 GMT+0800 (中国标准时间)
    console.log(d.setMilliseconds(100)); //  1513235264100
    console.log(d); // Thu Dec 14 2017 15:07:44 GMT+0800 (中国标准时间)
    ```

- `Date.prototype.setMinutes()` 方法根据本地时间为一个日期对象设置分钟数。

    > **语法**
    
        dateObj.setMinutes(minutesValue[, secondsValue[, msValue]])
    
    > **JavaScript 1.3之前版本**
    
        dateObj.setMinutes(minutesValue)
    
    > **参数**
        
        minutesValue    一个 0 到 59 的整数，表示分钟数。
        secondsValue    一个 0 到 59 的整数，表示秒数。如果指定了 secondsValue 参数，则必须同时指定 minutesValue 参数。
        msValue     一个 0 到 999 的数字，表示微秒数，如果指定了 msValue 参数，则必须同时指定 minutesValue 和secondsValue 参数。
        
    > **描述**
    
        如果没有指定 secondsValue 和 msValue 参数，就会使用 getSeconds() 和 getmilliseconds() 方法的返回值。
        如果有一个指定的参数超出了合理范围，setMinutes 会相应地更新日期对象中的时间信息。
        例如，为 secondsValue 指定 100，分钟数将会加 1，而秒数会为 40。

    ```javascript
    var d = new Date(); 
    console.log(d); // Thu Dec 14 2017 15:08:25 GMT+0800 (中国标准时间)
    console.log(d.setMinutes(32)); //  1513236745480
    console.log(d); // Thu Dec 14 2017 15:32:25 GMT+0800 (中国标准时间)
    console.log(d.setMinutes(32, 25, 125)); //  1513236745125
    console.log(d); // Thu Dec 14 2017 15:32:25 GMT+0800 (中国标准时间)
    ```

- `Date.prototype.setMonth()` 方法根据本地时间为一个设置年份的日期对象设置月份。
    
    > **语法**
    
        dateObj.setMonth(monthValue[, dayValue])

    > **JavaScript 1.3版本之前**
    
        dateObj.setMonth(monthValue)

    > **参数**
    
        monthValue 介于 0 到 11 之间的整数（表示一月到十二月）。
        dayValue 从 1 到 31 之间的整数，表示月份中的第几天。
        返回值！ 基于 1 January 1970 00:00:00 UTC 开始计算的毫秒数
   
    > **描述**
        如果不指定 dayValue 参数，就会使用 getDate 方法的返回值。
        如果有一个指定的参数超出了合理范围，setMonth 会相应地更新日期对象中的日期信息。
        例如，为 monthValue 指定 15，则年份会加 1，月份将会使用 3。
        
    ```javascript
    var d = new Date();  
    console.log(d); // Thu Dec 14 2017 15:09:10 GMT+0800 (中国标准时间)
    console.log(d.setMonth(6)); //  1500016150361
    console.log(d); // Fri Jul 14 2017 15:09:10 GMT+0800 (中国标准时间)
    console.log(d.setMonth(6, 25)); //  1500966550361
    console.log(d); // Tue Jul 25 2017 15:09:10 GMT+0800 (中国标准时间)
    ```

- `Date.prototype.setSeconds()`  方法根据本地时间设置一个日期对象的秒数。

    > **语法**
    
        dateObj.setSeconds(secondsValue[, msValue])
    
    > **JavaScript 1.3之前版本**
    
        dateObj.setSeconds(secondsValue)
    
    > **参数**
        secondsValue  一个 0 到 59 的整数。
        msValue  一个 0 到 999 的数字，表示微秒数。
    
    > **描述**
    
        如果没有指定 msValue 参数，就会使用 getMilliseconds() 方法的返回值。
        如果一个参数超出了合理范围， setSeconds 方法会相应地更新日期对象的时间信息。
        例如，为 secondsValue 指定 100，则日期对象的分钟数会相应地加 1，秒数将会使用 40。

    ```javascript
    var d = new Date();  
    console.log(d); // Thu Dec 14 2017 15:16:00 GMT+0800 (中国标准时间)
    console.log(d.setSeconds(30)); //  1513235790738
    console.log(d); // Thu Dec 14 2017 15:16:30 GMT+0800 (中国标准时间)
    console.log(d.setSeconds(40, 250)); //  1513235800250
    console.log(d); // Thu Dec 14 2017 15:16:40 GMT+0800 (中国标准时间)
    ```

- `Date.prototype.setTime()`  方法以一个表示从1970-1-1 00:00:00 UTC计时的毫秒数为来为 Date 对象设置时

    ```javascript
    var oldDay = new Date("July 1, 1990");
    var d = new Date();
    d.setTime(oldDay.getTime()); // 646761600000
    console.log(d); //  Sun Jul 01 1990 00:00:00 GMT+0800 (中国标准时间)
    ```

- `Date.prototype.setUTCDate(dayValue)` 方法就是根据全球时间设置特定date对象的日期。 dayValue是一个1-31的整形数字，用来指定日期。

    ```javascript
    var d = new Date();
    console.log(d); //  Thu Dec 14 2017 15:22:05 GMT+0800 (中国标准时间)
    console.log(d.setUTCDate(24)); // 1514100125177
    console.log(d); //Sun Dec 24 2017 15:22:05 GMT+0800 (中国标准时间)
    ```

- `Date.prototype.setUTCFullYear()` 方法根据世界标准时间为一个具体日期设置年份。
    
    > **语法**
    
        dateObj.setUTCFullYear(yearValue[, monthValue[, dayValue]])
    
    > **参数**
    
        yearValue 指定年份整数值，例如，1995
        monthValue 可选。指定一个0-11之间的整数值，代表从一月到十二月。
        dayValue 可选。指定一个1-31之间的整数值，代表月份中的第几天。如果你指定了dayValue参数，那么你必须指定monthValue参数。
        
    > **描述**
    
        如果你没有指定具体的monthValue和dayValue，将会使用 getUTCMonth 和getUTCDate 方法的返回值。
        如果你指定的参数超出了期待范围，setUTCFullYear()方法将会根据Date对象，更新其他参数和日期信息。
        例如，如果你将monthValue设定为15，年份会增加1，月份值则为为3。
        
    ```javascript
    var d = new Date();
    console.log(d); //  Thu Dec 14 2017 15:22:05 GMT+0800 (中国标准时间)
    console.log(d.setUTCFullYear(2018)); // 1544772206483
    console.log(d); // Fri Dec 14 2018 15:23:26 GMT+0800 (中国标准时间)
    console.log(d.setUTCFullYear(2018, 4, 3)); // 1525332409427
    console.log(d); // Thu May 03 2018 15:26:49 GMT+0800 (中国标准时间)
    ```

- `Date.prototype.setUTCHours()` 方法用于根据世界时 (UTC) 设置小时（0 - 23）。 该方法可用于设置分钟数，秒数以及毫米数。
    
    > **语法**
    
        Date.setUTCHours(hour,min,sec,millisec)
  
    > **参数**  
    
        hour    必需。要给 dateObject 设置的小时字段的值。
                该参数是 0 ~ 23 之间的整数：
                -1 为前一天的最后一个小时。
                24 为明天的第一个小时

        min     可选。要给 date Object 设置的分钟字段的值。
                该参数是 0 ~ 59 之间的整数：
                -1 为前一小时的最后一分钟
                60 为下一小时的第一分钟

        sec     可选。要给 date Object 设置的秒字段的值。
                该参数是 0 ~ 59 之间的整数：
                -1 为前一分钟的最后一秒
                60 为下一分钟的第一秒
        millisec    可选。要给 date Object 设置的毫秒字段的值。
        
                该参数是 1 ~ 999 之间的整数：
                -1 为前一秒钟的最后一毫秒数
                1000 为下一秒钟的第一毫秒数

    ```javascript
    var d = new Date();
    console.log(d); //  Thu Dec 14 2017 15:31:28 GMT+0800 (中国标准时间)
    console.log(d.setUTCHours(10)); // 1513247488164
    console.log(d); // Thu Dec 14 2017 18:31:28 GMT+0800 (中国标准时间)
    console.log(d.setUTCHours(10, 13, 14, 403)); // 1513246394403
    console.log(d); // Thu Dec 14 2017 18:13:14 GMT+0800 (中国标准时间)
    ```

- `Date.prototype.setUTCMilliseconds()` 方法用于根据世界时 (UTC) 设置指定时间的毫秒。
    
    > **语法**
        
        Date.setUTCMilliseconds(millisec)
    
    > **参数**
    
        millisec    必需。要给 dateObject 设置的毫秒字段的值。使用世界时表示。
                    该参数是 0 ~ 999 之间的整数：
                    -1 为上一秒钟的最后1毫秒
                    1000 为下一秒中的第一毫秒
                    1001 为下一秒中的第二毫秒

    ```javascript
    var d = new Date();
    console.log(d); //  Thu Dec 14 2017 15:34:57 GMT+0800 (中国标准时间)
    console.log(d.setUTCMilliseconds(520)); // 1513236897520
    console.log(d); // Thu Dec 14 2017 15:34:57 GMT+0800 (中国标准时间)
    ```

- `Date.prototype.setUTCMinutes()`  方法用于根据世界时 (UTC) 来设置指定时间的分钟

    > **语法**
    
        Date.setUTCMinutes(min,sec,millisec)
    
    > **参数** 
    
        min 必需。要给 date Object 设置的分钟字段的值，用世界时表示。
                该参数应该是 0 ~ 59 之间的整数：
                -1 为上一分钟的最后一秒
                60 为下一分钟的第一秒

        sec 可选。要给 dateObject 设置的秒字段的值。使用世界时表示。
                该参数是 0 ~ 59 之间的整数：
                -1 为上一分钟的最后一秒
                60 为下一分钟的第一秒

        millisec    可选。要给 date Object 设置的毫秒字段的值。使用世界时表示。
                该参数是 0 ~ 999 之间的整数：
                -1 为上一秒钟的最后1毫秒
                1000 为下一秒中的第一毫秒

    ```javascript
    var d = new Date();
    console.log(d); //  Thu Dec 14 2017 15:38:05 GMT+0800 (中国标准时间)
    console.log(d.setUTCMinutes(25)); // 1513236305568
    console.log(d); // Thu Dec 14 2017 15:25:05 GMT+0800 (中国标准时间)
    console.log(d.setUTCMinutes(25, 35, 140)); // 1513236335140
    console.log(d); // Thu Dec 14 2017 15:25:35 GMT+0800 (中国标准时间)
    ```

- `Date.prototype.setUTCMonth()` 方法用于根据世界时 (UTC) 来设置月份。

    > **语法**
    
        Date.setUTCMonth(month,day)
     
    > **参数**
    
    month   必需。要给 dateObject 设置的月份字段的值，用世界时表示。
            该参数是 0（一月） ~ 11（十二月） 之间的整数:
            -1 为上一年的最后一月。
            12 为下一年的第一个月。
            13 为下一年的第二月。

    day 可选。月份中的某一天。
        在 1 ~ 31 之间的整数，用作 date Object 的天字段，用世界时表示。
            0 为上一个月的最后一小时。
            -1 为上一个月最后一小时之前的小时时间。
        如果当月有31天：
            32 为下一个月的第一天。
        如果当月有30天：
            32 为下一个月的第二天。

    ```javascript
    var d = new Date();
    console.log(d); //  Thu Dec 14 2017 15:40:40 GMT+0800 (中国标准时间)
    console.log(d.setUTCMonth(4)); // 1494747640425
    console.log(d); // Sun May 14 2017 15:40:40 GMT+0800 (中国标准时间)
    console.log(d.setUTCMonth(4, 3)); // 1493797240425
    console.log(d); // Wed May 03 2017 15:40:40 GMT+0800 (中国标准时间)
    ```

- `Date.prototype.setUTCSeconds()` 方法用于根据世界时 (UTC) 设置指定时间的秒字段。  

    > **语法**
    
        Date.setUTCSeconds(sec,millisec)
     
    > **参数**
    
        sec  必需。要给 dateObject 设置的秒字段的值。使用世界时表示。
            该参数是 0 ~ 59 之间的整数：
            -1 为上一分钟的最后一秒
            60 为下一分钟的第一秒

        millisec  可选。要给 dateObject 设置的毫秒字段的值。使用世界时表示。
                该参数是 0 ~ 999 之间的整数：
                -1 为上一秒钟的最后1毫秒
                1000 为下一秒中的第一毫秒

    ```javascript
    var d = new Date();
    console.log(d); //  Thu Dec 14 2017 15:43:00 GMT+0800 (中国标准时间)
    console.log(d.setUTCSeconds(35)); // 1513237415005
    console.log(d); // Thu Dec 14 2017 15:43:35 GMT+0800 (中国标准时间)
    console.log(d.setUTCSeconds(35, 350)); // 1513237415350
    console.log(d); // Thu Dec 14 2017 15:43:35 GMT+0800 (中国标准时间)
    ```

- `Date.prototype.setYear()` <font color=red>已废弃</font>。请使用 setFullYear() 方法代替。

- `Date.prototype.toDateString()` 返回一个日期对象日期部分的字符串。

    ```javascript
    var d = new Date();
    console.log(d); //  Thu Dec 14 2017 15:45:16 GMT+0800 (中国标准时间)
    console.log(d.toDateString()); //  Thu Dec 14 2017
    ```

- `Date.prototype.toGMTString()` <font color=red>已废弃</font>。请使用 toUTCString() 方法代替。

- `Date.prototype.toISOString()` 方法返回一个 ISO（ISO 8601 Extended Format）格式的字符串： YYYY-MM-DDTHH:mm:ss.sssZ。时区总是UTC（协调世界时），加一个后缀“Z”标识。

    ```javascript
    var d = new Date();
    console.log(d); //  Thu Dec 14 2017 15:47:02 GMT+0800 (中国标准时间)
    console.log(d.toISOString()); //  2017-12-14T07:47:02.427Z
    ```

- `Date.prototype.toJSON()` 方法可以将 Date 对象转换为字符串，并格式化为 JSON 数据格式.JSON 数据用同样的格式就像x ISO-8601 标准: YYYY-MM-DDTHH:mm:ss.sssZ

    ```javascript
    var d = new Date();
    console.log(d); //  Thu Dec 14 2017 15:48:08 GMT+0800 (中国标准时间)
    console.log(d.toJSON()); //  2017-12-14T07:48:08.121Z
    ```

- `Date.prototype.toLocaleDateString()` 根据本地时间把 Date 对象的<font color=red>日期部分</font>转换为字符串

    ```javascript
    var d = new Date();
    console.log(d); //  Thu Dec 14 2017 15:48:08 GMT+0800 (中国标准时间)
    console.log(d.toLocaleDateString()); //  2017/12/14
    ```

- `Date.prototype.toLocaleFormat()` <font color=red>非标准</font>，chrome不支持

- `Date.prototype.toLocaleDateString()` 根据本地时间格式，把 Date 对象的日期部分转换为字符串，该字符串格式因不同语言而不同。新增的参数 locales 和 options 使程序能够指定使用哪种语言格式化规则，
允许定制该方法的表现（behavior）。在旧版本浏览器中， locales 和 options 参数被忽略，使用的语言环境和返回的字符串格式是各自独立实现的。

- `Date.prototype.toLocaleTimeString()` 根据本地时间格式，把 Date 对象的时间部分转换为字符串，该字符串格式因不同语言而不同。新增的参数 locales 和 options 使程序能够指定使用哪种语言格式化规则，
允许定制该方法的表现（behavior）。在旧版本浏览器中， locales 和 options 参数被忽略，使用的语言环境和返回的字符串格式是各自独立实现的。
    
- `Date.prototype.toLocaleString()` 据本地时间格式，把 Date 对象转换为字符串，该字符串格式因不同语言而不同。新增的参数 locales 和 options 使程序能够指定使用哪种语言格式化规则，
允许定制该方法的表现（behavior）。在旧版本浏览器中， locales 和 options 参数被忽略，使用的语言环境和返回的字符串格式是各自独立实现的。

    > **语法**
    
        dateObj .toLocaleString（[ locales [，options ]]）
    
    > **参数**
    
        检查浏览器兼容性部分以查看哪些浏览器支持locales和options参数，以及示例：检查localesoptions功能检测的支持和参数。

        locales
            可选的。一个带有BCP 47语言标签的字符串或这种字符串的数组。有关参数的一般形式和解释locales，请参阅Intl页面。以下Unicode扩展键是被允许的：

            nu
                编号系统。可能的值包括："arab"，"arabext"，"bali"，"beng"，"deva"，"fullwide"，"gujr"，"guru"，"hanidec"，"khmr"，
                "knda"，"laoo"，"latn"，"limb"，"mlym"，"mong"，"mymr"，"orya"，"tamldec"，"telu"，"thai"，"tibt"。
            ca
                日历。可能的值包括："buddhist"，"chinese"，"coptic"，"ethioaa"，"ethiopic"，"gregory"，"hebrew"，"indian"，"islamic"，
                "islamicc"，"iso8601"，"japanese"，"persian"，"roc"。
            hc
                小时周期。可能的值包括："h11"，"h12"，"h23"，"h24"。
        
        options
            可选的。具有部分或全部以下属性的对象：

            localeMatcher
                要使用的语言环境匹配算法。可能的值是"lookup"和"best fit"; 默认是"best fit"。有关此选项的信息，请参阅Intl页面。
            timeZone
                要使用的时区。唯一的价值实现必须认识到的是"UTC"; 默认是运行时的默认时区。实现也可以识别的时区名称IANA时区数据库，
                如"Asia/Shanghai"，"Asia/Kolkata"，"America/New_York"。
            hour12
                是否使用12小时的时间（而不是24小时的时间）。可能的值是true和false; 默认值是语言环境相关的。
                如果两者都存在，此选项将覆盖hc语言标记和/或  hourCycle选项。
            hourCycle
                小时周期使用。可能的值是"h11"，"h12"，"h23"，或"h24"。hc如果两者都存在，则此选项将覆盖语言标记，
                如果hour12指定了这两个选项，则该选项优先。
            formatMatcher
                要使用的格式匹配算法。可能的值是"basic"和"best fit"; 默认是"best fit"。有关使用此属性的信息，请参阅以下段落。
            
                以下属性描述了格式化输出中使用的日期时间组件以及它们所需的表示。实现需要至少支持以下子集：
                    weekday，year，month，day，hour，minute，second
                    weekday，year，month，day
                    year，month，day
                    year， month
                    month， day
                    hour，minute，second
                    hour， minute
            
                实现可以支持其他子集，并且将针对所有可用的子集表示组合来协商请求以找到最佳匹配。
                两种算法可用于此协商并由formatMatcher属性选择：完全指定的"basic"算法和依赖于实现的"best fit"算法。

                    weekday
                        周日的表示。可能的值是"narrow"，"short"，"long"。
                    era
                        时代的代表。可能的值是"narrow"，"short"，"long"。
                    year
                        年的表示。可能的值是"numeric"，"2-digit"。
                    month
                        月份的表示。可能的值是"numeric"，"2-digit"，"narrow"，"short"，"long"。
                    day
                        一天的表示。可能的值是"numeric"，"2-digit"。
                    hour
                        小时的表示。可能的值是"numeric"，"2-digit"。
                    minute
                        分钟的表示。可能的值是"numeric"，"2-digit"。
                    second
                        第二个的表示。可能的值是"numeric"，"2-digit"。
                    timeZoneName
                        时区名称的表示。可能的值是"short"，"long"。
                
                每个日期时组件属性的默认值是undefined，但如果weekday，year，month，day，hour，minute，second性质都是undefined，
                然后year，month，day，hour，minute，和second被认为是"numeric"。
        
    ```javascript
    /**
     * 在没有指定语言环境的基本使用中，将返回默认语言环境中的格式化字符串和默认选项。
     */
    var d = new Date();
    console.log(d); //  Thu Dec 14 2017 16:52:31 GMT+0800 (中国标准时间)
    console.log(d.toLocaleString()); //  2017/12/14 下午4:07:23
    console.log(d.toLocaleDateString()); //  2017/12/14
    console.log(d.toLocaleTimeString()); //  下午4:52:31

    /**
     *  检查支持locales和options参数
     *  在locales和options参数都无法在所有浏览器都支持呢。要检查一个实现是否已经支持它们，
     *  你可以使用非法语言标签被拒绝的RangeError例外情况：
     */
    function toLocaleStringSupportsLocales() {
      try {
        new Date().toLocaleString('i');
      } catch (e) {
        return e instanceof RangeError;
      }
      return false;
    }

    /**
     * 运用 locales
     * 本示例显示了本地化日期和时间格式中的一些变体。为了获得应用程序用户界面中使用的语言格式，
     * 请确保使用locales参数指定该语言（可能还有一些备用语言）：
     */

    var date = new Date();
    console.log(date); //  Thu Dec 14 2017 17:02:32 GMT+0800 (中国标准时间)

    //假定本地时区是 America/Los_Angeles(美国时区)
    //en-US(美利坚英语)使用 month-day-year 的顺序展示年月日
    console.log(date.toLocaleString("en-US")); // → 12/14/2017, 5:02:32 PM
    console.log(date.toLocaleDateString("en-US")); //  12/14/2017
    console.log(date.toLocaleTimeString("en-US")); //  5:02:32 PM

    // en-GB(不列颠英语)使用 day-month-year 顺序展示年月日
    console.log(date.toLocaleString("en-GB")); // → 14/12/2017, 17:02:32
    console.log(date.toLocaleDateString("en-GB")); //  14/12/2017
    console.log(date.toLocaleTimeString("en-GB")); //  17:02:32

    // 韩语使用 year-month-day 顺序展示年月日
    console.log(date.toLocaleString("ko-KR"));  // → 2017. 12. 14. 오후 5:02:32
    console.log(date.toLocaleDateString("ko-KR")); //  2017. 12. 14.
    console.log(date.toLocaleTimeString("ko-KR")); //  오후 5:02:32

    // 大多数阿拉伯语国家的阿拉伯语使用阿拉伯数字
    console.log(date.toLocaleString("ar-EG")); // → ١٤‏/١٢‏/٢٠١٧ ٥:٠٢:٣٢ م
    console.log(date.toLocaleDateString("ar-EG")); //  ١٤‏/١٢‏/٢٠١٧
    console.log(date.toLocaleTimeString("ar-EG")); //  ٥:٠٢:٣٢ م

    //在日本，应用可能想要使用日本日历,
    //2012 是平成24年（平成是是日本天皇明仁的年号,由1989年1月8日起开始计算直至现在）
    console.log(date.toLocaleString("ja-JP-u-ca-japanese")); // → 平成29/12/14 17:02:32
    console.log(date.toLocaleDateString("ja-JP-u-ca-japanese")); //  平成29/12/14
    console.log(date.toLocaleTimeString("ja-JP-u-ca-japanese")); //  17:02:32

    //当请求一个语言可能不支持，如巴厘(ban)，若有备用的语言印尼语(id)，
    //那么将使用印尼语(id)
    console.log(date.toLocaleString(["ban", "id"])); // → 14/12/2017 17.02.32
    console.log(date.toLocaleDateString(["ban", "id"])); // 14/12/2017
    console.log(date.toLocaleTimeString(["ban", "id"])); // 17.02.32
    

    /**
     * 运用 options
     * 提供的结果toLocaleString()可以使用options参数自定义：
     */
    
    var date = new Date();
    console.log(date); // Thu Dec 14 2017 17:07:19 GMT+0800 (中国标准时间)

    //请求参数(options)中包含参数星期(weekday)，并且该参数的值为长类型(long)
    var options = {weekday: "long", year: "numeric", month: "long", day: "numeric"};
    console.log(date.toLocaleString("de-DE", options)); // → Donnerstag, 14. Dezember 2017
    console.log(date.toLocaleDateString("de-DE", options)); // Donnerstag, 14. Dezember 2017
    console.log(date.toLocaleTimeString("de-DE", options)); // Donnerstag, 14. Dezember 2017, 17:07:19

    //一个应用使用 世界标准时间(UTC),并且UTC使用短名字(short)展示
    options.timeZone = "UTC";
    options.timeZoneName = "short";//若不写这一行那么仍然显示的是世界标准时间；但是GMT三个字母不会显示
    console.log(date.toLocaleString("en-US", options)); // → Thursday, December 14, 2017, UTC
    console.log(date.toLocaleDateString("en-US", options)); // Thursday, December 14, 2017, UTC
    console.log(date.toLocaleTimeString("en-US", options)); // Thursday, December 14, 2017, 9:07:19 AM UTC

    // 使用24小时制
    console.log(date.toLocaleString("en-US", {hour12: false})); // → 12/14/2017, 17:07:19
    console.log(date.toLocaleTimeString("en-US", {hour12: false})); // 17:07:19
    console.log(date.toLocaleDateString("en-US", {hour12: false})); // 12/14/2017
    ```

- `Date.prototype.toString()` 把 Date 对象转换为字符串。

    ```javascript
    var date = new Date();
    console.log(date.toString()); //  Thu Dec 14 2017 17:10:00 GMT+0800 (中国标准时间)
    ```

- `Date.prototype.toTimeString()` 把 Date 对象的时间部分转换为字符串。

    ```javascript
    var date = new Date();
    console.log(date.toTimeString()); // 17:10:21 GMT+0800 (中国标准时间)
    ```
 
- `Date.prototype.toUTCString()` 根据世界时，把 Date 对象转换为字符串。

    ```javascript
    var date = new Date();
    console.log(date.toUTCString()); // Thu, 14 Dec 2017 09:11:06 GMT
    ```

- `Date.prototype.valueOf()`  返回 Date 对象的原始值。date 的毫秒表示。返回值和方法 Date.getTime 返回的值相等,返回1970年1月1日午夜以来的毫秒数

    ```javascript
    var date = new Date();
    console.log(date.valueOf()); // 1513242700928
    ```

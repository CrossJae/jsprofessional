# 第五章 引用类型

## Date类型

1. 创建Date实例的方法
    ```
    var now = new Date();
    ```
    不同浏览器now的值是有差异的

2. [方法](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Date)
```
Date.UTC()//Date.UTC(2017,7,3) -> 1499011200000
Date.now()//1499011200000
Date.parse()//Date.parse('2017-7-3') -> 1499011200000
//get
Date.prototype.getYear()// 弃用
Date.prototype.getFullYear()//年
Date.prototype.getMonth()//月
Date.prototype.getDate()//日期
Date.prototype.getDay()//星期
Date.prototype.getHours()//时
Date.prototype.getMinutes()//分
Date.prototype.getSeconds()//秒
Date.prototype.getMilliseconds()//毫秒
Date.prototype.getTime()//时间戳
Date.prototype.valueOf()//时间戳
//get-UTC
Date.prototype.getUTCFullYear()
Date.prototype.getUTCMonth()
Date.prototype.getUTCDate()
Date.prototype.getUTCDay()
Date.prototype.getUTCHours()
Date.prototype.getUTCMinutes()
Date.prototype.getUTCSeconds()
Date.prototype.getUTCMilliseconds()
//get-other
Date.prototype.getTimezoneOffset()//UTC时间距当前时间的时间差（分钟）

//set
Date.prototype.setYear()//弃用
Date.prototype.setFullYear()
Date.prototype.setMonth()
Date.prototype.setDate()
Date.prototype.setHours()
Date.prototype.setMinutes()
Date.prototype.setSeconds()
Date.prototype.setMilliseconds()
Date.prototype.setTime()

//set-UTC
Date.prototype.setUTCFullYear()
Date.prototype.setUTCMonth()
Date.prototype.setUTCDate()
Date.prototype.setUTCHours()
Date.prototype.setUTCMinutes()
Date.prototype.setUTCSeconds()
Date.prototype.setUTCMilliseconds()

//tostring
Date.prototype.toString()//转成字符串
Date.prototype.toJSON()//相当于调用了toISOString()
Date.prototype.toGMTString()//Wed, 05 Jul 2017 07:54:18 GMT，弃用
Date.prototype.toUTCString()//Wed, 05 Jul 2017 07:54:18 GMT
Date.prototype.toLocaleString()//2017-7-5 15:54:18
Date.prototype.toISOString()//2017-07-05T07:54:18.451Z
Date.prototype.toDateString()//Wed Jul 05 2017
Date.prototype.toTimeString()//18:49:07 GMT+0800 (CST)
Date.prototype.toLocaleDateString()//2017/7/5
Date.prototype.toLocaleTimeString()//下午6:51:35
Date.prototype.toLocaleFormat()//

// dont known
Date.prototype[@@toPrimitive]//
Date.prototype.toSource()//
```

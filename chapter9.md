# 客户端检测

**不到万不得已，不要使用客户端检测**
### 能力检测 - 确定客户端支持什么能力
* 简单的能力检测，检测某个函数是否存在等
```
if(object.sort){...} // 项目中经常使用此方法来判断是端内还是端外
```
* 尽量使用typeof作为能力检测的依据，比如
```
typeof 'abc'; // string
typeof 123; // number
typeof true; // boolean
typeof []; // object
typeof {}; // object
typeof null; // object
typeof undefined; // undefined
typeof function(){}; // function
typeof a; // undefined
```
所以，null / [] / {} 不能用typeof判断出来。
判断对象是不是数组的方法
```
if(Object.prototype.toString.call(o) === '[Object Array]'){ alert '是数组'}
```
原理，Object原型上的toString方法返回的是对象内部属性`[Object type]`，比如
```
var o = new Object();
o.toString(); // returns [object Object]
```
**之所以不用`o.toString()`而是用`Object.prototype.toString.call(o)`，是因为Array和其他对象可能会重写toString方法，并不会返回`[Object type]`**
* 双逻辑非操作的作用是什么？
* 不要把能力检测当作浏览器检测使用，比如
```
// 为检测IE，判断document.all和document.uniqueID两种属性都存在，这相当于假设了未来IE都会继续支持这两种属性
var isIE = !!(document.all && document.uniqueID);
```

### 怪癖检测（quirk detection） - 确定客户端有什么缺陷
* 怪癖检测需要运行一段代码，建议在代码开头执行怪癖检测，及早发现问题。
* 针对特定浏览器的某个怪癖的检测，实际应用场景未在具体项目中见过。

### 用户代理检测 `navigator.userAgent`
* 用户代理是客户端检测的最后一种选择，因为对用户代理字符串具有很强的依赖性，用户代理字符串在发展的过程中，浏览器提供商曾在其中放入欺骗性信息，让服务端无法分辨具体的浏览器类型。

*-end-*

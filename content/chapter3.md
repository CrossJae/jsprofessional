# 第三章 基本概念

* 包括：语法、操作符、数据类型、内置功能 

## 语法
* 区分大小写
* 标识符：第一个字符必须是字母a-zA-Z、下划线_、美元符$
* 注释
* 严格模式：`use strict`，表示编译指示
* 语句：分号结尾

## 操作符
* 一元操作符：`++`和`--`，比如`num++`
* 位操作符：
* 布尔操作符：两个逻辑非操作符，相当于模拟Boolean的结果，比如`!!num`相当于`Boolean(num)`
* 乘性操作符
* 加性操作符
* 关系操作符
* 相等操作符
* 条件操作符
* 赋值操作符
* 逗号操作符：`var a=1, b=2, c=3`

## 数据类型
* typeof
* Undefined
* Null
* Boolean
* Number
* String
* Object
  * Object的实例（ES中所有对象）都具有的属性和方法：(`Object.prototype`)
    * constructor
    * hasOwnProperty(*propertyName*) - `o.hasOwnProperty("name")`
    * isPrototypeOf(object)
    * propertyIsEnumberable(propertyName) - 检测是否可以通过for-in循环
    * toLocaleString()
    * toString()
    * valueOf()

## 保留字和关键字
## 变量 - ES变量是松散型的

## 语句
1. if
2. do-while 后测试循环语句
3. while 前测试循环语句
4. for 前测试循环语句，功能同while
5. for-in 迭代语句，枚举对象的属性
  * for (variable in object) {...}
  * 对象的属性没有顺序，所以通过for-in循环输出的属性名的顺序是不可预测的，因浏览器而异。迭代array也是一样，顺序不可测。
  * 要迭代的对象值为null或undefined，for-in会抛出错误，建议在迭代之前，先检测该对象的值不是null或undefined。
  ```
  var person = {
    name : 'Jack',
    age : 25,
    job : fe
  }
  for(var item in person){
    console.log(item); // 'name','age','job'
    console.log(person[item]); // 'Jack',25,'fe'
  }
  ```
6. label
  * 只能和break continue一起使用，不经常被使用
7. break continue
8. with
```
with(location){
  var qs = search.substring(1); // location.search
  var hostName = hostmame; // location.hostname
  var url = href; //location.href
}
```
9. switch

## 函数
1.  函数中，return后面的代码都不会执行
2.  js中，对函数的参数个数、数据类型都不作限制
3.  函数参数是数组形式，arguments与数组类似，但并不是array的实例，arguments.length，arguments[0]
*-end-*

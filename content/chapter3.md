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
    * hasOwnProperty(propertyName) - `o.hasOwnProperty("name")`
    * isPrototypeOf(object) - `Object.prototype.isPrototypeOf(obj)`
    * propertyIsEnumberable(propertyName) - 检测是否可以通过for-in循环 `o.propertyIsEnumberable("name")`
    * toLocaleString()
    * toString() - 常用`Object.prototype.toString.call(fn)`
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
  * 要迭代的对象值为null或undefined，for-in会抛出错误(ES5不再抛出)，建议在迭代之前，**先检测该对象的值不是null或undefined**。
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
6. label（只能和break continue一起使用，不经常被使用）
7. break continue（break彻底退出循环，continue结束本次循环）
8. with（不建议）
```
with(location){
  var qs = search.substring(1); // location.search
  var hostName = hostmame; // location.hostname
  var url = href; //location.href
}
```
9. switch（常用来判断接口返回情况）
  ```
  switch(res.body.code){
    case 12001:
      //
      break;
    case 12002:
      //
      break;
    default:
      //
      breank;
  }
  ```

## 函数
* 函数中，return后面的代码都不会执行，return不带任何值返回即为返回undefined，目的是为了终止函数执行
* js中，对函数的参数个数、数据类型都不作限制
* 函数参数是数组形式，arguments与数组类似，但并不是array的实例，`arguments.length`，`arguments[0]`
  ```
  // 典型的值传递例子
  function setName(obj){
      obj.name = 'XX'    //参数按值传递，但obj和person访问的是同一个对象，修改对象会表现在参数person上
      obj = new Object() //注意这里obj变量引用变掉了,如果是传递的引用，person也会变掉
      obj.name = 'YY'
  }
  var person = new Object()
  setName(person)
  console.log(person.name)//输出'XX'
  ```

## 补充：命名
1. 好的代码胜过好的注释，优化代码的可读性，减少不必要的注释。
2. 规范
  1. 避免抽象的名字
  2. 在名字中增加额外信息
  3. 有目的的使用大小写、下划线命名
    1. CamelCase表示类名
    2. lower_separated表示变量名
    3. CONSTANT_NAME表示常量
    4. $all_images表示jQuery返回的结果
3. 为大作用域采用更长的名字
4. 使用不会被误解的名字
5. 使用英文命名

*-end-*

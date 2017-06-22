# 第三章 基本概念

## 语句

1. if
  * if (condition) statement1 else statement2
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
9. switch

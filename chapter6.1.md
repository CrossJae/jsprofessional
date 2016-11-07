# 第六章 面向对象的程序设计

## 理解对象（了解即可）

1. 属性类型
    1. 数据属性
        1. [[configurable]]：是否可以通过delete属性重新定义属性，默认true
        2. [[enumberable]]：是否可以for-in循环返回属性，默认true
        3. [[writable]]：是否可修改属性，默认true
        4. [[value]]：属性的数据值，默认undefined
    2. 访问器属性
        1. [[configurable]]：是否可以通过delete属性重新定义属性，默认true
        2. [[enumberable]]：是否可以for-in循环返回属性，默认true
        3. [[get]]：在读取属性时调用的函数，默认undefined
        4. [[set]]：在写入属性时调用的函数，默认undefined
2. 修改属性的方法object.defineProperty()
3. 定义多个属性object.defineProperties()
4. 读取属性的特性object.getOwnPropertyDescriptor()
5. 引申
    * _year，_代表一种只能通过对象方法访问属性的命名方式
# 第四章 变量、作用域和内存问题

*重点是总结部分，4.1.3*
## 关键词：
* JS变量可以保存两种类型的值：
    1. 基本数据类型（保存在栈内存中）：undefined、null、string、number、boolean
    2. 引用数据类型（保存在堆内存中）：object
* 检验数据类型的方式：
    1. 确定值是哪种基本类型：typeof
    2. 确定值是哪种引用类型：instanceof
* 执行环境 execution context（上下文）：
    1. 全局执行环境（全局环境）
    2. 函数执行环境
* 作用域（作用域链）：当代码在一个环境中执行时，会创建变量对象的一个作用域链（scope chain）。用途是，保证对执行环境有权访问的所有变量和函数的有序的访问。
* 延长作用域的方式：with ； catch try
* 生命周期：局部变量只在函数执行的过程中存在；
* 垃圾回收：
    1. javascript具有自动垃圾收集机制
    2. 分为：标记清除（主流）、引用计数（缺点是会出现循环引用的情况，函数a引用b，函数b引用a）
    ```
    function problem(){
      var objectA = new Object();
      var objectB = new Object();
      objectA.someOtherObject = objectB;
      objectB.anotherObject = objectA;
    }
    ```
* 解除引用dereferencing：将变量（一般是全局变量，局部变量会在离开执行环境时自动被解除引用）设置为null     
  `myObject.element=null`     
  解除引用的真正作用是让值脱离执行环境，以便垃圾收集器下次运行时将其回收。

* 引申阅读：
    1. 栈stack与堆heap的区别
        * 空间分布：栈是系统自动分配释放，堆是程序员分配释放
        * 缓存方式：栈是一级缓存，被调用时处于存储空间，调用完毕立即释放。堆是二级缓存，生命周期由虚拟机的垃圾回收算法决定，所以调用对象的速度相对来得低一些。
        * 数据结构：栈是LIFO（Last-In-First-Out后进先出），堆是树形结构。
    2. 执行环境与作用域

*-end-*

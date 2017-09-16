# 第六章 面向对象的程序设计

## 关键词：

* 关于继承机制：
* 参考阅读：http://www.ruanyifeng.com/blog/2011/06/designing_ideas_of_inheritance_mechanism_in_javascript.html
    1. Javascript里面都是对象，必须有一种机制，将所有对象联系起来。
    2. 不打算引入"类"（class）的概念，因为一旦有了"类"，Javascript就是一种完整的面向对象编程语言了，会变的复杂。
    3. 把new命令引入了Javascript，用来从原型对象生成一个实例对象。在Javascript语言中，new命令后面跟的不是类，而是构造函数。
    4. 用构造函数生成实例对象，无法共享属性和方法。于是为构造函数设置一个prototype属性。
    5. 共享的属性和方法放进prototype对象；不需要共享的属性和方法，放进构造函数中。
    6. 所以，实例对象就“继承”了prototype对象







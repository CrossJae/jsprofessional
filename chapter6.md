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
* 参考阅读《你不知道的javascript上》
  1. 当你通过各种语法（比如`for in`）进行属性查找时都会查找[[Prototype]]链，直到找到属性或者查找完整原型链。
  2. js中的继承并不是普通含义上的继承，因为：继承意味着复制操作，js中并没有复制对象的属性。js会在两个对象之间进行关联，这样一个对象就可以通过委托访问另一个对象的方法和属性。
  3. 构造函数和new很好地满足了一些程序员对于经典类式语法的追求，但它掩盖了很多细节和原理，容易让人产生误解。
  4. ES5终于提供了一个`Object.create()`的方法，用于设置`[[prototype]]`指针。
  6. `new`的原理，指定对象的`[[prototype]]`，并返回一个对象，以下两种写法相同
  ```
  // 1
  function A(name, age){
    var fn = Object.create(A.prototype);
    fn.name = name;
    fn.age = age;
    return fn
  }
  var B = A();
  console.log(B instanceof A);// true
  // 2
  function A(name, age){
    this.name = name;
    this.age = age;
  }
  var B = new A();
  console.log(B instanceof A);// true
  ```

*-end-*

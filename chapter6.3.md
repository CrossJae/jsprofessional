# 第六章 面向对象的程序设计

## 继承

1. 接口继承
    * 接口继承只继承签名，JS无签名，故无法使用这种继承
2. 实现继承
    1. 原型链继承
    ```
    function SuperType(){//构造函数
        this.property = true;
    }
    SuperType.prototype.getSuperValue = function(){//构造函数原型对象
        return this.property;
    };
    function SubType(){
        this.subproperty = false;
    }
    SubType.prototype = new SuperType();
    SubType.prototype.getSubValue = function(){
        return this.subproperty;
    };

    var instance = new SubType();

    console.log(instance.getSuperValue())//true
    ```
    问题：1.包含引用类型值的原型属性会被所有实例共享；2.没有办法在不影响所有对象实例的情况下，给SuperType的构造函数传递参数。故很少单独使用原型链。
    
    2. 借用构造函数继承（伪造对象、经典继承）
    ```
    function SuperType(){//构造函数
        this.colors = ["red","blue","green"];
    }

    function SubType(){
        SuperType.call(this);//继承了SuperType
    }

    var instance1 = new SubType();
    instance1.colors.push("black");
    console.log(instance1.colors);

    var instance2 = new SubType();
    console.log(instance2.colors)
    ```
    问题：方法都在构造函数中定义，那么函数不可能复用。故很少单独使用构造函数。
    
    3. 组合继承（伪经典继承）：最常用的方法
    ```
    function SuperType(name){//构造函数
        this.name=name;
        this.colors = ["red","blue","green"];
    }
    SuperType.prototype.sayName=function(){
        console.log(this.name)
    }

    function SubType(name,age){
        SuperType.call(this,name);//继承了SuperType
        this.age=age;
    }
    SubType.prototype=new SuperType();

    SubType.prototype.sayAge=function(){
        console.log(this.age)
    }

    var instance1 = new SubType("Nicholas",29);
    instance1.colors.push("black");
    console.log(instance1.colors);//"red,blue,green,black"
    instance1.sayName();//"Nicholas"
    instance1.sayAge();//29

    var instance2 = new SubType("Greg",27);
    console.log(instance2.colors);//"red,blue,green"
    instance2.sayName();//"Greg"
    instance2.sayAge();//27
    ```
    4. 原型式继承
    ```
    ```
    5. 寄生式继承
    ```
    ```
    6. 寄生组合式继承
    ```
    ```
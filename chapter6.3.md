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
    SubType.prototype = new SuperType();// 原型对象等于另一个对象的实例（new SuperType()）
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
        SuperType.call(this,name);//继承了SuperType,第二次调用SuperType()
        this.age=age;
    }
    SubType.prototype=new SuperType();// 第一次调用SuperType()

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
    问题：无论什么情况下，都会调用两次SuperType构造函数：一次是创建SubType函数时，一次是SubType函数内部
    4. 原型式继承
    ```
    //原理，创建临时构造函数，将其原型指向参数o，返回新的实例
    //可以用Object.create()代替这段函数
    function object(o){
        function F(){};
        F.prototype=o;
        return new F();
    }
    ```
    ```
    var person = {
        name:"Greg",
        friends:["MissA","MissB","MissC"]
    }
    var anotherperson=Object.create(person);
    console.log(anotherperson.friends);//"MissA","MissB","MissC"
    anotherperson.friends.push("MissD");
    console.log(anotherperson.friends);//"MissA","MissB","MissC","MissD"
    console.log(person.friends);//"MissA","MissB","MissC","MissD" person的引用型数据也被改变了
    ```
    好处：不需要创建构造函数，只是想两个对象之间保持类似的情况下，可以使用原型式继承。
    问题：跟原型模式相同，引用类型的值（friends=[]）会被共享

    5. 寄生式继承
    ```
    function object(o){
        function F(){}
        F.prototype = o;
        return new F();
    }

    function createAnother(original){
        var clone = object(original);//调用函数创建一个新对象
        clone.sayHi = function(){//增强对象
            console.log("hi");
        };
        return clone;//返回对象
    }

    var person={
        name:"Nicholas",
        friends:["Shelby","Court","Van"]
    };

    var anotherPerson=createAnother(person);//新对象具有person的属性和方法，还有自己的sayHi()方法
    anotherPerson.sayHi();
    ```
    问题：函数（sayHi）无法复用，像构造函数
    6. 寄生组合式继承（最理想的继承）
    ```
    function object(o){
        function F(){}
        F.prototype = o;
        return new F();
    }

    function inheritPrototype(subType, superType){
        var prototype = object(superType.prototype);   //create object
        prototype.constructor = subType;               //augment object
        subType.prototype = prototype;                 //assign object
    }

    function SuperType(name){
        this.name = name;
        this.colors = ["red", "blue", "green"];
    }

    SuperType.prototype.sayName = function(){
        console.log(this.name);
    };

    function SubType(name, age){  
        SuperType.call(this, name);

        this.age = age;
    }

    inheritPrototype(SubType, SuperType);

    SubType.prototype.sayAge = function(){
        console.log(this.age);
    };

    var instance1 = new SubType("Nicholas", 29);
    instance1.colors.push("black");
    console.log(instance1.colors);  //"red,blue,green,black"
    instance1.sayName();      //"Nicholas";
    instance1.sayAge();       //29

    var instance2 = new SubType("Greg", 27);
    console.log(instance2.colors);  //"red,blue,green"
    instance2.sayName();      //"Greg";
    instance2.sayAge();       //27
    ```

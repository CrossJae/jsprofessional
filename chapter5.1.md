# 第五章 引用类型

## Object类型

1. 创建object实例的方式
    1. new操作符后面跟object构造函数
        ```new操作符后面跟object构造函数
        var person = new Object();
        person.name = "CROSS";
        person.age = 29;
        
        ```
    2. 对象字面量表示法
        ```对象字面量表示法
        var person = {
            name : "Cross",
            age : 29
        };            
        ```
        ```
        var person = {}; //同 new Object()
        person.name = "CROSS";
        person.age = 29;
        ```
        * 对象字面量的优点：给人封装数据的感觉；向函数提供大量的可选参数时的首选
        
2. 访问属性方法
    ```
    // 点访问（推荐）
    alert(person.name);
    // 通过变量访问
    alert(person["name"]); 
    ```



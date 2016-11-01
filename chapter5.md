# 第五章 引用类型

*重点是*
## 关键词：
* 引用类型：
    1. 基本类型，如第四章，null undefined boolean string number
    2. 跟类相似，但不是类
* 构造函数：
    1. 啊
    2. 啊
* 表达式上下文、语句上下文 P84
* Object类型：
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
* Array类型：
    1. 创建Array实例的方法
        1. new
        ```
        var colors = new Array();
        var colors = new Array("red","yellow","blue");
        ```
        2. 数组字面量表示法
        ```
        var colors = [];
        var colors = ["red","yellow","blue"];
        ```
    2. 访问数组的值
        ```
        alert(colors[2]);
        ```
    3. length
        可读取；可写入
        ```
        colors.length = 1;
        ```
    4. 
* Date类型
* RegExp类型
* Function类型
* 基本包装类型
* 引申阅读：
    1. a
    2. a



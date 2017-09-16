# 第五章 引用类型

## Function类型

1. 定义函数的方法
    1. 函数声明
    ```
    function sum(num1,num2){
        return num1+num2
    }
    ```
    2. 函数表达式
    ```
    var sum = function(num1,num2){
        return num1+num2
    };
    ```
    
2. 函数声明与函数表达式的区别
    * 解析器先读取函数声明
    
3. 函数内部属性
    1. arguments
        * arguments保存函数参数
        * arguments.callee，指向arguments对象的函数
        ```
        function factorial(num){
            if(num<1){
                return 1;
            }else{
                return num*arguments.callee(num-1); //等同于factorial(num-1)
            }
        }  
        ```
        
    2. this
        * 引用的是函数执行的环境对象（全局作用域中，this引用的是window）
        
4. 函数的属性
    1. length：函数希望接收的命名参数的个数
    2. prototype
    
5. 函数的方法
    1. apply()
    2. call()
    * apply()与call()都是在特定的作用域中调用函数，实际上等于设置函数体内的this值
    * 两者最大的作用是扩大函数的作用域
    ```
    window.color="red";
    var o={
        color:"blue"
    };
    
    function sayColor(){
        alert(this.color);
    }
    
    sayColor();  //red
    
    sayColor.call(this);    //red
    sayColor.call(window);  //red
    sayColor.call(o);       //blue
    ```
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
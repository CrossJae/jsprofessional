# 第七章 函数表达式

## 递归

1. arguments.callee
    ```
    function factorial(num){
        if(num<=1){
            return 1;
        }else{
            return num * arguments.callee(num-1)
        }
    }
    ```
    * 问题：在严格模式下不能访问arguments.callee
2. 命名函数表达式
    ```
    var factorial = (function f(num){
        if(num<=1){
            return 1;
        }else{
            return num * f(num-1);
        }
    })
    ```
    * 总结：严格模式，非严格模式都可用
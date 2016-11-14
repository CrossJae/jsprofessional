# 第七章 函数表达式

## 闭包

1. 概念
    * 有权访问另一个函数作用域中的变量的函数
    
2. 包含函数：外部函数
3. 注意：闭包会携带包含它的函数的作用域，因此会比其他函数占用更多的内存。
4. 闭包与变量
    * 闭包只能取得包含函数中任何变量的最后一个值
    ```
    function createFunctions(){
        var result = new Array();
        for (var i=0; i < 10; i++){
            result[i] = function(){
                return i
            }
        }
        return result;
    }
    var funcs = createFunctions();
    for (var i=0; i < funcs.length; i++){
        document.write(funcs[i]() + "<br />");
    }
    ```
    结果都显示10
    ```
    function createFunctions(){
        var result = new Array();
        for (var i=0; i < 10; i++){
            result[i] = function(num){
                return function(){
                    return num
                }
            }(i);
        }
        return result;
    }
    var funcs = createFunctions();
    for (var i=0; i < funcs.length; i++){
        document.write(funcs[i]() + "<br />");
    }
    ```
    结果显示0 1 2 3 ... 10
    * 不知道为何要像以上一样写例子，也许只是为了说明闭包的特性，实践的话，如下的代码不是更省事？
    ```
    function createFunctions(){
        var result = new Array();
        for (var i=0; i < 10; i++){
            result[i] =  i
        }
        return result;
    }
    var funcs = createFunctions();
    for (var i=0; i < funcs.length; i++){
        document.write(funcs[i] + "<br />");
    }
    ```
    结果显示0 1 2 3 ... 10
5. this对象
6. 模仿块级作用域
7. 私有变量
    * 静态私有变量
    * 模块模式
    * 增强的模块模式
# 第七章 函数表达式

## 闭包

1. 闭包的概念
    * 有权访问 *另一个函数作用域中的变量* 的函数
2. 作用域链：指向变量对象的指针列表，只引用，不实际包含变量对象。
    * 在函数中访问一个变量时，就会从作用域链中搜索具有相应名字的变量。
2. 包含函数：外部函数
3. 注意：
    * 一般来说，当函数执行完毕，局部活动对象就会被销毁，内存中只保存全局作用域。
    * 闭包会携带包含它的函数的作用域，因此会比其他函数占用更多的内存。
4. 作用域链的副作用：闭包只能取得包含函数（外部函数）中任何变量的最后一个值
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

## 模仿块级作用域

## 私有变量
* 静态私有变量
* 模块模式
* 增强的模块模式

*-end-*

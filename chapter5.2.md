# 第五章 引用类型

## Array类型

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
3. length 可读取；可写入
    ```
    colors.length = 1;
    ```
4. 转换方法
    ```
    var colors = ["red","blue","green"];
    console.log(colors)
    console.log(colors.toString())
    console.log(colors.valueOf())
    console.log(colors.toLocaleString())
    console.log(colors.join("||"))
    ```
    
    ![转换方法](images/array.png)
    
5. 栈方法
    * 为数组提供类似栈的数据结构 
    * push() pop()，后进先出LIFO，后端添加 后端移除
    ```
    var colors = ["red","blue","green"];
    var item = colors.push("yellow");
    console.log(item);
    console.log(colors);
    item = colors.pop();
    console.log(item);
    ```
    ![栈方法](images/array1.png)

6. 队列方法
    1. push() shift()，先进先出FIFO，后端添加 前端移除
    ```
    var colors = ["red","blue","green"];
    var item = colors.shift();
    console.log(item);
    ```
    ![队列方法](images/array2.png)
    
    2. unshift() pop()，前端添加 后端移除
    ```
    var colors = [];
    var item = colors.unshift("red","blue","green");
    console.log(item);  //IE7及更早IE版本会返回undefined
    item = colors.pop();
    console.log(item);
    ```
    ![队列方法](images/array3.png)

7. 重排序方法
    1. 翻转数组 colors.reverse()
    2. 升序排列数组 colors.sort() ：调用toString()后比较字符串的升序排列

8. 操作方法
    1. concat()
    2. slice()
    3. splice()

9. 位置方法
    1. indexOf()
    2. lastIndexOf()

10. 迭代方法
    1. every()
    2. filter()
    3. forEach()
    4. map()
    5. some()

11. 归并方法
    1. reduce()
    2. reduceRight()


* 引申阅读：
    1. toString()与toLocaleString()区别
    2. sort()




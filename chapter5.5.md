# 第五章 引用类型

## Function类型

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
4. 转换方法
    ```
    var colors=["red","blue","green"];
    console.log(colors)
    console.log(colors.toString())
    console.log(colors.valueOf())
    console.log(colors.toLocaleString())
    console.log(colors.join("||"))
    ```
    
    ![转换方法](images/array.png)
    
5. 栈方法
    

* 引申阅读：
    1. toString()与toLocaleString()区别
    2. a



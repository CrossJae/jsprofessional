# 第五章 引用类型

## RegExp类型

1. 定义方法
    1. 字面量形式
    ```
    var pattern = /[bc]at/i; //匹配第一个bat或者cat，不区分大小写
    ```
    
    2. RegExp构造函数
    ```
    var pattern = new RegExp("[bc]at","i");
    ```

2. 标志

标志 | 说明 
--- |-------------
g   | 全局global 
i   | 不区分大小写 
m   | 多行，可查找多行 




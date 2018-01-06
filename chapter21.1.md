# 第二十一章 Ajax与Comet

## XMLHttpRequest对象

1. Ajax核心技术是XMLHttpRequest对象（简称XHR），无须刷新页面即可从服务器取得数据，但不一定是xml数据。
2. 各浏览器版本兼容的创建XHR对象的方法
```
function createXHR(){
  if(typeof XMLHttpRequest != 'undefined'){
    return new XMLHttpRequest();
  }else if (typeof ActiveXObject != 'undefined'){
    // 兼容<ie7的版本
  }
}
```
2. XHR的用法
    1. open()，三个参数：请求类型（get / post）、请求url、是否异步（false是同步，true是异步）发送请求。opne()并不会真的发送一个请求，而是启动一个请求以备发送。
    ```
    xhr.open("get","example.php",false)
    ```
    2. 只能向同域、相同端口、相同协议的url发送请求，否则会报错
3. HTTP头部信息
4. GET请求
5. POST请求

*-end-*

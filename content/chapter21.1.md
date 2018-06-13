# 第二十一章 Ajax与Comet

## XMLHttpRequest对象

1. Ajax核心技术是XMLHttpRequest对象（简称XHR），和服务器进行异步通信，无须刷新页面即可从服务器取得数据，但不一定是xml数据。
2. **各浏览器版本兼容的创建XHR对象的方法**
  ```
  function createXHR(){
    if(typeof XMLHttpRequest != 'undefined'){ // ie7以上版本
      return new XMLHttpRequest();
    }else if (typeof ActiveXObject != 'undefined'){ // 兼容<ie7的版本
      if(typeof arguments.callee.activeXString != 'string'){
        var versions = ["MSXML2.XMLHttp.6.0", "MSXML2.XMLHttp.3.0", "MSXML2.XMLHttp"],
            i, len;
        for(i=0, len=versions.length; i<len; i++){
          try{
            new ActiveXObject(version[i]);
            arguments.callee.activeXString = version[i];
            break;
          }catch(ex){
            // 跳过
          }
        }
      }
      return new ActiveXObject(arguments.callee.activeXString);
    }else{
      throw new Error('No XHR object available.');
    }
  }
  ```
2. XHR的用法
    1. open()，`open(method, url, async)`
      * method:（get / post）、请求url、是否异步（false是同步，true是异步）。
      * opne()并不会真的发送一个请求，而是 **启动** 一个请求以备发送。
        ```
        xhr.open("get", "example.php", false); //同步请求，浏览器会等待请求结束进行后续操作
        ```
      * 只能向同域、相同端口、相同协议的url发送请求，否则会报错，也就是说必须同域！
    2. send()，`send(null)` 发送特定请求，参数必须
      * send接收的参数是作为 **请求主体** 发送的数据
      * 调用send之后，请求就会被分派到服务器
    3. 响应相关属性
      * responseText
      * status
      * statusText
      * readyState
    4. abort(), 取消异步请求
3. HTTP头部信息: 每个http请求和响应都会带有头部信息
  * setRequestHeader('key': value)，在调用open之后，send之前，调用该方法
    ```
    var xhr = createXHR(); // 见上
    xhr.onreadystatechange = function(){
      if(xhr.readyState == 4){
        if((xhr.status >= 200 && xhr.status < 300) || xhr.status == 304){
          alert(xhr.responseText);
        }else{
          alert('unsuccessful' + xhr.status);
        }
      }
    };
    xhr.open("get", "example.php", true);
    xhr.setRequestHeader('MyHeader', "MyValue");
    xhr.send(null); //无数据时必须填写null
    ```
  * getResponseHeader('key') 获取响应字段的头部信息
  * getAllResponseHeaders(); 获取全部头部信息，返回是多行文本
4. GET请求
  * 向服务器查询信息
  * 可以将参数放在url后，key和value都必须`encodeURICompponent()`
5. POST请求
  * 向服务器发送应该被保存的信息
  * 比get请求消耗更多资源，更慢
  * 服务器对post请求和表单请求不会一视同仁，所以xhr可以模仿表单请求`Content-Type: application/x-www-form-urlencoded`

*-end-*

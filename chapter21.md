# 第二十一章 Ajax与Comet

## 关键词
* Ajax: Asynchronous JavsScript + XML
* Ajax原理：通过XMR（XMLHttpRequest）对象从服务器取得数据，然后通过js操作DOM插入数据更新页面
* 虽然XMR名字中包含XML，但AJAX通信与数据格式无关。
* 实现局部刷新的方法：
  * iframe，通过修改iframe的src，来实现iframe内的页面重载刷新，实质也是页面重载，会有性能问题
  * ajax，js发送异步请求，服务器查询数据库返回数据，js操作dom
* XMR对象方法：
  * `abort()` 停止当前请求
  * `getAllResponseHeaders()` 把HTTP请求的所有响应首部作为键/值对返回
  * `getResponseHeader("header")` 返回指定首部的串值
  * `open("method","URL",[asyncFlag],["userName"],["password"])` 建立对服务器的调用。method参数可以是GET、POST或PUT。url参数可以是相对URL或绝对URL。这个方法还包括3个可选的参数，是否异步，用户名，密码。ayncFlag=ture，异步；ayncFlag=false，同步。
  * `send(content)` 向服务器发送请求
  * `setRequestHeader("header", "value")` 把指定首部设置为所提供的值。在设置任何首部之前必须先调用open()。设置header并和请求一起发送 ('post'方法一定要 )
* XMR对象属性：
  * onreadystatechange    状态改变时触发
  * readyState            请求的状态, 0未初始化，1正在加载，2已加载，3交互中，4完成
  * responseText
  * responseXML
  * responseBody
  * responseStream
  * status                服务器HTTP状态码
  * statusText
* XMR示例：验证input标签是不是为空的一个Ajax的示例
```
function validate(field) {  
  if (trim(field.value).length != 0) {  
    var xmlHttp = null;  
    //表示当前浏览器不是ie,如ns,firefox  
    if(window.XMLHttpRequest) {  
        xmlHttp = new XMLHttpRequest();  
    } else if (window.ActiveXObject) {  
        xmlHttp = new ActiveXObject("Microsoft.XMLHTTP");  
    }  
    var url = "user_validate.jsp?userId=" + trim(field.value) + "&time=" + new Date().getTime();  

    //设置请求方式为GET，设置请求的URL，设置为异步提交  
    xmlHttp.open("GET", url, true);  

    //将方法地址复制给onreadystatechange属性  
    //类似于电话号码  
    xmlHttp.onreadystatechange=function() {  
    //Ajax引擎状态为成功  
    if (xmlHttp.readyState == 4) {  
      //HTTP协议状态为成功  
      if (xmlHttp.status == 200) {  
        if (trim(xmlHttp.responseText) != "") {  
          //alert(xmlHttp.responseText);  
          document.getElementById("spanUserId").innerHTML = "<font color='red'>" + xmlHttp.responseText + "</font>"  
        }else {  
          document.getElementById("spanUserId").innerHTML = "";  
        }  
      }else {  
        alert("请求失败，错误码=" + xmlHttp.status);  
      }
    };  

    //将设置信息发送到Ajax引擎  
    xmlHttp.send(null);  
  } else {  
    document.getElementById("spanUserId").innerHTML = "";  
  }     
}
```
*-end-*

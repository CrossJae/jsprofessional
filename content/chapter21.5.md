# 第二十一章 Ajax与Comet

## 其他跨域方法

21.4 介绍的跨域方法，服务端改变`Access-Control-Allow-Origin: *`来实现客户端可进行跨域请求，该值可以设定为具体的域名，比如`Access-Control-Allow-Origin: http://www.nczonline.net`

其他跨域方法：
1. 图片PING - 单向，只支持get请求
2. JSONP - 双向，但容易被篡改，有安全问题
3. comet - 服务器推送
    1. SSE - html5 server-sent event， 兼容性不好
    2. Web Sockets - 经典案例“实时聊天室”
        1. 单独的持久连接上提供全双工、双向通信，少量数据。可以构建一个端到端之间需要传输大量消息的大型多人在线游戏。
        2. 先发送http协议进行连接 —— 再从http协议变成web sockets协议
        3. url是`ws://`和`wss://`
        ```
        // 实例化
        var socket = new WebSocket('ws://www.example.com/server.php');
        // 发送简单数据
        socket.send('hello world');
        // 发送json数据
        var message = {
            time: new Date(),
            text: 'hello world',
            clientId: 'asdfg'
        };
        socket.send(JSON.stringify(message));
        // 接收数据
        socket.onmessage = function(event){
            var data = event.data;
            // 处理数据
        }
        ```
4. 补充
    * 为了解决长轮询的兼容性（ie8），要使用iframe进行异步发送请求
        * ajax的长轮询：在readyState = 4的时，再次执行原函数
        * iframe：创建iframe，然后reload（或者添加再删除iframe）
    ```
    var iframeCon = docuemnt.querySelector('#container'),
        text; //传递的信息
    var iframe = document.createElement('iframe'),
        iframe.id = "frame",
        iframe.style = "display:none;",
        iframe.name="polling",
        iframe.src="target.html";
    iframeCon.appendChild(iframe);
    iframe.onload= function(){
        var iloc = iframe.contentWindow.location,
            idoc  = iframe.contentDocument;
        setTimeout(function(){
            text = idoc.getElementsByTagName('body')[0].textContent;
            console.log(text);
            iloc.reload(); //刷新页面,再次获取信息，并且会触发onload函数
        },2000);
    }
    ```
*-end-*

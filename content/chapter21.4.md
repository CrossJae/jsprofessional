# 第二十一章 Ajax与Comet

## 跨源资源共享

CORS(Cross-Origin Resource Sharing跨源资源共享)

* `Preflighted Request` 一种透明服务器验证机制，使用`OPTIONS`方法，目的是判断实际发送的请求是否是安全的。
    * 支持自定义头部
    * get或post以外的方法
    * 不同类型的主体内容
    ```
    // Request Header
    OPTIONS / HTTP/1.1
    Host:
    Connection: keep-alive
    Access-Control-Request-Method: GET
    Origin: http://xxxxx.com:8000
    User-Agent: xxx
    Access-Control-Request-Headers: token
    Accept: */*
    Accept-Encoding: gzip, deflate
    Accept-Language: zh-CN,zh;xxx
    ```

*-end-*

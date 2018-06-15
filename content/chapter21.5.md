# 第二十一章 Ajax与Comet

## 其他跨域方法

21.4 介绍的跨域方法，服务端改变`Access-Control-Allow-Origin: *`来实现客户端可进行跨域请求，该值可以设定为具体的域名，比如`Access-Control-Allow-Origin: http://www.nczonline.net`

其他跨域方法：
1. 图片PING - 单向，只支持get请求
2. JSONP - 双向，但容易被篡改，有安全问题
3. comet

*-end-*

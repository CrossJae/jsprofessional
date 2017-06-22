# 第二十三章 离线应用与客户端存储 

## 离线检测
1. navigator.onLine
2. EventUtil.addHandler(window,"online",function(){...})
3. EventUtil.addHandler(window,"offline",function(){...})

## 应用缓存
1. <html manifest="/offline.manifest"> 描述文件列出要下载和缓存的资源

## 数据存储
1. Cookie
	* 名称与值都必须是URL编码
	* 每个浏览器对cookie都有数量上的限制，一般是20-50个
	* 名称不区分大小写，myCookie和MyCookie相同
	* cookie构成：名称／值／域／路径／失效时间（GMT格式日期）／安全标志(secure)
		```
		HTTP/1.1 200 OK
		Content-type:text/html
		Set-Cookie: name=value; expires=Mon, 22-Jan-07 07:10:24 GMT; domain=.wrox.com; path=/; secure
		Other-header:other-header-value
		```
4. IndexedDB
	








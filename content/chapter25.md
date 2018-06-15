# 第二十五章 新兴API

## requestAnimationFrame()
1.

## Page Visibility API
1.

## Geolocation API
1.

## File API

## Web计时
	* web计时机制的核心是`window.performance`对象
	* redirectCount 页面加载前的重定向次数
	* type
		* `performance.navigation.TYPE_NAVIGATE(0)` 页面第一次加载

## Web Workers - 不占用js自身线程
	* 实例：有人用web worker写了一个 [扫雷程序](https://github.com/michaelbutler/minesweeper)
	* 使用workder
		* `var worker = new Worker("xxx.js")` 浏览器会下载xxx.js
		* `worker.postMessage('start!')` 给Worker传递消息
		* `worker.onmessage = function(event){ var data = event.data; }`
		* `worker.onerror = function(event){ console.log( event.filename + event.lineno + event.message) }`
		* `worker.terminate()` 立即停止worker工作
	* worker全局作用域
		* 执行的js完全在另一个作用域，于当前网页不共享作用域，web worker不能访问dom，也无法通过任何方式影响页面的外观
		* worker全局对象是worker本身
	* 包含其他脚本
		* `importScripts("file1.js","file2.js")` 每个加载过程都是异步的，

*-end-*

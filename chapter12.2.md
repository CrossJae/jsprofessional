# DOM2和DOM3

### 元素大小
* 偏移量 offset dimension
```
offsetHeight // 元素内容高度 + 水平滚动条高度 + 边框高度 + 内边距
offsetWidth
offsetLeft
offsetTop
```
* 客户区大小 client dimension
```
clientWidth // 元素内容高度 + 内边距
clientHeight
```
* 滚动大小 scroll dimension
```
scrollHeight // 元素内容的总高度
scrollWidth
scrollLeft
scrollTop
```
  * 对于不包含滚动条的元素来说，scrollWidth和scrollHeight跟clientWidth/clientHeight之间的关系并不十分清晰，各浏览器之间是有差异的，所以确定 *文档总高度（不是窗口）* ，就取最大值
  ```
  var docHeight = Math.max(document.documentElement.scrollHeight, document.documentElement.clientHeight); // document.documentElement 指向html
  var docWidth = Math.max(document.documentElement.scrollWidth, document.documentElement.clientWidth);
  ```
* 三种区别
  * `document.body.offsetHeight` 获取的是窗口高度
  * `document.body.clientHeight` 获取的是窗口高度
  * `document.body.scrollHeight` 获取的是文档高度
* 确定元素大小`getBoundingClientRect()`

# DOM 扩展

### 选择符API
1. querySelector
```
document.querySelector('xxx');
element.querySelector('xxx');
```
2. querySelectorAll
3. matchesSelector（支持度不好）

### 元素遍历
* 新方法的出现，不必担心空白文本节点
```
childElementCount //子元素个数
firstElementChild //第一个元素
lastElementChild //最后一个元素
previousElementSibling //前一个兄弟元素
nextElementSibling //后一个兄弟元素
```

### HTML5
* getElementsByClassName
```
//没有这个方法时
var newDiv = getByClassName('new');
function getByClassName(selector){
  var allElements = document.getElementsByTagName('*'),
      selectorArray = [];
  for(var i=0,len=allElements.length;i<len;i++){
    if(allElements[i].nodeType===1 && allElements[i].getAttribute('class')===selector){
      selectorArray.push(allElements[i]);
    }
  }
  return selectorArray;
}
console.log(newDiv);
```
* 焦点管理
```
/**
 * 加载完成时，document.activeElement中保存的是document.body
 * 加载期间，document.activeElement = null
 */
document.activeElement
document.hasFocus(); //判断是否文档是否获得焦点，是否正与页面交互，浏览器兼容良好
```

### HTMLDocument的变化
* document.readyState[浏览器兼容良好]
  * `loading` 正在加载文档
  * `complete` 已经加载完成
  ```
  if(document.readyState === 'complete'){
    // ...
  }
  ```
* document.compatMode 兼容模式[浏览器兼容良好]
  * `CSS1Compat` 标准Standards mode
  * `BackCompat` 混杂Quirks mode
* document.head[浏览器兼容不好]
  ```
  var head = document.head || document.getElmentsByTagName('head')[0];
  ```

### 字符集属性
* document.charset[浏览器兼容良好]
  * default，`alert(document.charset); //'utf-16'`
  * 可以指定新字符集 `document.charset = 'utf-8'`
* document.defaultCharset[浏览器兼容不好]根据操作系统和浏览器设置的默认字符

### 自定义数据属性[浏览器兼容不好]
* element.dataset.xxx
```
var div = document.getElementById('myDiv');
// 取到自定义属性是data-appId的值
var appId = div.dataset.appId;
// 设置值
div.dataset.appId = 2345;
```

### 插入标记
* innerHTML
* outerHTML
* insertAdjacentHTML
  * beforebegin 在当前元素之前插入一个紧邻的兄弟元素
  * afterbegin 在当前元素之下插入一个新的子元素或在第一个子元素之前再插入新的子元素
  * beforeend 在当前元素之下插入一个新的子元素或在最后一个子元素之后再插入新的子元素
  * afterend 在当前元素之后插入一个紧邻的兄弟元素
  ```
  element.insertAdjacentHTML('beforebegin','<p>hello<\/p>');
  ```
* 内存与性能
```
var itemsHtml = '';
for(var i=0,len=values.length;i<len;i++){
  itemsHtml += '<li>' + values[i] + '<\/li>'
}
ul.innerHTML = itemsHtml;
```

### scrollIntoView()滚动页面
* scrollIntoView(true); //调用元素的顶部与视口顶部尽量平齐
* scrollIntoView(false); //调用元素尽可能在视口中,底部平齐
```
document.forms[0].scrollIntoView(true);
```

### 专有扩展（未进入标准，但个别浏览器已支持的有用的属性或方法）
* 文档模式 document.documentMode
* children属性
  * 跟childNodes类似，但只返回元素节点
* contains()方法
  * !!!!
* 插入文本
  * innerText 属性
  * outerText 属性
  * ！！！！
* 滚动
  * `scrollIntoViewIfNeede(alignCenter)` 不在窗口内时滚动到窗口中，参数为true时垂直显示
  * `scrollByLines(lineCount)` 将元素的内容滚动指定行高
  * `scrollByPages(pageCount)` 将元素的内容滚动指定的页面高度

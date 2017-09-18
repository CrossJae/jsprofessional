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

### 自定义数据属性

### 插入标记

### scrollIntoView()方法

### 专有扩展

# DOM2和DOM3

### 样式
* HTML中定义样式的方式
  1. `<link />`
  2. `<style />`
  3. `style`内联样式
* 确定浏览器是否支持DOM2级定义的CSS能力
```
var supportsDOM2CSS = document.implementation.hasFeature('CSS','2.0');
var suppotrsDOM2CSS2 = document.implementation.hasFeature('CSS2','2.0')
```
* style对象是CSSStyleDeclaration的实例
```
element.style.width = '100px';
element.style.backgroundColor = 'green';
element.style.border = '1px solid black';
```
* style对象的属性方法
```
cssText // element.style.cssText or element.style.cssText('xxx')
length //
parentRule
getPropertyCSSValue(propertyName) // 返回两个属性cssText和cssValueType, cssValueType = 0(继承的值) 1(基本的值) 2(值列表) 3(自定义的值)
getPropertyPriority(propertyName) // 返回优先权标识符
getPropertyValue(propertyName)
item(index)
removeProperty(propertyName)
setProperty(propertyName,value,priority)
```
* 计算的样式
```
document.defaultView.getComputedStyle(element, null);
element.currentStyle;
```

### 元素大小
* 偏移量 offset dimension
```
offsetHeight
offsetWidth
offsetLeft
offsetTop
```
* 客户区大小 client dimension
```
clientWidth
clientHeight
```
* 滚动大小 scroll dimension
```
scrollHeight
scrollWidth
scrollLeft
scrollTop
```
* 确定元素大小

### 遍历
1. NodeIterator
  * `nextNode()`
  * `previousNode()`
2. TreeWalker
  * `parentNode()`
  * `firstChild()`
  * `lastChild()`
  * `nextSibling()`
  * `previousSibling()`

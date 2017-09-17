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

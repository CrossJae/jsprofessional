# DOM2和DOM3

### 遍历
1. NodeIterator 是一个简单的接口，只允许以一个节点的步幅前后移动
  * `nextNode()`
  * `previousNode()`
2. TreeWalker 提供NodeIterator的功能同时，还支持在DOM结构的各个方向上移动，包括父节点、同辈节点和子节点
  * `parentNode()`
  * `firstChild()`
  * `lastChild()`
  * `nextSibling()`
  * `previousSibling()`

### 范围
* 备注：不太了解range的使用场景有什么，是以前完全没有接触的知识点

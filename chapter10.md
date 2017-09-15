# DOM

## 节点层次
1. HTML中，根节点是文档节点，文档节点只有一个子节点，是文档元素<html>，其他元素都包含在文档元素中。
2. 有12种节点类型，都是继承自Node类型
```
Node.ELEMENT_NODE(1);
Node.ATTRIBUTE_NODE(2);
Node.TEXT_NODE(3);
Node.CDATA_SECTION_NODE(4);
Node.ENTITY_REFERENCE_NODE(5);
Node.ENTITY_NODE(6);
Node.PROCESSING_INSTRUCTION_NODE(7);
Node.COMMENT_NODE(8);
Node.DOCUMENT_NODE(9);
Node.DOCUMENT_TYPE_NODE(10);
Node.DOCUMENT_FRAGMENT_NODE(11);
Node.NOTATION_NODE(12);
```
3. 判断节点类型的方法`someNode.nodeType == 1;//是否是元素节点`，因为ie没有Node类型的构造函数，所以还是判断数字
4. 属性
	* nodeType
	* nodeName
	* nodeValue
	* childNodes，保存着NodeList对象，NodeList对象并不是数组，只是类数组
	* parentNode
	* previousSibling/nextSibling，第一个元素的previousSibline=null，最后一个元素的nextSibling=null
	* firstChild/lastChild，只有一个节点时firstChild=lastChild；没有子节点的时候，firstChild=lastChild=null
	* ownerDocument
5. 方法
	* hasChildNodes(); //是否有子节点，有时返回true

## 操作节点
1. 插入节点
	* `someNode.appendChild(newNode)`
	* `someNode.insertBefore(newNode,oldNode)//在oldNode前面插入newNode，如果oldNode=null,则相当于appendChild插入到最后`
2. 替换
	* `someNode.replaceChild(newNode,oldNode);//newNode替换oldNode`
3. 删除
	* `someNode.removeChild(oldNode)`
4. 复制
	* `someNode.cloneChild(true);//参数是boolean，true表示深复制，也复制所有子节点`
5. 处理文本节点
	* `normalize()`

## Document类型（nodeType=9）
1. 特征，document是HTMLDocument的一个实例
```
nodeType = 9
nodeName = "#document"
nodeValue = null
parentNode = null
ownerDocument = null
// 子节点可能是DocumentType(最多一个),Element(最多一个),ProgessingInstruction,或Comment
```
2. 访问子节点的方法
```
// 指向<html>
document.documentElement //相当于document.childNodes[0]或者document.firstChild,都指向<html>
document.childNodes[0]
```
```
// 指向<body>
document.body
```
```
// 指向<!DOCTYPE>
document.doctype //浏览器支持不一致，所以这个属性用处有限
```
3. 属性
```
document.title
// 以下属性都存在于请求的HTTP头部
document.URL
document.domain
document.referrer
```
4. 方法
```
document.getElementById()
document.getElementsByTagName(); //返回一个HTMLCollection，也是类数组，不是真的数组
document.getElementsByTagName('*'); //获取所有元素
document.getElementsByName(); //一般用于单选框
```
5. 特殊集合，都是HTMLCollection对象
```
document.linkes
document.images
document.forms
```

## Text类型

* 创建有文本节点的元素节点
```
var element = document.createElement('div');
element.className = 'new';

var textNode = document.createTextNode('Hello World!');

element.appendChild(textNode);
document.body.appendChild(element);
```
* 动态添加script脚本
```
//<script type="text/javascript" src="./script.js"><\/script>
var script = document.createElement('script');
script.type = 'text/javascript';
script.src = './script.js';

document.body.appendChild(script);
```
* 动态添加style标签
```
// <link rel="stylesheet" type="text/css" href="./style.css" />
var link = document.createElement('link');
link.rel = 'stylesheet';
link.type = 'text/css';
link.href = './style.css';
var head = document.getElementsByTagName('head')[0];
head.appendChild(link);
```

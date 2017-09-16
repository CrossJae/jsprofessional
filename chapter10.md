# DOM

### 最重要的三种动态集合
1. NodeList `element.childNodes`
2. NamedNodeMap `element.attributs`
3. HTMLCollection `document.getElementsByTagName('div')`

### 节点层次
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

### 操作节点
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

### Document类型 (nodeType=9)
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
document.documentElement //相当于document.childNodes[0]或者document.firstChild
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
document.anchors
document.applets
document.forms
document.images
document.linkes
```
6. 文档写入
```
document.write(); //会重写页面
document.writeIn(); //写入在末尾会加换行符
document.open();
document.close();
```

### Element类型 (nodeType=1)
1. 特征
```
nodeType = 1;
nodeName = 元素标签名;
nodeValue = null;
parentNode = Document/Element;
```
2. 属性
```
// 元素标签名
div.tagName.toLowerCase();
div.nodeName;
```
3. 方法
```
// 获取属性
/**
 * getAttribute获取属性时，有两类属性很特殊：
 * 1.style，div.getAttribute('style')返回的是样式文本。div.style返回的是对象。
 * 2.onclick等事件，div.getAttribute('onclick')返回的是js脚本文本。div.onclick返回的是js函数。
 */
div.getAttribute('data-id');
div.setAttribute('data-id');
div.removeAttribute('data-id');
```
4. attributes属性
	* attributes属性中包含**aNamedNodeMap**，与NodeList类似，是个动态集合
	* 由于attributes的方法不够方便，所以一般还是使用getAttribute等方法
	* 序列化长字符串的方法
	```
	function outputAttributes(element){
		var pairs = new Array();
				attrName,
				attrValue,
				i,
				len;
		for(i=0,len=element.attributes.length;i<len;i++){
			attrName = element.attributes[i].nodeName;
			attrValue = element.attributes[i].nodeValue;
			if(element.attributes[i].specified){ //兼容ie7及更早版本
				pairs.push(attrName + '=\"' + attrValue + '\"'); //1.使用数组将名值对保存起来
			}
		}
		return pairs.join(" "); //2.在用空格作为分隔符拼接起来，变成字符串
	}
	```
5. 创建元素
```
document.createElement('div');
```

### Text类型 (nodeType=3)
1. 特征
```
nodeType = 3;
nodeName = "#text";
nodeValue = 文本内容;
parentNode = Element;
```
2. 创建文本节点
```
element.createTextNode('hello world!');
```
3. 规范文本节点，将元素内的所有文本节点合并成一个文本节点
```
element.normalize();
```
4. 分割文本节点
```
var element = document.createElement('div');
element.className = 'message';
var textNode = document.createTextNode('hello world!');
element.appendChild(textNode);
document.body.appendChild(element);
// 分割
var newNode = element.firstChild.splitText(5);
alert(element.firstChild.nodeValue); //"hello"
alert(newNode.nodeValue); //" world!"
alert(element.childNodes.length); //2
```
5. 其他方法
```
appendData(text); //text添加到节点结尾
deleteData(offset, count); //从offset开始删除删除count个字符
insertData(offset, text); //在offset的位置插入text
replaceData(offset, count, text); //用text替换从offset开始的count个字符
splitText(offset); //从offset将文本分成两个文本节点
substringData(offset, count); //提取从offset位置开始到offset+count为止的字符
```

### Comment类型 (nodeType=8)
1. 特征
```
nodeType = 8;
nodeName = "#comment";
nodeValue = 注释内容
parentNode = Document / Element;
```

### CDATASection类型 (nodeType=4)
1. 特征，只出现xml中
```
nodeType = 4;
nodeName = "#cdata-section";
nodeValue = CDATA区域中的内容
parentNode = Document / Element;
```

### DocumentType类型 (nodeType=10)
1. 特征，浏览器支持一般
```
nodeType = 10;
nodeName = doctype的值;
nodeValue = null
parentNode = Document;
```

### DocumentFragment类型 (nodeType=11)
1. 特征，作为仓库使用
```
nodeType = 11;
nodeName = "#document-fragment";
nodeValue = null
parentNode = null;
```
2. 避免浏览器反复渲染
```
var fragment = document.createDocumentFragment(); //作为缓存仓库使用
var ul = document.getElementById('myList'); //已有的id为myList的div
var li = null;
for(var i=0;i<3;i++){
	li = document.createElement('li');
	li.appendChild(document.createTextNode('item' + i));
	fragment.appendChild(li); //现存进缓存仓库中
}
ul.appendChild(fragment);
```

### Attr类型
1. 特征
```
nodeType = 2;
nodeName = 特性名称;
nodeValue = 特性的值;
parentNode = null;
```
2. 属性
	* name
	* value
	* specified：boolean值，区分属性是代码指定(true)的还是默认(false)的


### 常用脚本
1. 创建有文本节点的元素节点
```
var element = document.createElement('div');
element.className = 'new';
var textNode = document.createTextNode('Hello World!');
element.appendChild(textNode);
document.body.appendChild(element);
```
2. 动态添加script脚本
```
var script = document.createElement('script');
script.type = 'text/javascript';
script.src = './script.js';
document.body.appendChild(script);
```
3. 动态添加script行内脚本
```
function loadScriptString(code){
	var script = document.createElement('script');
	script.type = 'text/javascript';
	try{
		script.appendChild(document.createTextNode(code));
	}catch(ex){
		script.text = code;
	}
	document.body.appendChild(script);
}
loadScriptString('function sayHi(){alert("hi");}'); //这个方法同eval()
```
4. 动态添加style标签
```
var link = document.createElement('link');
link.rel = 'stylesheet';
link.type = 'text/css';
link.href = './style.css';
var head = document.getElementsByTagName('head')[0];
head.appendChild(link);
```

### 操作表格

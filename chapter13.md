# 事件

### 事件流（在页面中事件接收顺序）
1. 事件冒泡 event bubbling
    * 通常理解的事件接收顺序就是冒泡，由最具体的元素先接收，一层层向上传播，到document或window
    * IE5.5以前冒泡到document为止，IE9和其他浏览器冒泡到window对象。
2. 事件捕获 event capturing
    * Netscape Communicator团队提出的事件流方式
    * 由不太具体的元素，document或window先接收，最后捕获到具体元素，被点击的div。
    * 很少使用
3. DOM事件流
    * DOM2级事件流：事件捕获阶段、处于目标阶段、事件冒泡阶段
    * 事件捕获阶段：从document或window到具体元素的上一级就停止了
    * 处于目标阶段：事件在具体元素上发生
    * 事件冒泡阶段：事件回传到文档
    * 具体的使用不太了解？

### 事件处理程序（事件侦听器）
1. HTML事件处理程序
    * `<div data="click-event" onclick="alert(this.data)"></div>`
    * 主要缺点：HTML与JS **重度耦合**
2. DOM0级事件处理程序
    * 常用
    ```
    var btn = document.getElementById('myBtn');
    btn.onclick = function(){
        alert(this.id); // myBtn. this引用的是当前元素
    }
    ```
    * 移除 `btn.onclick = null;`
3. DOM2级事件处理程序
    * 常用。优点：可以绑定多个事件
    * 通过 `addEventListener` 添加的事件处理程序，只能使用 `removeEventListener` 方法移除
    * 绑定的匿名函数不可以被移除
    ```
    var btn = document.getElementById('myBtn');
    var handler = function(){
        alert(this.id);
    }
    btn.addEventListener('click', handler, false);
    // 移除
    btn.removeEventListener('click', handler, false);
    ```
4. IE事件处理程序
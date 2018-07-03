# 第一章 JavaScript简介

* JavaScript最初始的作用是在client端完成验证表单的任务
* JavaScript的实现包含：核心ECMAScript、文档对象模型DOM、浏览器对象模型BOM
* ECMAScript只是JS的语言基础，浏览器Web是ES实现的宿主环境，其他宿主环境还有NODE / FLASH
* DOM1：DOM CORE + DOM HTML
* DOM2：DOM VIEW + DOM EVENTS (定义了事件)+ DOM STYLE（CSS） + DOM Traversal and Range（遍历和范围）
* DOM3: DOM Load and Save（加载保存） + DOM Validation（验证）

# 第二章 在HTML中使用JS
* defer：异步加载，加载后延迟执行，在DOMContentLoaded之前执行，并按照请求顺序执行，算是有序的（但浏览器环境中未必会真的有序且在DOMContentLoaded之前执行），defer也相当于把脚本放在页面最后执行，一般一个页面里，最好只有一个defer执行的js。
* async：异步加载，加载后立即执行，谁先加载好谁执行，所以是无序的。

*-end-*

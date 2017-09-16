# 第八章 BOM

## window对象
* 既是访问浏览器的一个接口，又是es规定的global对象
* 所有全局作用域中声明的变量，函数都是window对象的属性和方法。
```
var age = 29;
alert(window.age);
```
* 全局变量不能delete删除，在window上定义的属性可以。
```
var age = 29;
window.color = 'red';
delete window.age;
delete window.color;
alert(window.age);//29
alert(window.color);//undefined
```


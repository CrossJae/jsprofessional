# 第八章 BOM

### window对象
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

### location对象
* 既是window对象的方法，也是document对象的方法
* 属性：每次修改location的属性，除hash以外，页面都会以URL重新加载
```
href        //"#content"
host        //"www.wrox.com:80"
hostname    //"www.wrox.com"
href        //"http://www.wrox.com:80"
pathname    //"/WileyCDA"
port        //"8080"
protocol    //"http:"
search      //"?q=js"
```
* replace方法：修改location属性，都会生成新的历史记录，禁用这种行为时使用replace方法
```
location.replace('http://www.wrox.com'); //页面跳转，并无法回退
```
* reload方法
```
location.reload(); //有可能从缓存中重新加载
location.reload(true); //从服务器重新加载
```

### navigator对象
* 通常使用的是`navigator.userAgent`

*-end-*

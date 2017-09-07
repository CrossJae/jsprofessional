# DOM

## 节点操作
1. 插入节点
	* appendChild()
	* insertBefore()
	```
	appendChild(newnode);
	insertBefore(newnode,oldnode);//在oldnode前面插入newnode，如果oldnode=null,则相当于appendChild插入到最后
	```
2. 替换
	* `replaceChild(newnode,oldnode);//newnode替换oldnode`
3. 删除
	* removeChild

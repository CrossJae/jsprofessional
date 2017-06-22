# 错误处理与调试

## 错误处理
1. try-catch
```
try{
	// 可能发生错误的代码
}catch(error){ // 必须给包含错误信息的对象命名
	// 错误时的处理
	alert(error.message); // message属性是唯一所有浏览器支持的属性
}finally{
	// 可选
	// 无论是否错误，都会执行finally的语句
}
```
	* 错误类型：Error,EvalError,RangeError,ReferenceError(引用错误),SyntaxError,TypeError,URIError
2. throw 抛出错误
3. 常见的错误类型
	* 类型转换错误
	* 数据类型错误
	* 通信错误

## 调试技术
* console.log

## 常见的IE错误 

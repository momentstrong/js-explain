> 闭包定义

​	官方解释：闭包是一个拥有许多变量和绑定了这些变量的环境的表达式（通常是一个函数），因而这些变量也是该表达式的一部分。

​	通俗解析：一般就是将一函数内嵌套的函数的引用保存到了函数之外的变量

> 看下面这段代码：

```tiki wiki
function a(){
	function b(){
		console.log(i++);
	}	
 	var i = 0;
	return b;
}
var foo = a();
```

 foo变量引用的是b函数的代码块 ---> foo == function b () {console.log(i++)}
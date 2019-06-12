```js
console.log(a)  //functiona(){	 var a = 'a';}
// a = 'test';

function a(){
	console.log(b)
	a = 'a'; // 暗示全局变量
	function b (){

	}
}
a(); 
console.log(a)
```

输出:

```js
function a(){
	console.log(b)
	a = 'a'; 
	function b (){
	}
}
function b(){

} 
a
```

### 原因：

* js执行前会进行预编译
  * 全局预编译GO(Global Object)
    * 创建GO对象
    * 给全局变量赋值 `undefined`   GO{a: undefined}
    * 将全局的函数申明的函数名作为key,value为函数整体赋值到GO对象中  
      * GO{a:function a(){
        ​	console.log(b)
        ​	a = 'a'; // 暗示全局变量
        ​	function b (){}
        }}
  * 函数预编译AO (Activation Object)
    * 创建AO对象
    * 将函数内的形参和变量声明存储到AO对象中，值为undefined
    * 将实参和形参统一
    * 将函数内的函数申明的名称作为AO对象的key，函数的整体内容为value 存储到AO对象 
      * AO{b:function b(){}}

### 说明

* GO=window对象，GO即操作window，a为全局变量,console.log(a) = console.log(window.a)


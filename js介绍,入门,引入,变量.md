## js引入

* **内部引入**

  * 在html/web 页面上通过 *<script><script>* 引入

* **外部引用**

  * 在html/web 页面上通过 *<script src="location"><script>* 引入

  * 代码结构如下

    > folder文件夹
    >
    > > > Introduction.html
    > > >
    > > > introduction.js

  * 示例如下

  ```html
  <html>
  <head>
  	<title>js-introduction</title>
  	<!-- 内部引用 script的type属性可有可无  -->
  	<script type="text/javascript">
  		document.write('hello world')
  		document.write("<br>");
  	</script>
  	 <!-- 外部引用 -->
  	<script type="text/javascript" src="introduction.js">
  		document.write("inner content");
  
  		// 当外部引用和内部引用条件同时具备时，外部引用有效
  	</script>
  
  </head>
  <body>
  	<!-- script 可以也放在body区 -->
  	<script type="text/javascript">
  		document.write("<br>");
  		document.write('hello world')
  	</script>
  </body>
  </html>
  ```

  * **introduction.js 内容**

  ```js
  document.write("out content");
  ```

  * **运行结果**
    `hello world
    out content 
    hello world`
  * **建议和注意**
    建议使用外部引入，符合结构，行为，样式相分离的思想

  ---

  ## 变量

* **申明方式**

  - 使用var声明
  - 示例
    - var temp 申明任意类型的变量，默认值为`undefined`

* **赋值方式**

  * 先申明，后赋值
    * 示例
      * var temp; temp ="12" 

  * 申明时立即赋值
    * 示例
      * var temp = "12"

  * 同时申明写法

    * 示例

      * var temp1,temp2,
      * var temp1="1" ,temp2="2"
      * 可以同时申明不同类型的变量

    * 可读性较好的写法

      * ```js
        var v1 = "a",
        	v2= 3,
        	v3=true;
        ```

  * 说明
    * js变量的类型是根据值来定义的
    * var temp = "1"后 temp = true 语法正确

* 命名规则
  * 变量名以 `_`  `$`  和字母开头
  * 变量名可以包含字母，数字，`_`  `$` 
  * js关键字和保留字不可用作变量名

---

## 数据类型

* **原始值**（5种）

  * Number :数字类型 
  * String:字符串   
  * Boolean(2中情况) ：true  false
  * null 占位符
  * Undefined  js变量默认值  

* 引用值

  * Array 
  * Object
  * Function
  * data 
  * RegExp
  * ...

* 两者区别

  * 赋值情况不一样

    * 示例

  * ```js
    //原始值
    var a = 10;
    var b =a;
    a=20;
    b==20？ 还是 b==10？
    结果：b=10
    var arr = [1];
    var arr1= arr;
    arr.push(2)
    arr1的内容有变化吗？
    结果： arr=[1,2]
    ```

    * 原因分析
      * 原始值和引用值存的地方不一样，原始值在stack(栈)中，引用值在heap堆(大部分)中

## js语法

* 每个语句结束以`;`标识
* 运算符操作
  * `+` : 加   `-`: 减 `*`：乘  `/` :除   `%`:取模(求余数)
  * `++`     `--`   `*=`     `+=`   `-=`  `/+`    `%=`
  * 任意类型类型加字符串都等于字符串
  * var str = "1", 操作 ` str ++ `   `str--`   `--str` `++str`会隐式转化数据类型为Number, 所以讲数字形式的字符串，转化为Number类型的可以这样操作  `++str -1`  = 1
  * `0/0` :NaN   `1/0`: Infinity.  `-1/0` :-Infinity
* 优先级`=` 最弱，`()` 优先级最高
* 建议规范
  * 运算符左右留一个空格，方便阅读
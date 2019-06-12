### typeof(param):

  判断输入`param`的类型,结果值情况：返回字符串描述的数据类型

* `"number"` :数字类型
  * 100，100.1
* `"string"` :字符串类型
  * "12","abc"
* `"boolean"`:布尔类型
  * true  false
* `"object"`: 对象

### 类型转换

* **隐式转换**

  * 自动转换为number
    * 2 * "2"  = 4     "2" * "2" = 4 	"2" - "2" = 0 	"2" / 2 = 1   "2" % 2 = 0
    * `var a = "123"; a++`   a= 123
    * `var a =  +"abc"   typeof(a)= number`  
    * `var a = +"123"`  a= 123
    * `var a = - "123"` a= -123
  * 自动转换为string 
    * "abc" + 2 = "abc2"   2 + "2" = "22"   2  + ""  = "2"
  * 自动转换为Boolean
    * `!""= true`	  `!false= true`	`!null = true`   `!undefined = true`  `!"abc"=false`
  * `isNaN()`函数
    * isNaN("123")   = false  会先执行 Number("123")，将执行的结果与NaN作比较
  * `==`   `!=`
    * `2 == "2"` 结果为true
    *  `2 != "2"`  结果为false
    * `0 == false` 结果为true
    * `0 !=true` 结果为true  

* 显式转换

  * **`Number()`** 函数  : 转换为数字类型
    * Number("1") = 1
    * Number("a") = NaN
    * Number(null)=0
    * Number(false)=0
    * Number(undefined) =NaN
    * Number("1a") = NaN=NaN
    * Number(true) = 1
    * Number() =0
    * Number("") = 0
  * **`parseInt()`** 函数：转换为整型，将参数当作某一进制（默认：10）的数，转换为10进制的数，parseInt("123",10) = parseInt("123")
    * parseInt("123") =123
    * parseInt("a") =NaN
    * parseInt(null)=NaN
    * parseInt(undefined) =NaN
    * parseInt() = NaN
    * parseInt("") = NaN
    * parseInt("1.2") = 1
    * parseInt("1.9") = 1
    * parseInt("123abc") = 123
    * parseInt("a123") = NaN
  * **`parseFloat()`** 函数 ： 转换为符点型
    * parseFloat("1") = 1
    * parseFloat("1.1") = 1.1
    * parseFloat("1.1abc") = 1.1
    * 其他参数情况情况同`parseInt()`
  * **`toString()`**函数：转换为字符串
    * var d = 2; d.toString() = "2"
    * var d = {} , d.toString() = "[object Object]" 
    * var d = true ; d.toString()="true"
    * var d = null  ; d.toStirng() : 报错 `ncaught TypeError: Cannot read property 'toString' of null`
    * var d= undefined; d.toString() :报错`Uncaught TypeError: Cannot read property 'toString' of undefined `
    * toString(radix) : 以十进制为基底，转换为目标进制 : `var d = 10; d.toString(2) = "1010"`
  * **`String()`** 函数 ：转换为字符串
    * String(null) = "null"
    * String(undefined) = "undefined"
    * String(1) = "1"
    * String(false) = "false"
  * **`Boolean()`** 函数：转换为布尔
    * Boolean(1) = true
    * Boolean("a") = true
    * Boolean(0) = false
    * Boolean(null) = false
    * Boolean(undefined) = false
    * Boolean("") = false

  ### 不会发生类型转换的情况

  * 先判断类型，在比较值，类型不相等，直接返回false

  * `===`  :全等于 
    * `1 === "1"` 返回false	`0 ===false` 返回false
  * `!==` ：完全不等
    * `1!== "1"` 返回true		`0 !==false` 返回true

* ⚠**注意**

  * `NaN 于任何数据比较都返回false ,包括自己`
    * `NaN == NaN`  返回false
    * `NaN === NaN` 返回false
  * 变量a未提前定义， console.log(a) ==> 报错 ： `...is not defined...` , typeof(a) 不会报错，会返回 "undefined"
  * `typeof(typeof(undefined))`  返回 "string" 
### 比较运算符

* `>`      `<`     `>=`     `<=`  `==` `===`   `!=`   `!==` 
  * 比较结果为true

### 逻辑运算符

* `&&`  `||`    `!`
  * &&(与操作)： 寻找一个条件结果为false的值，遇到false返回本身值,如果条件为最后一个，返回条件本身(判断的结果)
    * `var temp = 1 && 2  ;temp =2; `      `var temp = null&& 1 ;temp=null`   `var temp =(1==1)&& (2==2); temp=true`
  * `||(或)`: 寻找一个结果为 true 的值，遇到条件结果为true的项, 返回该项本身(或者条件判断的结果)
    * `var temp=1||2; temp的值为1;` `var tempnull || 1;temp:1`  `var temp= 1==1 || 2==2 temp:true(1==1的结果为true)` 
  * `!(非): 结果取反 有`true` 和 `false` 两种结果
    * `var temp = !1; temp:false`  `var temp =!!1 ; temp:true`
* 条件判断
  * 


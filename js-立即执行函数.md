* ```html
  <html>
  <head>
  	<title>立即执行函数</title>
  
  </head>
  	<script type="text/javascript">
  	/*立即执行函数*/
  		// 针对初始化功能 只执行一次
  		// 无需函数名，但也可写上，但没有任何实际意义
  		// 写法1. w3c推荐写法
  		(function(){
  			console.log('hello world w3c 推荐写法');
  		}());
  		// 写法2
  		(function(){
  			console.log('hello word immediately function');
  		})();
  
  		// 可以存在函数名
  		(function test(){
  			console.log('hello LQ');
  		}());
  
  		// 函数可以有返回值
  		var str =(function (){
  			return 'immediately fun'
  		}());
  		console.log(str);
  
  		// 函数可以带参数
  		var num = (function (a,b,c,d){
  			return a + b + c + d;
  		}(1,2,3,4));
  		console.log(num);
  
  
  		// 常见面试题  该函数会有出现什么效果
  		// 不会输出 test...   (1,2,3,4)里面当作了表达式，而不是执行符合
  		function test(a,b,c,d){
  			console.log('test...')
  		}(1,2,3,4);
  
  		/* 报错 成为表达式才可以被执行
  		function test1(a,b,c,d){
  
  		}()
  		*/
  		// 函数表达式
  		var result = function bds(){
  				console.log('bds...');
  		}();
  
  
  		// 以下情况，也被视为立即执行函数
  		// 只要被识别为表达式，就能被执行符号执行
  		// - +  ! || 符号可以将函数转换为表达式 ， 因此可以被执行符号()执行
  		-function (){
  			console.log('a...')
  		}();
  		+ function bbb(){
  			console.log('b...')
  		}();
  		!function(){
  			console.log('c...')
  		}();
  		0|| function(){
  			console.log('d...')
  		}()
  
  
  		/* 
  			()  也是一种表达式
  			所以 写法2 
  			(function(){})()
  			可以被执行
  
  			将执行符号()放入表达式()里，函数后面，
  			即写法1 (function(){}())
  			可以被执行
  
  		*/ 
  
  
  	</script>
  <body>
  
  </body>
  </html>
  ```

  Js代码执行结果：
  ![immediately-function-console.png](https://upload-images.jianshu.io/upload_images/17953874-5af64496edddd271.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


  ###    立即执行函数：

  * **定义**

    申明一个函数，并马上调用这个(匿名)函数，就叫立即执行函数；就是声明后立即执行；   

  * **用途**

    * 针对初始化功能，只需执行一次，例如：初始化环境变量

    * 封装临时变量,避免污染全局变量

      * 以下案列

      ```html
      <body>
          <ul id="list">
              <li>公司简介</li>
              <li>联系我们</li>
              <li>营销网络</li>
          </ul>
          <script>
             var list = document.getElementById("list");
             var li = list.children;
            for(var i = 0 ;i<li.length;i++){
              li[i].onclick=function(){
                alert(i);  // 结果总是3.而不是0，1，2
              }
            }
           </script>  
      </body>
      ```

      以上代码运行，alert的结果总是3，不是 0 ，1，2，因为for循环后 ，i变成了3，i是全局GO的变量

      使用立即函数解决：

      ```html
      <body>
          <ul id="list">
              <li>公司简介</li>
              <li>联系我们</li>
              <li>营销网络</li>
          </ul>
          <script>
             var list = document.getElementById("list");
            var li = list.children;
            for(var i = 0 ;i<li.length;i++){
             ( function(j){
                  li[j].onclick = function(){
                    alert(j);
                })(i); //把实参i赋值给形参j
              }
            }
           </script>  
      </body>
      ```

  * **常见写法**

    * `(function(){`

        // 代码体

        `}())  `    

      w3c推荐写法

    * `(function(){`

       // 代码体

      `})()`

  * 分析

    1. 立即执行函数属于函数，也会经过预编译，函数申明提升，变量提升过程，生成AO对象，

       可以有返回值

    2. 可以存在函数名，但无实际意义

    3. 函数表达式 可以通过执行符号()执行，立即执行函数其实就是一个函数表达式，被()转译成表达式

       `(function(){})` 是一个表达式， 最后在加一个执行符号`()` 即可执行，执行符号也可放入表达式里面执行匿名函数 ，即 `(function(){}())`

  * 相关面试题分析

    function test(a,b,c,d){
    ​			console.log('test...')
    }(1,2,3,4);

    问:**是立即执行函数吗？运行结果是什么？**

    解答：

    **不是立即执行函数**，test是函数申明，不是函数表达式。

    (1,2,3,4)不是当作执行符号，js引擎为了尽可能不报错，会将(1,2,3,4)当作表达式处理；

    **运行不会有任合输出**，相当于申明了个test函数，也没有调用

    这段代码相当于被分割成两部分，如下：

    function test(a,b,c,d){
    ​			console.log('test...')
    }

    (1,2,3,4);

     

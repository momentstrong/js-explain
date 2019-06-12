```js
function bar(){
    function foo(){
        a = 100;
    }
    var a = 110;
    foo();
    console.log(a);//100
    
}
bar();
```

执行结果输出 `100`

当bar()函数执行的时候，bar()函数生成一个bar.[[scope]],即bar的作用域,由js引擎访问

bar.[[scope]]是一个执行期间前创建的上下文对象，存储的是执行上下文对象的集合，这个集合是由上下文对象链组成的。

当bar()被执行时，经过以下流程

1. 在bar.[[scope]]的第0位创建一个AO对象

   AO{

   ​	a:undefined

   ​	foo:function ... // 函数整体

   }

2. 在bar.[[scope]]的第1位创建一个GO对象

   GO{

    bar:function... // 函数整体

   }

3. 将bar.[[scope]]中的第0位中的AO对象的a属性赋值为110

   AO{

   ​	a:110

   ​	foo:function ... // 函数整体

   }

4. 执行foo()函数,创建foo()的作用域，foo.[[scope]] ,foo[[scope]]的作用域建立在bar函数的作用域之上

   ,第0位foo()函数的AO对象，第1位为bar()函数的AO对象，第2位为GO对象

5. 函数的作用域自顶向下查找，由里向外查找，所以当执行foo()函数时，能访问到bar()函数AO对象的a属性并进行赋值，并输出100

`foo[[scope]][0] `———>(foo)AO对象

`foo[[scope]][1] `———>(bar)AO对象

`foo[[scope]][2] `————> GO对象  



[其他相关js分享](<https://www.jianshu.com/u/53845e62e413>,点击打开)


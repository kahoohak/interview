## 数据类型<br>

1. JavaScript有哪些数据类型，它们的区别？<br>
undefined, null, string, number, boolean, object, symbol, bigint<br>
除了object，其他都是原始数据类型<br>
原始数据类型存放在栈中，引用类型存放在堆中，栈中存放指针<br>

2. 数据类型检测的方式有哪些<br>
typeof 只能检测原始数据类型<br>
instanceof 只能检测引用类型，机制是检查对象的原型链中是否有构造函数的原型<br>
constructor 可以通过constructor访问构造函数，但是构造函数被修改，就不能正确检测了<br>
Object.prototype.toString.call 为何不调用obj.toString 因为array，function类型重写了toString方法，不能判断类型<br>

3. 判断数组的方式有哪些<br>
Array.isArray<br>
obj instanceof Array<br>
obj.__proto__ == Array.prototype<br>
obj.constructor.toString().slice(8, 14) == Array<br>
Object.prototype.toString.call(obj).slice(8, -1) == Array<br>
Array.prototype.isProtypeof(obj) <br>

4. null和undefined区别<br>
undefined代表未定义，null代表空对象<br>
undefined并不是保留字，意味着可以作为变量名，安全获取undefined可以使用void 0<br>


5. typeof null 的结果是什么，为什么？<br>
Object<br>
这是一个历史遗留bug，因为null的类型标签和object一样都是000，所以判定为object<br>

6. intanceof 操作符的实现原理及实现<br>
判断构造函数的prototype是否出现在目标对象的原型链上<br>


7. 为什么0.1+0.2 ! == 0.3，如何让其相等<br>
因为这两个数的二进制都是无限循环的，又因为双精度浮点数小数只能保存到52位，相加后转为十进制就是0.30000...0004<br>
Math.abs((0.1 + 0.2) - 0.3) < Number.EPSILON<br>

8. 如何获取安全的 undefined 值？<br>
void 0<br>

9. typeof NaN 的结果是什么？<br>
Number<br>

10. isNaN 和 Number.isNaN 函数的区别？<br>
前者会进行类型转换，后者不会，更精确<br>

11. == 操作符的强制类型转换规则？<br>
x, y类型是否相同，相同直接比大小<br>
null == undefined true<br>
string == number 会把string转为number<br>
boolean == any 会把boolean转为number<br>
object == (string || number || symbol) 会把object转为原始类型<br>

12. 其他值到字符串的转换规则？<br>
undefined => 'undefined'<br>
null => 'null'<br>
true => 'true'<br>
false => 'false'<br>
number直接转，极大极小值以指数显示<br>
symbol直接转，只允许显示转换，隐式转换会报错<br>
object调用toString()方法，自身可以定义，没有就调Object.prototype.toString()<br>

13. 其他值到数字值的转换规则？<br>
undefined => NaN<br>
null => 0<br>
true => 1<br>
false => 0<br>
string直接转，包含非数字为NaN，空字符串为0<br>
object首先转换为原始类型，如果非数字，继续转<br>
object转原始类型，首先看valueof方法是否返回原始类型，如不是，接着调用toString方法，如还不是，则报错<br>

14. 其他值到布尔类型的值的转换规则？<br>
false: undefined, null, +0, -0, NaN, ''<br>
之外的都是true<br>

15. || 和 && 操作符的返回值？<br>
会对第一个操作数进行判断<br>
|| 前者为false，返回后者操作数的值，前者为true返回前者<br>
&& 前者为false，返回前者操作数的值，前者为true返回后者<br>
返回的都是操作数的值，而非布尔值<br>

16. Object.is() 与比较操作符 “===”、“==” 的区别？<br>
==会进行类型转换<br>
===类型不一致直接返回false<br>
Object.is是更符合逻辑的三等，+0和-0不再相等，NaN等于自身<br>

17. 什么是 JavaScript 中的包装类型？<br>
原始类型上是没有属性和方法的，但在使用时，会把它转换成对象，这就是包装类型<br>
可以显式调用，Object或者new对应的类型（String， Number，Boolean）<br>

18. JavaScript 中如何进行隐式类型转换？<br>
除了Date对象，其他所有ToPrimitive都是先valueOf，再toString，如果两步转换完还是没有返回原始类型，报错。 原始类型返回自身<br>
+号两边有一个字符串，则转字符串，其余情况都转为数字<br>
==尽量都转为数字<br>
<, >如果都是字符串，比较字母顺序，否则转为数字比较<br>

19. + 操作符什么时候用于字符串的拼接？<br>
如果其中一个是字符串，则拼接，否则按加法算<br>

20. 为什么会有BigInt的提案？<br>
因为原先超出了数值最大范围计算不精确<br>

21. object.assign和扩展运算法是深拷贝还是浅拷贝，两者区别<br>
浅拷贝<br>

## es6<br>

1. let、const、var的区别<br>
是否有块级作用域 let const<br>
是否存在变量提升 var<br>
是否添加全局属性 var<br>
能否重复声明变量 var<br>
是否存在暂时性死区 let const<br>
是否必须设置初始值 const<br>
能否改变指针指向 let var<br>

2. const对象的属性可以修改吗<br>
可以。const只是限制对象的指针不可变，对象内部属性变化是不可控的<br>

3. 如果new一个箭头函数的会怎么样<br>
箭头函数没有prototype，没有this，没有arguments，不能进行new操作<br>

4. 箭头函数与普通函数的区别<br>
箭头函数写法更简洁<br>
箭头函数没有自己的this，它的this是捕获其所在上下文的this<br>
箭头函数的this永远不会改变<br>
call, apply, bind等方法不可改变箭头函数的this指向<br>
箭头函数不可作为构造函数<br>
箭头函数没有arguments<br>
箭头函数没有prototype<br>
箭头函数不能用作generator函数，不能使用yield<br>

5. 箭头函数的this指向哪⾥？<br>
指向其所在上下文的this<br>

6. 扩展运算符的作用及使用场景<br>
用于对象的解构赋值和浅拷贝<br>
用于展开数组，数组的解构赋值，合并，复制<br>
如果将扩展运算符用于数组赋值，只能放在最后<br>
任何Iterator接口的对象，都可以用扩展运算符转为数组<br>

7. Proxy 可以实现什么功能？<br>
vue3中的数据响应式<br>

8. 对对象与数组的解构的理解<br>
数组解构时，严格按照顺序提取元素<br>
对象解构，按key来提取<br>

9. 如何提取高度嵌套的对象里的指定属性？<br>
在第一层解构出来的变量名右侧加冒号和目标属性名，进一步解构，逐层获取<br>

10. 对 rest 参数的理解<br>
...rest可以获取剩余参数，也可以在参数数量不确定时获取所有参数集合，他会把参数序列整合成数组<br>

11. ES6中模板语法与字符串处理<br>
模板字符串可以嵌入${}变量，空格，缩进，换行都会被保留，比之前的写法更简洁，更易读<br>

## javascript基础<br>

1. new操作符的实现原理<br>
创建一个空对象<br>
空对象原型设为构造函数的prototype<br>
构造函数this指向空对象，执行函数<br>
返回结果，结果如果不是object则返回空对象<br>

2. map和Object的区别---了解即可<br>

3. map和weakMap的区别---了解即可<br>

4. JavaScript有哪些内置对象<br>
Infinity, NaN, undefined, null<br>
eval(), parseInt(), parseFloat()<br>
Object, Function, Boolean等<br>
Number, Math, Date<br>
String, RegExp<br>
Map, Set, WeakMap, WeakSet<br>
JSON<br>
Promise<br>
Reflect, Proxy<br>

5. 常用的正则表达式有哪些？<br>
const reg_phone = /^1[345678]\d{9}$/g<br>

6. 对JSON的理解---了解即可<br>

7. JavaScript脚本延迟加载的方式有哪些？<br>
defer属性，会使外部脚本立即下载，与文档加载同时进行，文档加载完成立即执行，脚本会按照顺序依次执行，但在浏览器执行不保证一定顺序就对<br>
async属性，外部脚本异步加载，与文档加载同时进行，加载完立即执行，调用顺序是不确定的<br>
动态创建script插入dom<br>
设置定时器<br>
把脚本放在最后加载<br>

8. JavaScript 类数组对象的定义？<br>
拥有length和若干索引属性的对象都可称为类数组对象<br>
常见的有arguments和DOM返回结果<br>
类数组转数组的方法：<br>
[...arguments]<br>
Array.from(arguments)<br>
Array.prototype.slice.call(arguments)<br>
Array.prototype.splice.call(arguments, 0)<br>
Array.prototype.concat.apply([], arguments)<br>

9. 数组有哪些原生方法？<br>
toString() join()<br>
push, pop, shift, unshift, reverse, sort, splice 改变原数组<br>
concat, slice<br>

10. Unicode、UTF-8、UTF-16、UTF-32的区别？---了解即可<br>

11. 常见的位运算符有哪些？其计算规则是什么？---了解即可<br>

12. 为什么函数的 arguments 参数是类数组而不是数组？如何遍历类数组?<br>
因为arguments拥有length，它的属性也是从零递增的数字，但是并不拥有数组的常见的方法，所以叫类数组<br>
调用Array原型上的遍历方法<br>
或者先转为数组，再遍历<br>

13. 什么是 DOM 和 BOM？<br>
DOM是文档对象模型，BOM是浏览器对象模型，document对象是window对象下的子对象，是归属于BOM的<br>

14. 对类数组对象的理解，如何转化为数组<br>
拥有length和若干索引属性的对象都可称为类数组对象<br>
常见的有arguments和DOM返回结果<br>
类数组转数组的方法：<br>
[...arguments]<br>
Array.from(arguments)<br>
Array.prototype.slice.call(arguments)<br>
Array.prototype.splice.call(arguments, 0)<br>
Array.prototype.concat.apply([], arguments)<br>

15. escape、encodeURI、encodeURIComponent 的区别<br>
encodeURI转义会对特殊字符保留<br>
encodeURIComponent会连同特殊字符一起转义<br>

16. 对AJAX的理解，实现一个AJAX请求<br>
ajax是指通过js的异步通信，从服务端获取xml文档从中提取数据，再更新当前网页的对应部分，不必刷新整个网页的一种技术<br>

17. JavaScript为什么要进行变量提升，它导致了什么问题？<br>
解析和预编译阶段的变量提升可以提高性能，让函数在执行时预先为变量分配栈空间<br>
变量提升还可以提升容错性，使一些不规范的代码正常运行<br>
缺点：<br>
变量提升会覆盖外层变量，变为undefined<br>

18. 什么是尾调用，使用尾调用有什么好处？<br>
尾调用是指在函数最后一步调用函数，因为函数调用时是基于调用栈的，当在一个函数内部调用另一个函数，会保留当前执行上下文，创建新的上下文加入栈中<br>
如果是尾调用，就不会保留当前上下文，从而节省了内存，这就是尾调用优化<br>
es6的尾调用优化仅在严格模式开启，正常模式无效<br>

19. ES6模块与CommonJS模块有什么异同？<br>
es6 module是对模块的引用（export default效果等同于commonJS），commonJS是对模块的浅拷贝，基本类型会缓存，引用类型实时取值<br>
es6 module是编译时加载，commonJS是运行时加载<br>
es6 module是异步加载，commonJS是同步加载<br>

20. 常见的DOM操作有哪些<br>
getElementById, getElementsByTagName, getElementsByClassName, querySelectorAll<br>
createElement, appendChild<br>
removeChild<br>

21. use strict是什么意思 ? 使用它区别是什么？<br>
严格模式，该模式消除了语法的不合理，不严谨之处，减少怪异行为，保证代码运行安全。<br>
提高编译器效率，提升运行速度。<br>
区别：<br>
禁止使用with语句<br>
禁止对象重名属性<br>
禁止this指向全局对象<br>

22. 如何判断一个对象是否属于某个类？<br>
instanceof判断构造函数的prototype是否在对象原型链上<br>
Object.prototype.toString.call()来进行判断<br>
constructor是否指向构造函数，但这种方法不安全，因为constructor可以被改<br>

23. 强类型语言和弱类型语言的区别<br>
强类型语言规定变量先定义类型再使用，如果不经过强制类型转换，类型固定不会变<br>
弱类型语言的变量类型可以被忽略，可以将字符串和数字拼接，js会进行强制类型转换<br>
强类型语言可能速度上稍逊弱类型语言，但是可以规避很多错误<br>

24. 解释性语言和编译型语言的区别---了解即可<br>

25. for...in和for...of的区别<br>
for...in主要针对遍历对象，for...of可以遍历所有含有Iterator接口的数据结构<br>

26. 如何使用for...of遍历对象<br>
添加[Symbol.Iterator]属性，并指向一个迭代器<br>

27. ajax、axios、fetch的区别<br>
ajax是一种无需重载页面，实现页面局部刷新的技术，但是因为不符合mvvm的浪潮被淘汰<br>
fetch是基于原生promise实现的，语法简洁，更加语义化<br>
fetch的缺点：<br>
只会对网络错误报错，400,500不会reject<br>
无法监测请求进度<br>
不支持超时控制<br>
axios是一种基于promise封装的http客户端<br>
在浏览器发起xhr请求，node端发起http请求，支持promise的api，可以监听请求和返回，取消请求，有超时控制，自动转化json数据，客户端抵御xsrf攻击<br>

28. 数组的遍历方法有哪些<br>
for循环，for...of，foreach，map，every，some，filter，find，findIndex，reduce<br>

29. forEach和map方法有什么区别<br>
foreach会为每个元素执行操作，没有返回值，是否改变原数组看改变的是原始类型还是引用类型<br>
map会对每个元素执行完操作，返回一个新数组<br>


## 原型与原型链<br>

1. 对原型、原型链的理解<br>
js在使用构造函数创建对象时，构造函数有个prototype属性，里面包含了所有对象共享的属性和方法，对象内部的指针指向prototype，这个指针被称为原型<br>
prototype因为也是一个对象，它也有自己的原型，层层向上链接成一个原型链，原型链的尽头是null<br>

2. 原型修改、重写<br>
原型重写会导致对象的constructor指向改后原型的构造函数，所以我们需要手动指定constructor回来<br>

3. 原型链指向<br>
4. 原型链的终点是什么？如何打印出原型链的终点？<br>
null Object.prototype.__proto__<br>

5. 如何获得对象非原型链上的属性？<br>
hasOwnProperty判断是否自身的属性还是原型链上的<br>

## 执行上下文/作用域链/闭包<br>

1. 对闭包的理解<br>
一个函数引用了不属于自身作用域的变量，这个变量叫做自由变量，引用了自由变量的函数就是闭包<br>
闭包的一个用途就是通过返回闭包函数，从而在外部访问函数内的变量<br>
另一个用途是使函数作用域中的变量保存在内存中，因为闭包保存了对变量的引用，不会被回收<br>

2. 对作用域、作用域链的理解<br>
全局作用域，函数作用域，块级作用域<br>
在当前作用域查找变量时，如果找不到，依次向上级作用域查找，直到全局作用域终止，这链接成了作用域链<br>
通过作用域链，可以查找外层的变量和函数，保证了执行环境可使用的变量的有序访问<br>

3. 对执行上下文的理解<br>
全局执行上下文，函数执行上下文，eval（不常用）<br>
执行上下文栈：<br>
js执行代码时，首先将全局执行上下文压入执行栈，每当遇到函数调用，都会将函数调用栈压入栈顶，调用完，出栈，最后代码全部执行完，全局执行上下文出栈<br>
执行上下文是js在解析代码时，会先创建全局执行上下文，将变量赋值为undefined，函数声明为可使用。在一个函数执行前，创建函数执行上下文，会比前者多出一些参数，例如this，arguments<br>

## this/call/apply/bind<br>

1. 对this对象的理解<br>
this是执行上下文中的属性，指向最后调用函数的对象<br>
函数调用模式：this指向全局对象<br>
对象属性模式：this指向该对象<br>
构造器模式：this指向new出来的对象<br>
call/apply/bind：this指向可以改变，指向我们指定的对象。bind返回的函数的this如果是new的，this被改为新的对象<br>
优先级为：构造器模式 > call/apply/bind > 对象属性模式 > 函数调用模式<br>

2. call() 和 apply() 的区别？<br>
call第二个参数为依次传递，apply第二个参数传入数组或者类数组<br>

3. 实现call、apply 及 bind 函数（建议看一下鲨鱼哥的掘金手写）<br>

## 异步编程<br>

1. 异步编程的实现方式？<br>
回调函数的方式，promise链式调用，generator，async/await<br>
generator可以以同步方式来书写，在外部手动控制异步流程，async是基于generator和promise的语法糖，可以自执行<br>

2. setTimeout、Promise、Async/Await 的区别<br>
setTimeout是宏任务，Promise，async/await是微任务<br>
setTimeout回调放进宏任务队列，等待执行栈清空，下一次事件循环执行<br>
promise.then回调放进相应宏任务的微任务队列，等待宏任务执行完再执行<br>
async表示函数中可能有异步方法，await后面跟一个表达式，async执行是，会执行await表达式，await后面的代码注册微任务，让出执行栈先执行同步代码<br>

3. 对Promise的理解<br>
Promise是一种异步解决方案，Promise是一个构造函数，接受一个函数，返回一个promise实例。<br>
promise实例有三种状态，pedding，fulfilled，rejected，状态只会从pedding转变成fulfilled或者rejected，并且状态变了就锁定了，不会再改变<br>
promise实例的原型上有then方法，可以注册状态改变后的回调函数，回调会注册成微任务，在本轮同步任务执行完后执行<br>

4. Promise的基本用法<br>
new Promise() 创建promise实例<br>
Promise.resolve() 将promise状态变更为fulfilled<br>
Promise.reject() 将promise状态变更为rejected<br>
then() 接受两个函数参数，第一个处理resolve，第二个处理reject，then支持链式调用<br>
catch() 相当于then第二个参数，处理reject，在resolve回调抛出错误时，会进入catch，不会阻断下面代码的执行<br>
all() 接收一个promise数组，等待所有promise状态变更为fulfilled，all对应的promise实例才会变更为fulfilled<br>
race() 接收一个promise数组，等待第一个promise状态变更为，race对应的promise实例随之变更<br>
finally promise必定会执行的回调<br>

5. Promise解决了什么问题<br>
回调地狱<br>

6. Promise.all和Promise.race的区别的使用场景<br>
Promise.all返回所有promise的结果组成的数组，返回的结果集与promise数组顺序一致，适合在发送多个请求并根据顺序使用数据的场景<br>
Promise.race只会返回第一个改变状态的promise的结果<br>

7. 对async/await 的理解<br>
async其实就是generator的语法糖，async相当于*，await相当于yield，它能实现的用then链也能实现，但是它可以用同步的写法更优雅<br>
async声明一个函数是异步的，await等待异步方法执行，语法上强制await必须在async内部<br>
async返回一个promise对象，需要用then来处理这个promise对象<br>

8. await 到底在等啥？<br>
await在等待它的表达式的结果，如果表达式是普通函数或者直接量，直接执行剩下的代码，如果结果是promise对象，就会等待promise对象变更状态，再执行之后的代码<br>

9. async/await的优势<br>
对promise链式调用的优化，可以以同步的方式来编码<br>

10. async/await对比Promise的优势<br>
代码阅读更清晰，以同步的方式来编写<br>
传递中间值更方便<br>
错误处理友好，可以使用try/catch<br>

11. async/await 如何捕获异常<br>
try, catch<br>

12. 并发与并行的区别？---了解即可<br>

13. 什么是回调函数？回调函数有什么缺点？如何解决回调地狱问题？<br>
例如ajax请求完成执行的函数<br>
缺点：<br>
容易造成回调地狱，耦合性太强，不利于阅读<br>
promise，async/await<br>

14. setTimeout、setInterval、requestAnimationFrame 各有什么特点？<br>
因为js是单线程的缘故，setTimeout，setInterval都会因为耗时操作影响执行的精准度<br>
requestAnimationFrame自带函数节流，确保每一帧只会执行一次，而且延时效果是精准的<br>

## 面向对象<br>

1. 对象创建的方式有哪些？<br>
 字面量直接创建<br>
 工厂模式，只是对复用代码的简单封装<br>
 构造函数模式，方法会重复声明<br>
 原型模式，对象属性无法传参<br>
 构造函数加原型组合模式，基本完美，代码封装性还不够好<br>
 动态原型模式，对组合模式的优化，封装性更好，完美<br>

2. 对象继承的方式有哪些？<br>
原型链继承，Child.prototype = new Father() 不同实例的原型是共享的，属性是引用类型，修改属性会相互影响，无法向父类传递参数<br>
构造函数继承，Child内部使用call调用Father，缺点是方法只能在构造函数内定义，无法复用。Father.prototype上的属性和方法无法继承，可以向父类传递参数<br>
组合继承，也就是原型链加构造函数继承，原型链实现继承父类原型的属性和方法，构造函数实现继承父类自身的属性，它融合了二者的优点。缺点是会调用两次父类函数，子对象的原型上会有所有的父类实例属性<br>
原型式继承，用一个对象作为原型创建子对象 Object.create()<br>
寄生式继承，创建一个对象副本，然后做扩展<br>
寄生组合式继承，解决了组合继承原型链有不必要属性的问题，子类的prototype不再由父类实例重写，而是寄生于父类原型<br>

## 垃圾回收与内存泄漏---了解即可<br>

1. 浏览器的垃圾回收机制<br>
垃圾回收的概念：<br>
当变量不在需要使用时，会被回收，以便空出内存<br>
垃圾回收机制：<br>
JavaScript会自动对不再使用的变量进行回收，释放内存<br>
全局变量会持续存在到页面卸载<br>
局部变量在函数执行完毕卸载<br>
闭包是个例，因为内层函数会保持对自由变量的引用，尽管函数执行完毕，但是自由变量不会被回收<br>
垃圾回收的方式：<br>
标记清除，引用计数<br>
引用计数：<br>
一个引用类型赋值给变量，值计数加1，该值再赋值给其他变量，计数再加1，如果变量指向了其他值，原先值引用减1<br>
引用计数最致命的缺点，无法回收循环引用的对象，最终导致内存泄漏<br>
标记清除：<br>
现在的主流方式，变量进入执行环境，会被标记为不可回收，离开环境时，会打上回收的标记，js引擎会定时回收打上回收标记的变量<br>
优化：<br>
数组清空可以设置length为0<br>
对象尽量复用，不再使用的对象赋值为null<br>

2. 哪些情况会导致内存泄漏<br>
意外的全局变量<br>
遗忘的定时器<br>
脱离dom的引用<br>
不合理的闭包<br>

基础
1. CSS 选择器及其优先级
标签选择器，伪元素选择器：1
类选择器，属性选择器，伪类选择器：10
id选择器：100
内联：1000
!important

2. CSS 中可继承与不可继承属性有哪些---了解即可

3. display 的属性值及其作用

4. display 的 block、inline 和 inline-block 的区别
block是块级元素，可以设置宽高，margin，padding，多个元素另起一行
inline是行内元素，不可以设置宽高，margin和padding只能设置水平方向，多个元素排列在同一行
inline-block将元素设为inline元素，但内容作为block元素呈现

5. 隐藏元素的方法有哪些
display: none
visibility: hidden
opacity: 0
position: absolute将元素移除视口
z-index: 负值
transform: scale(0, 0)
clip

6. link 和@import 的区别
link除了加载css，还可以加载RSS等其他事务，@import只能加载css
link与页面加载同时进行，后者等待页面加载完才会执行
link没有兼容问题，后者只有css2.1才支持，低版本浏览器不支持
link支持使用js控制dom来改变样式，后者不支持

7. transition 和 animation 的区别---了解即可

8. display:none 与 visibility:hidden 的区别
前者在渲染树中不会占据空间，后者还会占用，只是不可见
前者是非继承属性，子元素都会消失，后者是继承属性，子元素可以设置visible显示
修改display通常会造成重排，后者只会造成本元素的重绘
读屏器读取不到前者，后者可以

9. 伪元素和伪类的区别和作用？
伪元素在元素前后插入额外的元素，它们不会在文档中生成，但是外部可见
伪类是在现有元素上添加类名，不会产生新元素

10. 对 requestAnimationframe 的理解
该方法传入callback，会在下一次重绘前执行
优势：
节省cpu开销，页面未激活时，动画会停止
函数节流，保证每一帧只执行一次callback
setTimeout的缺点：
需要放入异步队列，等待主线程执行完再执行，所以会比预期晚
间隔时间不一定会和帧刷新时间吻合，可能丢帧

11. 对盒模型的理解
分为标准盒模型和怪异盒模型
前者width和height只包含content
后者包含content，padding，border
可以通过设置box-sizing来改变

12. 为什么有时候⽤translate来改变位置⽽不是定位？
前者不会触发重绘和回流，后者会
前者更高效，transform会创建gpu图层，后者用cpu计算的

13. li 与 li 之间有看不见的空白间隔是什么原因引起的？如何解决？
浏览器会把行内元素之间的空白字符渲染成一个空格
解决办法：
float，li编写在同一行，ul设置fon-size：0，ul设置letter-spacing：-8px；li设置letter-spacing：normal

14. CSS3 中有哪些新特性
各种选择器，圆角，阴影，线性渐变，旋转，缩放，倾斜，动画

15. 替换元素的概念及计算规则---不需要看

16. 常见的图片格式及使用场景
bmp，gif，jpg，jpeg，png-8，png-24，svg，webp

17. 对 CSSSprites 的理解---了解即可

18. 什么是物理像素，逻辑像素和像素密度，为什么在移动端开发时需要用到@3x, @2x 这种图片？
设备的像素叫物理像素，元素的像素叫逻辑像素，一个逻辑像素等于几个物理像素，像素密度就是多少
移动端通过媒体查询，不同像素密度的设备选用不同尺寸的图片

19. margin 和 padding 的使用场景

20. 对line-height 的理解及其赋值方式
带单位，纯数字，百分比

21. CSS 优化和提高性能的方法有哪些？
加载性能：
css压缩，css单一样式，减少使用@import，使用link
选择器性能：
避免使用通配规则
尽量少的去对标签选择，使用class
了解哪些属性可以继承，避免重复
如有id选择器，则不要为规则加标签
渲染性能：
慎重使用高性能属性：浮动，定位
尽量避免重绘和回流
去除空规则
属性为0不加单位
属性为小数去除前面的0
标准化浏览器前缀
不使用@import
选择器优化嵌套，避免层级过深
css雪碧图
正确使用display
可维护性和健壮性：
抽离公共样式
样式与内容分离

22. CSS 预处理器/后处理器是什么？为什么要使用它们？
预处理器为css增加了一些编程特性，无需考虑浏览器兼容问题，可以使用变量，函数，层级等来增加可读性和可维护性
后处理器通常是在完成的样式表中根据css规范处理css，如postcss添加浏览器兼容前缀
使用原因：
结构清晰，便于扩展
可以实现多重继承
可以屏蔽浏览器私有语法的差异
完美兼容css代码，可以运用到老项目

23. ::before 和 :after 的双冒号和单冒号有什么区别？
两者都是伪元素，单冒号是css2.1的写法，双冒号是css3的写法

24. display:inline-block 什么时候会显示间隙？
有空格时会有空隙
margin负值解决
font-size：0，letter-spacing，word-spacing解决

25. 单行、多行文本溢出隐藏

26. Sass、Less 是什么？为什么要使用他们？
css预处理器，是css的抽象层。他们为css提供了动态语言的特性，变量，函数，继承，运算等
结构清晰，易于扩展，可以屏蔽浏览器私有语法的差异
可以轻松实现多重继承，完美兼容css代码，可以运用到老项目

27. 对媒体查询的理解？
通过媒体查询，可以为不同媒体设备提供不同的样式，通常用来做响应式页面。页面resize，样式也会更新

28. 对 CSS 工程化的理解
css工程化主要为了解决以下问题：
宏观设计，编码优化，构建优化，可维护性
预处理器，postcss，webpack loader
预处理器对标1,2,4，宏观上可以通过extend和mixin优化目录结构，层级，运算等特性提升了编码爽感，代码一目了然，同时也提升了可维护性
postcss是后处理器，可以对不同浏览器加上不同的前缀，而且有强大的插件机制，极大强化了css能力
css-loader对css进行编译处理，可以让webpack能处理css
style-loader创建style标签，将样式插入html
css-loader执行一定在style-loader之前（若插入了未编译的代码，webpack会报错）

29. 如何判断元素是否到达可视区域
img.offsetTop < window.innerHeight + document.body.scrollTop

30. z-index 属性在什么情况下会失效
父元素position为relative时，子元素z-index会失效
元素没有设置position为非static属性
元素同时设置了float

31. CSS3 中的 transform 有哪些属性
translate，rotate，scale，skew

页面布局
1. 常见的 CSS 布局单位
px, em, rem, %, vw/vh

2. px、em、rem 的区别及使用场景
只需适配少量设备，且分辨率对页面影响不大，适合px
需要适配多种设备，使用rem

3. 两栏布局的实现

4. 三栏布局的实现

5.水平垂直居中的实现

6. 如何根据设计稿进行移动端适配？
主要从两个维度来适配，像素密度和屏幕尺寸，对于前者，可以使用媒体查询，不同像素密度使用不同精度的图片，以保证图片不会失真
对于后者，为了适配不同屏幕，应当按照比例来还原设计稿，可以使用rem，vw，vh等单位

7. 对 Flex 布局的理解及其使用场景
flex将元素变为容器，子元素变为项目，容器内有一根主轴和交叉轴，子元素的float，clear，vertical-align将失效。
使用justify-cotent设置主轴排列方式，align-items设置交叉轴排列方式，flex-wrap设置一行放不下时的排列方式。
flex：1是flex-grow，flex-shrink，flex-basis的简写

8. 响应式设计的概念及基本原理
指网站可以兼容多个终端，其原理主要是使用媒体查询针对不同终端处理，页面头目必须有meta声明的viewport

定位与浮动
1. 为什么需要清除浮动？清除浮动的方式
浮动会引起高度坍塌，与浮动元素同级的元素也会紧跟其后，若浮动元素不是第一个元素，之前的元素也要浮动，否则会影响页面结构。
清除浮动：
父元素设置height
父元素overflow：hidden或者auto
浮动元素后添加空div，clear：both
使用after伪元素clear：both

2. 使用 clear 属性清除浮动的原理？
clear其实是避免了浮动元素对该元素的影响。设置both包含了left和right，因为两个不可能同时生效，所以可以直接为both
clear属性只对块级元素生效，所以after伪元素需要设置display

3. 对 BFC 的理解，如何创建 BFC
BFC是一个独立的布局环境，可以理解为一个容器，容器内的布局不受外部影响

BFC创造条件：
根元素body
元素设置浮动
元素设置绝对定位
display：inline-block，flex等
overflow：hidden，scroll，auto

BFC特点：
子元素margin重叠
计算高度需要计算浮动元素的高度
容器内元素不会影响外部元素

BFC作用：
解决margin重叠
解决浮动引起的高度坍塌
创建自适应两栏布局

4. 什么是 margin 重叠问题？如何解决？
在垂直方向上的两个块级元素的margin重叠
兄弟元素重叠：
底部元素变为display：inline-block
浮动或者定位
父子元素重叠：
overflow：hidden
父元素设置透明边框
子元素变为display：inline-block
浮动或者定位

5. 元素的层叠顺序
背景和边框
负z-index
块级盒子
浮动元素
行内盒子
z-index：0
正z-index

6. position 的属性有哪些，区别是什么
static
absolute
relative
fixed
inherit

7. display、float、position 的关系
position优先级最高，会忽略float，display会调整
float不为none或者它是根元素时，display会调整
最后三者皆不是，display等同设置值

8. absolute 与 fixed 共同点与不同点
共同点：
display：inline-block
会使元素脱离文档流
覆盖非定位元素
不同点：
absolute相对于祖先元素第一个定位元素，fixed相对于浏览器
如果页面有滚动条，absolute会随着相对元素滚动，fixed会固定

9. 对 sticky 定位的理解---了解即可

场景应用
1. 实现一个三角形

2. 实现一个扇形

3. 实现一个宽高自适应的正方形

4. 画一条 0.5px 的线
transform: scale()
meta viewport

5. 设置小于 12px 的字体
transform: scale()
使用图片

6. 如何解决 1px 问题？
获取设备的像素密度，手动设置为1px/密度
伪元素先放大后缩小
动态设置meta viewport缩放页面

## HTML<br>

1. src 和 href 的区别<br>
src表示对资源的引用，当浏览器解析到该行时，会暂停其他资源的下载，直到该资源下载，编译，执行完毕<br>
href表示超文本引用，当浏览器识别到指向的文件时，就会并行下载资源，不会暂停对其他资源的处理<br>

2. 对 HTML 语义化的理解<br>
语义化是指根据内容的结构化，选择合适的标签<br>
有利于SEO，增强可读性<br>

3. DOCTYPE(⽂档类型) 的作⽤<br>
是HTML5中的文档类型声明，它会告诉浏览器应该以什么类型来解析文档，必须在第一行，有两种模式<br>
标准模式(模式) 浏览器以其最高标准来呈现页面<br>
怪异模式 浏览器以宽松的向后兼容的方式来呈现<br>


4. script 标签中 defer 和 async 的区别<br>
两者都可以异步加载js脚本<br>
多个defer会按加载顺序执行，async不能保证执行顺序<br>
async 文档加载执行和js脚本加载执行是并行的<br>
defer js脚本仅加载和文档加载执行并行，待所文档执行完再执行js脚本，在DOMContentLoaded触发之前<br>

5. 常⽤的 meta 标签有哪些<br>
charset 编码类型<br>
keywords 页面关键词<br>
description 页面描述<br>
viewport 页面适配<br>


6. HTML5 有哪些更新<br>
语义化标签<br>
媒体标签<br>
表单类型，属性和事件<br>
dom查询 querySelector querySelectorAll<br>
数据存储 localStorage sessionStorage<br>
canvas，地理定位api，websocket<br>
history api go，forward，back，pushstate<br>


7. img 的 srcset 属性的作⽤？<br>
在响应式页面中，浏览器自动选择合适质量的图片地址<br>

8. 行内元素有哪些？块级元素有哪些？ 空(void)元素有那些？<br>
a，span，img，input<br>
div，p，h1，ul，li，ol<br>
br，img，input，link，meta<br>

9. 说一下 web worker<br>
在执行脚本是，页面是不可响应的 webworker是后台运行的js，在进行复杂操作时，不会阻塞主线程，不会影响性能，通过postmessage传回结果到主线程<br>

10. HTML5 的离线储存怎么使用，它的工作原理是什么--了解即可<br>

11. 浏览器是如何对 HTML5 的离线储存资源进行管理和加载？<br>

12. title 与 h1 的区别、b 与 strong 的区别、i 与 em 的区别？---了解即可<br>

13. iframe 有那些优点和缺点？<br>
iframe会创建另外一个文档的内联框架<br>
优点：可以使脚本并行加载，跨子域通信<br>
缺点：iframe会阻塞主页面onload事件，无法被一些搜索引擎所识别<br>

14. label 的作用是什么？如何使用？---了解即可<br>

15. Canvas 和 SVG 的区别<br>
svg是可缩放矢量图形，是基于xml描述的2d图形的语言。每个绘制的图形可视为对象，如果属性发生改变，浏览器将重新绘制<br>
canvas是画布，通过JavaScript来绘制2d图形，是逐像素渲染的。其位置发生改变，就会重新绘制<br>

16. head 标签有什么作用，其中什么标签必不可少？<br>
用于定义文档的头部，其中可以引入资源（脚本，样式），描述文档（元信息，标题），绝大多数头部信息不会真正作为内容呈现给用户<br>

17. 文档声明（Doctype）和<!Doctype html>有何作用? 严格模式与混杂模式如何区分？它们有何意义?<br>
<!Doctype html>的作用是使html用标准模式来解析页面，前者是怪异模式<br>
标准模式让各个浏览器统一执行一套规范，保证了旧网站的正常运行<br>

18. 浏览器乱码的原因是什么？如何解决？---了解即可<br>

19. 渐进增强和优雅降级之间的区别<br>
渐进增强主要是针对低版本浏览器进行页面重构，保证基本功能，再针对高级浏览器进行改进<br>
优雅降级一开始就构建完整功能，再针对低版本浏览器向下兼容<br>

20. 说一下 HTML5 drag API---了解即可<br>
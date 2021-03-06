1移动端、响应式、自动化构建、HTTP、离线存储、WEB安全、优化、重构、团队协作、可维护、易用性、SEO、UED、架构、职业生涯、快速学习能力



涉及面试题：

1. 从 URL 输入到页面展现背后发生了什么事？
2. 一次完整的 HTTP 事务是怎么一个过程？
3. 浏览器是如何渲染页面的？
4. 浏览器的内核有哪些？分别有什么代表的浏览器？
5. 刷新页面，js 请求一般会有哪些地方有缓存处理？

其他部分：

1 http状态码

2 xss，csrf的概念以及防范方法

3 CommonJs，AMD，CMD规范

4 谈谈对前端模块化的理解

5 优雅降级和渐进增强

6 前端优化（提高网页的加载速度）

7 渲染优化：

8 谈谈以前端角度出发做好SEO需要考虑什么？

9 我们知道可以以外链的方式引入CSS文件，请谈谈外链引入CSS有哪些方式，这些方式的性能有区别吗？

10  前端页面有哪三层构成，分别是什么？作用是什么？

11 框架的优点

12 框架的缺点

- 原来公司工作流程是怎么样的，如何与其他人协作的？如何夸部门合作的？
- 你遇到过比较难的技术问题是？你是如何解决的？
- 设计模式 知道什么是singleton, factory, strategy, decrator么?
- 常使用的库有哪些？常用的前端开发工具？开发过什么应用或组件？

13 页面重构怎么操作？

14 列举IE与其他浏览器不一样的特性？

15 99%的网站都需要被重构是那本书上写的？

16 什么叫优雅降级和渐进增强？

17 是否了解公钥加密和私钥加密。

18 WEB应用从服务器主动推送Data到客户端有那些方式？

19 对Node的优点和缺点提出了自己的看法？

20 你有用过哪些前端性能优化的方法？

21 http状态码有那些？分别代表是什么意思？

22 一个页面从输入 URL 到页面加载显示完成，这个过程中都发生了什么？（流程说的越详细越好）

23 部分地区用户反应网站很卡，请问有哪些可能性的原因，以及解决方法？

24 从打开app到刷新出内容，整个过程中都发生了什么，如果感觉慢，怎么定位问题，怎么解决?

25 除了前端以外还了解什么其它技术么？你最最厉害的技能是什么？

26 你用的得心应手用的熟练地编辑器&开发环境是什么样子？

27 对前端工程师这个职位是怎么样理解的？它的前景会怎么样？

28 你怎么看待Web App 、hybrid App、Native App？

29 你移动端前端开发的理解？（和 Web 前端开发的主要区别是什么？）

30 你对加班的看法？

31 平时如何管理你的项目？

32 如何设计突发大规模并发架构？

33 当团队人手不足，把功能代码写完已经需要加班的情况下，你会做前端代码的测试吗？

34 说说最近最流行的一些东西吧？常去哪些网站？

35 知道什么是SEO并且怎么优化么? 知道各种meta data的含义么?

36 移动端（Android IOS）怎么做好用户体验?

37 简单描述一下你做过的移动APP项目研发流程？

38 你在现在的团队处于什么样的角色，起到了什么明显的作用？

39 你认为怎样才是全端工程师（Full Stack developer）？

40 介绍一个你最得意的作品吧？

41 你有自己的技术博客吗，用了哪些技术？

42 对前端安全有什么看法？

43 是否了解Web注入攻击，说下原理，最常见的两种攻击（XSS 和 CSRF）了解到什么程度？

44 项目中遇到国哪些印象深刻的技术难题，具体是什么问题，怎么解决？。

45 最近在学什么东西？

46 你的优点是什么？缺点是什么？

47 如何管理前端团队?

48 最近在学什么？能谈谈你未来3，5年给自己的规划吗？





#### 一、从 URL 输入到页面展现背后发生了什么事？

1. 浏览器根据请求的 URL 交给 DNS 域名解析，找到真实 IP，向服务器发起请求；

2. 服务器交给后台处理完成后返回数据，浏览器接收文件（HTML、JS、CSS、图象等）；

3. 浏览器对加载到的资源（HTML、JS、CSS 等）进行语法解析，建立相应的内部数据结构（如 HTML 的 DOM）；

4. 载入解析到的资源文件，渲染页面，完成。

   

- DNS 解析:将域名解析成 IP 地址
- TCP 连接：TCP 三次握手(为了防止已失效的连接请求报文段突然又传送到了服务端，因而产生错误”。)
- 发送 HTTP 请求
- 服务器处理请求并返回 HTTP 报文
- 浏览器解析渲染页面
- 断开连接：TCP 四次挥手



#### 二、一次完整的 HTTP 事务是怎么一个过程？

1. 域名解析；
2. 发起 TCP 的三次握手；
3. 建立 TCP 连接后发起 http 请求；
4. 服务器端响应 http 请求，浏览器得到 html 码；
5. 浏览器解析 html 代码，并请求 html 代码中的资源；
6. 浏览器对页面进行渲染并呈现给客户。

#### 三、浏览器是如何渲染页面的？

浏览器页面渲染流程：

浏览器从 HTTP 服务器获取 html 文档，到呈现页面给用户，会经过以下几个步骤：

**1. 解析文档构建 DOM 树**

浏览器的解析内容可以分为三个部分：

- HTML/XHTML/SVG：解析这三种文件后，会生成 DOM 树（DOM Tree）；
- CSS：解析样式表，生成 CSS 规则树（CSS Rule Tree）；
- JavaScript：解析脚本，通过 DOM API 和 CSSOM API 操作 DOM Tree 和 CSS Rule Tree，与用户进行交互。

以上三类文件的执行顺序会根据其在文档中的位置及其标签属性的不同而有异同。



**2. 构建渲染树**

解析文档完成后，浏览器引擎会将 CSS Rule Tree 附着到 DOM Tree 上，并根据 DOM Tree 和 CSS Rule Tree 构造 Rendering Tree（渲染树）。

此处需要注意：

- Render Tree 和 DOM Tree 的区别在于，类似 Head 或 display: none; 之类的东西不会放在渲染树中；
- 将 CSS Rule Tree 匹配到 DOM Tree需要解析 CSS 的选择器，为了提高该过程的性能，DOM 树应该尽量小，CSS Selector 应该尽量使用 id 和 class，避免过度层叠。



**3. 布局与绘制渲染树**

解析 position，overflow，z-index 等等属性，计算每一个渲染树节点的位置和大小，此过程被称为 reflow。最后调用操作系统的 Native GUI API 完成绘制（repain）。

注意：

渲染树的节点，在 Gecko 中称为 frame，而在 webkit 中称为 renderer。



**简述浏览器渲染过程**

1.  **解析HTML以构建DOM树**：渲染引擎开始解析HTML文档，转换树中的html标签或js生成的标签到DOM节点，它被称为 — 内容树。
2.  **构建渲染树**：解析CSS（包括外部CSS文件和样式元素以及js生成的样式），根据CSS选择器计算出节点的样式，创建另一个树 — 渲染树。
3.  **布局渲染树**: 从根节点递归调用，计算每一个元素的大小、位置等，给每个节点所应该出现在屏幕上的精确坐标。
4.  **绘制渲染树**: 遍历渲染树，每个节点将使用UI后端层来绘制。

**CSS阻塞渲染**

- CSS 是阻塞渲染的资源。需要将它尽早、尽快地下载到客户端，以便缩短首次渲染的时间。
- 这就是为什么我们将外部样式的引入放在head标签中的原因，在body渲染前先把相对完整CSSOM Tree构建好。

**JavaScript阻塞渲染**

- JavaScript 会阻止 DOM 构建和延缓网页渲染。 为了实现最佳性能，可以让您的JavaScript 异步执行，并去除关键渲染路径中任何不必要的 JavaScript。

#### 四、浏览器的内核有哪些？分别有什么代表的浏览器？

**Trident 内核**：代表作品是 IE。

**Gecko 内核**：代表作品是 Firefox，即火狐浏览器。

**Webkit 内核**：代表作品是 Safari Chromewebkit、曾经的 Chrome，是开源的项目。

**Presto 内核**：代表作品是 Opera ，Presto 是由 Opera Software 开发的浏览器排版引擎，它是世界公认最快的渲染速度的引擎。在 13 年之后，Opera 宣布加入谷歌阵营，弃用了 Presto。

**Blink 内核**：由 Google 和 Opera Software 开发的浏览器排版引擎，2013 年 4 月发布。现在 Chrome 内核是 Blink。谷歌还开发了自己的 JS 引擎，V8，使 JS 运行速度极大地提高了。



#### 五、刷新页面，js 请求一般会有哪些地方有缓存处理？

1. DNS 缓存：短时间内多次访问某个网站，在限定时间内，不用多次访问 DNS 服务器；
2. CDN 缓存：内容分发网络（人们可以在就近的代售点取火车票了，不用非得到火车站去排队）；
3. 浏览器缓存：浏览器在用户磁盘上，对最新请求过的文档进行了存储；
4. 服务器缓存：将需要频繁访问的 Web 页面和对象保存在离用户更近的系统中，当再次访问这些对象的时候加快了速度。







三、其他部分

（1）http状态码

http状态码是表示服务器对请求的响应状态，主要分为以下几个部分

1**：这类响应是临时响应，只包含状态行和某些可选的响应头信息，并以空行结束

2**：表示请求成功，

3**：表示重定向

4**：表示客户端错误

5**：表示服务器端错误

100（continue），客户端应当继续发送请求。这个临时响应是用来通知客户端它的部分请求已经被服务器接收

200（OK），表示请求成功，请求所希望的响应头或数据体将随此响应返回。

202（Accepted），服务器已接受请求，但尚未处理。

204（No-Content），服务器成功处理了请求，但不需要返回任何实体内容

205（Reset-Content），服务器成功处理了请求，且没有返回任何内容。但是与204响应不同，返回此状态码的响应要求请求者重置文档视图。该响应主要是被用于接受用户输入后，立即重置表单，以便用户能够轻松地开始另一次输入。

206（Partial-Content），服务器已经成功处理了部分 GET 请求。

301（Moved-Permanently），永久性重定向

302（Moved-Temporarily），暂时性重定向

304（Not-Modified），浏览器端缓存的资源依然有效

400（Bad-Reques），请求有误，当前请求无法被服务器理解。

401（Unauthorized），当前请求需要用户验证。

403（Forbidden），服务器已经理解请求，但是拒绝执行它。

404（Not-Found），请求的资源没有被找到

500（Interval Server Error），服务器内部错误

502（Bad GateWay），网关出错

503（Service Unavailable），由于临时的服务器维护或者过载，服务器当前无法处理请求。

504（Gateway Timeout），作为网关或者代理工作的服务器尝试执行请求时，未能及时从上游服务器（URI标识出的服务器，例如HTTP、FTP、LDAP）或者辅助服务器（例如DNS）收到响应。

（2）xss，csrf的概念以及防范方法

大公司如bat在面试的时候，web安全问题是必问的问题，所以一定要懂，要彻底理解xss和csrf的概念和防范方式，最好在项目中有用到对这两种攻击的防范，这样会给你的面试加很多分。由xss和csrf涉及的东西比较多，我就不具体给出了，详情请看[XSS攻击及防御](https://link.zhihu.com/?target=http%3A//blog.csdn.net/ghsau/article/details/17027893)，[CSRF攻击](https://link.zhihu.com/?target=http%3A//www.cnblogs.com/hyddd/archive/2009/04/09/1432744.html)

（3）CommonJs，AMD，CMD规范

对于前端模块化来说，这三个规范是必须要了解的，详情请看我的这篇文章[CommonJS，AMD，CMD](https://zhuanlan.zhihu.com/p/22954387)

（4）谈谈对前端模块化的理解

前端模块话就是把复杂的文件分成一个个独立的模块，比如js文件，分成独立的模块之后有利于代码的重用和维护，但是这样又会引来模块与模块之间的依赖问题，所以就有了CommonJS、AMD、CMD规范，最后出现了webpack，webpack就是前端模块话的一种解决方案，基本上大公司都会使用webpack，想要详细的学习webpack的话请看[webpack简明使用教程](https://zhuanlan.zhihu.com/p/23538138)

（5）优雅降级和渐进增强

优雅降级指的是一开始就构建功能完好的网站，然后在慢慢兼容低版本的浏览器，使得各个浏览器之间的差异不要太大。

渐进增强是指在基本功能得到满足的情况下，对支持新特性的浏览器使用新特性，带给用户更换的体验。

优雅降级和渐进增强的出发点不同，前者是慢慢向下兼容，是向后看，后着是慢慢向上，增强功能，是向前看。

（6）前端优化（提高网页的加载速度）

​    1、使用css sprites，可以有效的减少http请求数

​    2、使用缓存

​    3、压缩js，css文件，减小文件体积

​    4、使用cdn，减小服务器负担

​    5、懒加载图片

​    6、预加载css，js文件

​    7、避免dom结构的深层次嵌套

​    8、给DOM元素添加样式时，把样式放到类中，直接给元素添加类，减少重构，回流







(7) 渲染优化：

1.禁止使用iframe（阻塞父文档onload事件）

 

- iframe会阻塞主页面的Onload事件；
- 搜索引擎的检索程序无法解读这种页面，不利于SEO;
- iframe和主页面共享连接池，而浏览器对相同域的连接有限制，所以会影响页面的并行加载。

 

使用 iframe 之前需要考虑这两个缺点。如果需要使用 iframe，最好是通过 javascript 动态给 iframe 添加 src 属性值，这样可以绕开以上两个问题。

  

2.禁止使用gif图片实现loading效果（降低CPU消耗，提升渲染性能）；

 

3、使用CSS3代码代替JS动画（尽可能避免重绘重排以及回流）；

 

4、对于一些小图标，可以使用base64位编码，以减少网络请求。但不建议大图使用，比较耗费CPU；

 

小图标优势在于：

 

- 1.减少HTTP请求； 
- 2.避免文件跨域； 
- 3.修改及时生效；

 

5、页面头部的 会阻塞页面；（因为 Renderer进程中 JS线程和渲染线程是互斥的）；

 

6、页面头部 会阻塞页面；（因为 Renderer进程中 JS线程和渲染线程是互斥的）；

 

7、页面中空的 href 和 src 会阻塞页面其他资源的加载 (阻塞下载进程)；

​      

8、网页Gzip，CDN托管，data缓存 ，图片服务器；

 

9、前端模板 JS+数据，减少由于HTML标签导致的带宽浪费，前端用变量保存AJAX请求结果，每次操作本地变量，不用请求，减少请求次数

 

10、用innerHTML代替DOM操作，减少DOM操作次数，优化javascript性能。

 

11、当需要设置的样式很多时设置className而不是直接操作style。

 

12、少用全局变量、缓存DOM节点查找的结果。减少IO读取操作。

 

13、避免使用CSS Expression（css表达式)又称Dynamic properties(动态属性)。

 

14、图片预加载，将样式表放在顶部，将脚本放在底部  加上时间戳。

 

15、 避免在页面的主体布局中使用table，table要等其中的内容完全下载之后才会显示出来，显示比div+css布局慢。

 

对普通的网站有一个统一的思路，就是尽量向前端优化、减少数据库操作、减少磁盘IO。 向前端优化指的是，在不影响功能和体验的情况下，能在浏览器执行的不要在服务端执行，能在缓存服务器上直接返回的不要到应用服务器，程序能直接取得的结果不要到外部取得，本机内能取得的数据不要到远程取，内存能取到的不要到磁盘取，缓存中有的不要去数据库查询。减少数据库操作指减少更新次数、缓存结果减少查询次数、将数据库执行的操作尽可能的让你的程序完成（例如join查询），减少磁盘IO指尽量不使用文件系统作为缓存、减少读写文件次数等。程序优化永远要优化慢的部分，换语言是无法"优化"的。



##### 8 谈谈以前端角度出发做好SEO需要考虑什么？

- 1、了解搜索引擎如何抓取网页和如何索引网页。
- 2、Meta标签优化。
- 3、如何选取关键词并在网页中放置关键词。
- 4、了解主要的搜索引擎。
- 5、主要的互联网目录
- 6、按点击付费的搜索引擎。
- 7、搜索引擎登录。
- 8、链接交换和链接广泛度（Link Popularity）。
- 9、标签的合理使用。

##### 9 我们知道可以以外链的方式引入CSS文件，请谈谈外链引入CSS有哪些方式，这些方式的性能有区别吗？

CSS的引入方式最常用的有三种：

- 第一：在head部分加入 `<link rel="stylesheet" type="text/css" href="my.css"/>`, 引入外部的CSS文件。

- 第二：在head部分加入

  ```
  <style type="text/css"> 
  div{margin: 0;padding: 0;border:1px red solid;} 
  </style>
  ```

- 第三：直接在页面的标签里加 `<div style="border:1px red solid;">`





##### 10 前端页面有哪三层构成，分别是什么？作用是什么？

网页分成三个层次，即：结构层、表示层、行为层。

- 1、网页的结构层（structurallayer）由HTML 或XHTML 之类的标记语言负责创建。标签，也就是那些出现在尖括号里的单词，对网页内容的语义含义做出这些标签不包含任何关于如何显示有关内容的信息。例如，P标签表达了这样一种语义："这是一个文本段。"
- 2、网页的表示层（presentationlayer）由CSS 负责创建。CSS对"如何显示有关内容"的问题做出了回答。
- 3、网页的行为层（behaviorlayer）负责回答"内容应该如何对事件做出反应"这一问题。这是Javascript 语言和DOM 主宰的领域。







##### 11 框架的优点

- 重载页面时不需要重载整个页面，只需要重载页面中的一个框架页(减少了数据的传输，增加了网页下载速度)
- 方便制作导航栏

##### 12框架的缺点

- 会产生很多页面，不容易管理
- 不容易打印
- 浏览器的后退按钮无效
- 代码复杂,无法被一些搜索引擎索引到
- 多数小型的移动设备（PDA 手机）无法完全显示框架
- 多框架的页面会增加服务器的http请求
- 由于上面诸多缺点，因此不符合标准网页设计的理念,已经被标准网页设计抛弃

提示: 目前框架的所有优点完全可以使用Ajax实现，因此已经没有必要使用框架了。











- 原来公司工作流程是怎么样的，如何与其他人协作的？如何夸部门合作的？

- 你遇到过比较难的技术问题是？你是如何解决的？

- 设计模式 知道什么是singleton, factory, strategy, decrator么?

- 常使用的库有哪些？常用的前端开发工具？开发过什么应用或组件？

- 13 页面重构怎么操作？

  ```
  网站重构：在不改变外部行为的前提下，简化结构、添加可读性，而在网站前端保持一致的行为。
  也就是说是在不改变UI的情况下，对网站进行优化，在扩展的同时保持一致的UI。
  
  对于传统的网站来说重构通常是：
  
  表格(table)布局改为DIV+CSS
  使网站前端兼容于现代浏览器(针对于不合规范的CSS、如对IE6有效的)
  对于移动平台的优化
  针对于SEO进行优化
  深层次的网站重构应该考虑的方面
  
  减少代码间的耦合
  让代码保持弹性
  严格按规范编写代码
  设计可扩展的API
  代替旧有的框架、语言(如VB)
  增强用户体验
  通常来说对于速度的优化也包含在重构中
  
  压缩JS、CSS、image等前端资源(通常是由服务器来解决)
  程序的性能优化(如数据读写)
  采用CDN来加速资源加载
  对于JS DOM的优化
  HTTP服务器的文件缓存
  ```

- 14 列举IE与其他浏览器不一样的特性？

  ```
  1、事件不同之处：
  
      触发事件的元素被认为是目标（target）。而在 IE 中，目标包含在 event 对象的 srcElement 属性；
  
      获取字符代码、如果按键代表一个字符（shift、ctrl、alt除外），IE 的 keyCode 会返回字符代码（Unicode），DOM 中按键的代码和字符是分离的，要获取字符代码，需要使用 charCode 属性；
  
      阻止某个事件的默认行为，IE 中阻止某个事件的默认行为，必须将 returnValue 属性设置为 false，Mozilla 中，需要调用 preventDefault() 方法；
  
      停止事件冒泡，IE 中阻止事件进一步冒泡，需要设置 cancelBubble 为 true，Mozzilla 中，需要调用 stopPropagation()；
  ```

- 15 99%的网站都需要被重构是那本书上写的？

  ```
  网站重构：应用web标准进行设计（第2版）
  ```

- 16 什么叫优雅降级和渐进增强？

  ```
  优雅降级：Web站点在所有新式浏览器中都能正常工作，如果用户使用的是老式浏览器，则代码会针对旧版本的IE进行降级处理了,使之在旧式浏览器上以某种形式降级体验却不至于完全不能用。
  如：border-shadow
  
  渐进增强：从被所有浏览器支持的基本功能开始，逐步地添加那些只有新版本浏览器才支持的功能,向页面增加不影响基础浏览器的额外样式和功能的。当浏览器支持时，它们会自动地呈现出来并发挥作用。
  如：默认使用flash上传，但如果浏览器支持 HTML5 的文件上传功能，则使用HTML5实现更好的体验；
  ```

- 17 是否了解公钥加密和私钥加密。

  ```
  一般情况下是指私钥用于对数据进行签名，公钥用于对签名进行验证;
  HTTP网站在浏览器端用公钥加密敏感数据，然后在服务器端再用私钥解密。
  ```

- 18 WEB应用从服务器主动推送Data到客户端有那些方式？

  ```
  html5提供的Websocket
  不可见的iframe
  WebSocket通过Flash
  XHR长时间连接
  XHR Multipart Streaming
  <script>标签的长时间连接(可跨域)
  ```

- 19 对Node的优点和缺点提出了自己的看法？

  ```
  *（优点）因为Node是基于事件驱动和无阻塞的，所以非常适合处理并发请求，
    因此构建在Node上的代理服务器相比其他技术实现（如Ruby）的服务器表现要好得多。
    此外，与Node代理服务器交互的客户端代码是由javascript语言编写的，
    因此客户端和服务器端都用同一种语言编写，这是非常美妙的事情。
  
  *（缺点）Node是一个相对新的开源项目，所以不太稳定，它总是一直在变，
    而且缺少足够多的第三方库支持。看起来，就像是Ruby/Rails当年的样子。
  ```

- 20 你有用过哪些前端性能优化的方法？

  ```
    （1） 减少http请求次数：CSS Sprites, JS、CSS源码压缩、图片大小控制合适；网页Gzip，CDN托管，data缓存 ，图片服务器。
  
    （2） 前端模板 JS+数据，减少由于HTML标签导致的带宽浪费，前端用变量保存AJAX请求结果，每次操作本地变量，不用请求，减少请求次数
  
    （3） 用innerHTML代替DOM操作，减少DOM操作次数，优化javascript性能。
  
    （4） 当需要设置的样式很多时设置className而不是直接操作style。
  
    （5） 少用全局变量、缓存DOM节点查找的结果。减少IO读取操作。
  
    （6） 避免使用CSS Expression（css表达式)又称Dynamic properties(动态属性)。
  
    （7） 图片预加载，将样式表放在顶部，将脚本放在底部  加上时间戳。
  
    （8） 避免在页面的主体布局中使用table，table要等其中的内容完全下载之后才会显示出来，显示比div+css布局慢。
    对普通的网站有一个统一的思路，就是尽量向前端优化、减少数据库操作、减少磁盘IO。向前端优化指的是，在不影响功能和体验的情况下，能在浏览器执行的不要在服务端执行，能在缓存服务器上直接返回的不要到应用服务器，程序能直接取得的结果不要到外部取得，本机内能取得的数据不要到远程取，内存能取到的不要到磁盘取，缓存中有的不要去数据库查询。减少数据库操作指减少更新次数、缓存结果减少查询次数、将数据库执行的操作尽可能的让你的程序完成（例如join查询），减少磁盘IO指尽量不使用文件系统作为缓存、减少读写文件次数等。程序优化永远要优化慢的部分，换语言是无法“优化”的。
  ```

- 21 http状态码有那些？分别代表是什么意思？

  ```
      简单版
      [
          100  Continue   继续，一般在发送post请求时，已发送了http header之后服务端将返回此信息，表示确认，之后发送具体参数信息
          200  OK         正常返回信息
          201  Created    请求成功并且服务器创建了新的资源
          202  Accepted   服务器已接受请求，但尚未处理
          301  Moved Permanently  请求的网页已永久移动到新位置。
          302 Found       临时性重定向。
          303 See Other   临时性重定向，且总是使用 GET 请求新的 URI。
          304  Not Modified 自从上次请求后，请求的网页未修改过。
  
          400 Bad Request  服务器无法理解请求的格式，客户端不应当尝试再次使用相同的内容发起请求。
          401 Unauthorized 请求未授权。
          403 Forbidden   禁止访问。
          404 Not Found   找不到如何与 URI 相匹配的资源。
  
          500 Internal Server Error  最常见的服务器端错误。
          503 Service Unavailable 服务器端暂时无法处理请求（可能是过载或维护）。
      ]
  
    完整版
    1**(信息类)：表示接收到请求并且继续处理
      100——客户必须继续发出请求
      101——客户要求服务器根据请求转换HTTP协议版本
  
    2**(响应成功)：表示动作被成功接收、理解和接受
      200——表明该请求被成功地完成，所请求的资源发送回客户端
      201——提示知道新文件的URL
      202——接受和处理、但处理未完成
      203——返回信息不确定或不完整
      204——请求收到，但返回信息为空
      205——服务器完成了请求，用户代理必须复位当前已经浏览过的文件
      206——服务器已经完成了部分用户的GET请求
  
    3**(重定向类)：为了完成指定的动作，必须接受进一步处理
      300——请求的资源可在多处得到
      301——本网页被永久性转移到另一个URL
      302——请求的网页被转移到一个新的地址，但客户访问仍继续通过原始URL地址，重定向，新的URL会在response中的Location中返回，浏览器将会使用新的URL发出新的Request。
      303——建议客户访问其他URL或访问方式
      304——自从上次请求后，请求的网页未修改过，服务器返回此响应时，不会返回网页内容，代表上次的文档已经被缓存了，还可以继续使用
      305——请求的资源必须从服务器指定的地址得到
      306——前一版本HTTP中使用的代码，现行版本中不再使用
      307——申明请求的资源临时性删除
  
    4**(客户端错误类)：请求包含错误语法或不能正确执行
      400——客户端请求有语法错误，不能被服务器所理解
      401——请求未经授权，这个状态代码必须和WWW-Authenticate报头域一起使用
      HTTP 401.1 - 未授权：登录失败
      　　HTTP 401.2 - 未授权：服务器配置问题导致登录失败
      　　HTTP 401.3 - ACL 禁止访问资源
      　　HTTP 401.4 - 未授权：授权被筛选器拒绝
      HTTP 401.5 - 未授权：ISAPI 或 CGI 授权失败
      402——保留有效ChargeTo头响应
      403——禁止访问，服务器收到请求，但是拒绝提供服务
      HTTP 403.1 禁止访问：禁止可执行访问
      　　HTTP 403.2 - 禁止访问：禁止读访问
      　　HTTP 403.3 - 禁止访问：禁止写访问
      　　HTTP 403.4 - 禁止访问：要求 SSL
      　　HTTP 403.5 - 禁止访问：要求 SSL 128
      　　HTTP 403.6 - 禁止访问：IP 地址被拒绝
      　　HTTP 403.7 - 禁止访问：要求客户证书
      　　HTTP 403.8 - 禁止访问：禁止站点访问
      　　HTTP 403.9 - 禁止访问：连接的用户过多
      　　HTTP 403.10 - 禁止访问：配置无效
      　　HTTP 403.11 - 禁止访问：密码更改
      　　HTTP 403.12 - 禁止访问：映射器拒绝访问
      　　HTTP 403.13 - 禁止访问：客户证书已被吊销
      　　HTTP 403.15 - 禁止访问：客户访问许可过多
      　　HTTP 403.16 - 禁止访问：客户证书不可信或者无效
      HTTP 403.17 - 禁止访问：客户证书已经到期或者尚未生效
      404——一个404错误表明可连接服务器，但服务器无法取得所请求的网页，请求资源不存在。eg：输入了错误的URL
      405——用户在Request-Line字段定义的方法不允许
      406——根据用户发送的Accept拖，请求资源不可访问
      407——类似401，用户必须首先在代理服务器上得到授权
      408——客户端没有在用户指定的饿时间内完成请求
      409——对当前资源状态，请求不能完成
      410——服务器上不再有此资源且无进一步的参考地址
      411——服务器拒绝用户定义的Content-Length属性请求
      412——一个或多个请求头字段在当前请求中错误
      413——请求的资源大于服务器允许的大小
      414——请求的资源URL长于服务器允许的长度
      415——请求资源不支持请求项目格式
      416——请求中包含Range请求头字段，在当前请求资源范围内没有range指示值，请求也不包含If-Range请求头字段
      417——服务器不满足请求Expect头字段指定的期望值，如果是代理服务器，可能是下一级服务器不能满足请求长。
  
    5**(服务端错误类)：服务器不能正确执行一个正确的请求
      HTTP 500 - 服务器遇到错误，无法完成请求
      　　HTTP 500.100 - 内部服务器错误 - ASP 错误
      　　HTTP 500-11 服务器关闭
      　　HTTP 500-12 应用程序重新启动
      　　HTTP 500-13 - 服务器太忙
      　　HTTP 500-14 - 应用程序无效
      　　HTTP 500-15 - 不允许请求 global.asa
      　　Error 501 - 未实现
    HTTP 502 - 网关错误
    HTTP 503：由于超载或停机维护，服务器目前无法使用，一段时间后可能恢复正常
  ```

- 22 一个页面从输入 URL 到页面加载显示完成，这个过程中都发生了什么？（流程说的越详细越好）

  ```
  2  注：这题胜在区分度高，知识点覆盖广，再不懂的人，也能答出几句，
    而高手可以根据自己擅长的领域自由发挥，从URL规范、HTTP协议、DNS、CDN、数据库查询、
    到浏览器流式解析、CSS规则构建、layout、paint、onload/domready、JS执行、JS API绑定等等；
  
    详细版：
      1、浏览器会开启一个线程来处理这个请求，对 URL 分析判断如果是 http 协议就按照 Web 方式来处理;
      2、调用浏览器内核中的对应方法，比如 WebView 中的 loadUrl 方法;
      3、通过DNS解析获取网址的IP地址，设置 UA 等信息发出第二个GET请求;
      4、进行HTTP协议会话，客户端发送报头(请求报头);
      5、进入到web服务器上的 Web Server，如 Apache、Tomcat、Node.JS 等服务器;
      6、进入部署好的后端应用，如 PHP、Java、JavaScript、Python 等，找到对应的请求处理;
      7、处理结束回馈报头，此处如果浏览器访问过，缓存上有对应资源，会与服务器最后修改时间对比，一致则返回304;
      8、浏览器开始下载html文档(响应报头，状态码200)，同时使用缓存;
      9、文档树建立，根据标记请求所需指定MIME类型的文件（比如css、js）,同时设置了cookie;
      10、页面开始渲染DOM，JS根据DOM API操作DOM,执行事件绑定等，页面显示完成。
  
    简洁版：
      浏览器根据请求的URL交给DNS域名解析，找到真实IP，向服务器发起请求；
      服务器交给后台处理完成后返回数据，浏览器接收文件（HTML、JS、CSS、图象等）；
      浏览器对加载到的资源（HTML、JS、CSS等）进行语法解析，建立相应的内部数据结构（如HTML的DOM）；
      载入解析到的资源文件，渲染页面，完成。
  ```

- 23 部分地区用户反应网站很卡，请问有哪些可能性的原因，以及解决方法？

- 24 从打开app到刷新出内容，整个过程中都发生了什么，如果感觉慢，怎么定位问题，怎么解决?

- 25 除了前端以外还了解什么其它技术么？你最最厉害的技能是什么？

- 26 你用的得心应手用的熟练地编辑器&开发环境是什么样子？

  ```
  Sublime Text 3 + 相关插件编写前端代码
  Google chrome 、Mozilla Firefox浏览器 +firebug 兼容测试和预览页面UI、动画效果和交互功能
  Node.js+Gulp
  git 用于版本控制和Code Review
  ```

- 27 对前端工程师这个职位是怎么样理解的？它的前景会怎么样？

  ```
  前端是最贴近用户的程序员，比后端、数据库、产品经理、运营、安全都近。
  1、实现界面交互
  2、提升用户体验
  3、有了Node.js，前端可以实现服务端的一些事情
  
  
  前端是最贴近用户的程序员，前端的能力就是能让产品从 90分进化到 100 分，甚至更好，
  
  参与项目，快速高质量完成实现效果图，精确到1px；
  
  与团队成员，UI设计，产品经理的沟通；
  
  做好的页面结构，页面重构和用户体验；
  
  处理hack，兼容、写出优美的代码格式；
  
  针对服务器的优化、拥抱最新前端技术。
  ```

- 28 你怎么看待Web App 、hybrid App、Native App？

- 29 你移动端前端开发的理解？（和 Web 前端开发的主要区别是什么？）

- 30 你对加班的看法？

  ```
  加班就像借钱，原则应当是------救急不救穷
  ```

- 31 平时如何管理你的项目？

  ```
  先期团队必须确定好全局样式（globe.css），编码模式(utf-8) 等；
  
  编写习惯必须一致（例如都是采用继承式的写法，单样式都写成一行）；
  
  标注样式编写人，各模块都及时标注（标注关键样式调用的地方）；
  
  页面进行标注（例如 页面 模块 开始和结束）；
  
  CSS跟HTML 分文件夹并行存放，命名都得统一（例如style.css）；
  
  JS 分文件夹存放 命名以该JS功能为准的英文翻译。
  
  图片采用整合的 images.png png8 格式文件使用 尽量整合在一起使用方便将来的管理
  ```

- 32 如何设计突发大规模并发架构？

- 33 当团队人手不足，把功能代码写完已经需要加班的情况下，你会做前端代码的测试吗？

- 34 说说最近最流行的一些东西吧？常去哪些网站？

  ```
      ES6\WebAssembly\Node\MVVM\Web Components\React\React Native\Webpack 组件化
  ```

- 35 知道什么是SEO并且怎么优化么? 知道各种meta data的含义么?

- 36 移动端（Android IOS）怎么做好用户体验?

  ```
  清晰的视觉纵线、
  信息的分组、极致的减法、
  利用选择代替输入、
  标签及文字的排布方式、
  依靠明文确认密码、
  合理的键盘利用
  ```

- 37 简单描述一下你做过的移动APP项目研发流程？

- 38 你在现在的团队处于什么样的角色，起到了什么明显的作用？

- 39 你认为怎样才是全端工程师（Full Stack developer）？

- 40 介绍一个你最得意的作品吧？

- 41 你有自己的技术博客吗，用了哪些技术？

- 42 对前端安全有什么看法？

- 43 是否了解Web注入攻击，说下原理，最常见的两种攻击（XSS 和 CSRF）了解到什么程度？

- 44 项目中遇到国哪些印象深刻的技术难题，具体是什么问题，怎么解决？。

- 45 最近在学什么东西？

- 46 你的优点是什么？缺点是什么？

- 47 如何管理前端团队?

- 48 最近在学什么？能谈谈你未来3，5年给自己的规划吗？
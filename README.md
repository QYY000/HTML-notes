# HTML-notes

### 1.src和href的区别
src和href都是引用外部的资源 

区别:

**src:** 表示对资源的引用。它指向的内容会嵌入到当前标签所在的位置。src会将其指向的资源下载并应用到文档内,如请求js脚本。当浏览器解析到该元素的时候,**会暂停其他资源的下载和处理,直到将该资源加载、编译、执行完毕**,所以一般js脚本会放在页面底部

**href:** 表示超文本引用,它指向一些网络资源,建立当前元素或者是本文档的链接关系。当浏览器识别到它指向的文件的时候就会并行下载,**不会停止会当前文档的处理**。常用在a、link等标签上

### 2.HTML语义化的理解

语义化是指 根据内容的结构化(内容语义化)、选择合适的标签(代码语义化)。通俗来讲就是用正确的标签做正确的事情

#### 优点

* 对机器友好。带有语义的文字表现力丰富,更适合搜索引擎的爬虫爬取信息,有利于SEO。除此之外,还支持读屏软件,根据文章自动生成目录
* 对开发者友好。语义类标签增强了可读性,结构更加清晰下,开发者能清晰的看出网页的结构,便于团队的开发和维护

常见语义化标签:

```
<header></header>  头部

<nav></nav>   导航栏

<section></section>  区块(有语义化的div)

<main></main>  主要区域

<article></article>  主要内容

<aside></aside>  侧边栏

<footer></footer>  底部

```

### 3.DOCTYPE(文档类型的作用)

DOCTYPE是HTML5中一种标准通用标记语言的**文档类型声明**,它的目的是**告诉浏览器(解析器)** 应该以什么样(html或xhtml)的文档类型来定义**解析文档**,不同的渲染模式会影响浏览器第CSS代码甚至是JavaScript脚本的解析,它必须声明在HTML文档的第一行

###### 浏览器渲染页面的两种模式(可以通过document.compatMode获取,比如语雀官网的文档类型是**CSS1Compat**)

* CSS1Compat: **标准模式(Strike mode)** 默认模式,浏览器使用W3C的标准解析渲染页面。在标准模式中,浏览器以其支持的最高标准呈现页面
* BackCompat: **怪异模式(混杂模式)(Quick mode)** 浏览器使用自己的怪异模式解析渲染页面。在怪异模式中,页面以一种比较宽松的向后兼容的方式显示

### 4.script标签中的defer和async的区别

如果没有defer和async属性,浏览器会立即加载并执行相应的脚本。它不会等到后续加载的文档元素,**读取到就会开始加载和执行**,这样就阻塞了后续文档的加载

![image](https://user-images.githubusercontent.com/70131313/138060497-cbae2aa9-9fe9-4af1-9dbe-cb37cbe4d2cd.png)

蓝色代表js脚本网络加载时间, 红色代表js脚本执行时间,绿色代表html解析。

###### defer和async属性都是异步加载外部的js脚本,它们都不会阻塞页面的解析

**区别**

* **执行顺序:** 多个带async属性的标签,不能保证加载的顺序;多个带defer属性的标签,按照加载顺序执行
*  **脚本是否并行执行:**  async属性 ,表示后续文档的加载和执行与js脚本的加载和执行是并行进行的,即异步执行;
*  defer属性,加载后续文档的过程和js脚本的加载时并行进行的(**加载并行**),js脚本需要等到文档所有元素解析完成之后才执行,DOMContentLoaded事件触发执行之前。

### 5.常见的meta标签

meta标签由name和content属性定义,**用来描述网页文档的属性**,比如网页的作者,网页描述,关键词等,除了HTTP标准固定了一些name作为大家使用的共识,开发者还可以自定义name

常用的meta标签:

(1)charset, 用来描述HTML文档的编码类型:

```
<meta charset="UTF-8">
```

(2) keywords, 页面关键词

```
<meta name="keywords" content="关键词" />
```

(3) description, 页面描述

```
<meta name="description" content="页面描述内容" />
```

(4) refresh, 页面重定向和刷新

```
<meta http-equiv="refresh" content="0;url= " />
```

(5)viewport, 适配移动端,可以控制视口的大小和比例

```
<meta name="viewport" content="width = device-width,initial-scale = 1, maximum-scale=1">

其中content的参数有以下几种:

* width viewport: 宽度(数值/device-width)
* height viewport: 高度(数值/device-height)
* initial-scale:初始缩放比例
* maximum-scale:最大缩放比例
* minimum-scale:最小缩放比例
* user-scalable:是否允许用户缩放(yes/no)

```


(6)搜索引擎方式

```
<meta name="robots" content="index,follow" />

其中content参数有以下几种:

*all: 文件将被检索,且页面上的链接可以被查询
*none: 文件将不被检索,且页面上的连接不可以被查询
*index: 文件将被检索
*follow: 页面上的链接可以被查询
*noindex: 文件将不被检索
*nofollow: 页面上的链接不可以被查询

```

### 6.HTML5有哪些更新

**1.语义化标签**

* header: 定义文档的页眉(头部);
* nav:定义导航链接的部分;
* footer:定义文档的页脚(底部);
* article:定义文章内容;
* section: 定义文档中的节(section、区段);
* aside:定义其所处内容之外的内容(侧边)

**2.媒体标签**

(1) audio: 音频
```
<audio src='' controls autoplay loop="true"></audio>

属性:
  *controls控制面板
  *autoplay自动播放
  *loop="true"循环播放
```
(2)video: 视频

```
<video src='' poster='imgs/aa.jpg' controls></video>
属性:
  *poster: 指定视频还没有完全下载完毕,或者用户还没有点击播放前显示的封面。默认显示当前视频文件的第一帧画面,通过poster也可以自己指定
  *controls 控制面板
  *width
  *height
```

(3)source标签
因为对浏览器对视频的格式支持程度不同,为了能够兼容不同的浏览器,可以通过source来指定视频源

```
<video>
  <source src='aa.flv' type='video/flv'></source>
  <source src='aa.mp4' type='video/mp4'></source>
</video>
```

**3.表单**

>**表单类型:**

* email:能够验证当前输入的邮箱地址是否合法
* url: 验证URL
* number: 只能输入数字,其他输入不了,而且自带上下增大减小箭头,max属性可以设置为最大值,min可以设置为最小值,value为默认值
* search:输入框后面会提供一个小叉叉,可以删除输入的内容,更加人性化
* range:可以提供一个范围,其中可以设置max,min以及value,其中value属性可以设置为默认值
* color:颜色拾取器
* time:时分秒
* date:日期选择年月日
* datetime:日期时间(目前只有safari支持)
* datetime-local:日期时间控件
* week: 周控件
* month:月控件

>**表单属性**
* placeholder: 提示信息
* autofocus: 自动获取焦点
* autocomplete="on" 或者autocomplete="off"使用这个属性需要有两个前提
    > * 表单必须提交过
    > * 必须有name属性
* required: 要求输入框不能为空,必须有值才能够提交
* pattern=""  里面写入想要的正则模式,例如手机号patte="^(+86)?"
* multiple: 可以选择多个文件或者多个邮箱
* form="form表单的ID"

>**表单事件**
* oninput 每当input里的输入框内容发生变化都会触发此事件
* onvalid 当验证不通过时触发此事件

**4.进度条、度量器**
* progress标签: 用来表示任务的进度(IE、Safari不支持),max表示任务的进度,value表示已完成多少
* meter属性: 用来显示剩余容量或者剩余库存(IE、Safari不支持)
*  * high/low: 规定被视作高/低的范围
*  * max/min: 规定最大/最小值
*  * value: 规定当前度量
设置规则: min < low < high < max

**5.DOM查询操作**
* document.querySelector()
* document.querySelector()
选择的对象可以是标签,可以是类(需要加点),可以是ID(需要加#)

**6.Web存储**
HTML5提供了两种客户端存储数据的新方法:
  * localStorage 没有时间限制的数据存储
  * sessionStorage 针对一个session的数据存储
  
**7.其他**

* 拖放:  抓取对象以后拖到另外一个位置,设置元素可拖放
```
<img draggle="true" />
```
* 画布(canvas): canvas元素使用JavaScript在网页上绘制图像。画布是一个矩形区域,可以控制每一像素。canvas拥有多种绘制路径,矩形、圆形、字符、以及添加图像的方法
```
<canvas id="myCanvas" width="200" height="100"></canvas>
```
* SVG: SVG指的是可伸缩矢量图形,用于定义网络的基于矢量的图形,使用XML格式定义图形,图象在放大或者改变尺寸的情况下图形质量不会有损失,它是万维网联盟的标准
* 地理定位: Geolocation(地理定位) 用于定位用户的位置

**总结**

（1）新增语义化标签：nav、header、footer、aside、section、article

（2）音频、视频标签：audio、video

（3）数据存储：localStorage、sessionStorage

（4）canvas（画布）、Geolocation（地理定位）、websocket（通信协议）

（5）input 标签新增属性：placeholder、autocomplete、autofocus、required

（6）history API：go、forward、back、pushstate

**移除的元素有**
* 纯表现的元素:basefont,big,center,font,s,strike,tt,u
* 对可用性产生负面影响的元素:frame,frameset,noframes

### 7.img的srcset属性的作用
响应式页面中经常用到根据屏幕密度设置不同的图片。这是用到了img标签的srcset属性。
**srcset属性用于设置不同屏幕密度下,img会自动加载不同的图片。** 用法如下:
```
<img src="image-128.png" srcset="image-256.png 2x" />
此用法可以实现在屏幕密度为1x的情况下加载iamge-128.png,屏幕密度为2x时加载image-256.png
```
按照上面的实现,不同的屏幕密度都要设置图片地址,目前屏幕密度有1x,2x3x,4x四种,如果每一个图片都设置4张图片,加载就会很慢,所以有了新的标准
```
<img src="image-128.png"
     srcset="image-128.png 128w, image-256.png 256w, image-512.png 512w"
     size="(max-width:360px) 340px,128px" />
```
其中srcset指定图片的地址和对应的图片质量。sizes用来设置图片的尺寸零界点。对于srcset中的w单位,可以理解为图片质量。如果可视区域小于这个质量的值,就可以使用,浏览器会自动选择一个最小的可用图片
sizes语法如下:
```
sizes="[media query][length],[media query][length]..."
```








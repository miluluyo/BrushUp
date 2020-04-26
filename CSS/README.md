# CSS3

**目录**

 [1.介绍一下标准的 CSS 的盒子模型？低版本 IE 的盒子模型有什么不同的？](#1)<br />
 [2.什么是响应式设计？响应式设计的基本原理是什么？如何兼容低版本的IE？](#2)<br />
 [3. CSS选择符有哪些？哪些属性可以继承？](#3)<br />
 [4. 浏览器是怎样解析CSS选择器的？](#4)<br />
 [5. CSS优先级算法如何计算？](#5)<br />
 [6. 为什么要初始化CSS样式。](#6)<br />
 [7. CSS3新增伪类有那些？](#7)<br />
 [8. ::before 和 :after中双冒号和单冒号 有什么区别？解释一下这2个伪元素的作用。](#8)<br />

<a name="538MG"></a>
<div id="1"></div>

### 1、介绍一下标准的 CSS 的盒子模型？低版本 IE 的盒子模型有什么不同的？

<a name="LhfD3"></a>

#### 什么是盒子模型？

把所有的网页元素都看成一个盒子，它具有： <br />content，padding，border，margin <br />四个属性，这就是盒子模型。<br /> <br />盒子模型有两种形式：标准盒子模型，怪异盒子模型（IE盒模型）<br /> <br />首先，两种模式可以利用box-sizing属性进行自行选择：<br />　　标准模式：box-sizing:content-box;<br />　　怪异模式：box-sizing:border-box;<br /> <br />两种模式的区别：<br />　　标准模式会被设置的padding撑开，而怪异模式则相当于将盒子的大小固定好，再将内容装入盒子。盒子的大小并不会被padding所撑开。<br /> <br />　　例：<br />
```css
.box{
	box-sizing:border-box; //没有添加时，按照标准模式计算， 添加时按照怪异模式解析
	width:200px;
	height:200px;
	border:2px solid black;
	padding:50px;
	margin:50px;
}
```
 <br />标准模式：盒子总宽度/高度 = 内容区宽度 /高度+padding+border + margin。效果：<br />![](https://cdn.nlark.com/yuque/0/2020/png/709817/1587801920959-13e6df83-3ce5-4e53-a0df-594b35e83128.png#align=left&display=inline&height=170&margin=%5Bobject%20Object%5D&originHeight=170&originWidth=205&size=0&status=done&style=none&width=205)<br />
<br />怪异模式：盒子总宽度/高度 = width/height + margin。效果：<br />![](https://cdn.nlark.com/yuque/0/2020/png/709817/1587801921020-8f730655-8bb0-41cc-afc0-803ff062ccaa.png#align=left&display=inline&height=174&margin=%5Bobject%20Object%5D&originHeight=174&originWidth=202&size=0&status=done&style=none&width=202)<br />
<br />

<a name="bDhTb"></a>
<div id="2"></div>

### 2、什么是响应式设计？响应式设计的基本原理是什么？如何兼容低版本的IE？

响应式设计集百中创建页面的图片排版大小，可以度智能地根据用户行为以及使用的设备问环境（系统答平台、屏幕尺寸、屏幕定向等）进行相对应的布局。<br />

**基本原理：**
通过媒体查询检测不同的设备屏幕尺寸做处理。页面头部必须有meta声明viewport：<br /> `<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no”>`<br />
<br />兼容 IE 需要 JS 进行辅助 <br />

<a name="HMkIq"></a>
<div id="3"></div>

### 3、CSS选择符有哪些？哪些属性可以继承？

**CSS 选择符有哪些？**
1.id选择器（#id）<br />2.类选择器（.class）<br />3.标签选择器（div，h1，p）<br />4.相邻选择器（h1 + p）<br />5.子选择器（ul > li）<br />6.后代选择器（li a）<br />7.通配符选择器（ * ）<br />8.属性选择器（a[title]）<br />9.伪类选择器（a:hover，li:nth-child）<br /> <br />

**可继承的样式**
1.字体系列属性 font，font-family，font-weight，font-size，font-style，font-variant，font-stretch，font-size-adjust<br />2.文本系列属性 text-indent，text-align，line-height，word-spacing，letter-spacing，text-transform，direction，color<br />3.元素可见性 visibility<br />4.表格布局属性 caption-side，border-collapse，border-spacing，empty-cells，table-layout<br />5.列表布局属性 list-style-type，list-style-image，list-style-position，list-style<br />6.生成内容属性 quotes<br />7.光标属性 cursor<br />8.页面样式属性 page，page-break-inside，windows，orphans<br />9.声音样式属性 speak，speak-punctuation，speak-numeral，speak-header，speech-rate，volume，voice-family，pitch，pitch-range，stress，richness，azimuth，elevation<br />

<a name="upf1R"></a>
<div id="4"></div>

### 4、浏览器是怎样解析CSS选择器的？

浏览器会**从右往左**解析css选择器<br />（从右往左的匹配在第一步就排除了大量的不符合条件的最右节点；而从左向右匹配规则的性能都浪费在了失败查找上面）<br />**
<a name="wXWUX"></a>

### 5、CSS优先级算法如何计算？
<div id="5"></div>

1.优先级就近原则，同权重情况下样式定义最近者为准；<br />2.载入样式以最后载入的定位为准；<br />3.!important > id > class > tag；<br />4.important 比 内联优先级高，但内联比id要高；<br />

<a name="1U01j"></a>
<div id="6"></div>

### 6、为什么要初始化CSS样式。

1.浏览器差异<br />不同浏览器对有些标签的默认值是不同的，如果没对css初始化会出现浏览器之间的页面显示差异<br />2.提高编码质量<br />如果不初始化，整个页面做完会很糟糕，重复的css样式很多<br /> <br /> <br />最简单的初始化方法是：（不建议）
```css
* {padding: 0; margin: 0;}
```
 <br />淘宝样式 样式初始化<br /> 
```css
body, h1, h2, h3, h4, h5, h6, hr, p, blockquote, dl, dt, dd, ul, ol, li, pre, form, fieldset, legend, button, input, textarea, th, td { margin:0; padding:0; }
body, button, input, select, textarea { font:12px/1.5tahoma, arial, \5b8b\4f53; }
h1, h2, h3, h4, h5, h6{ font-size:100%; }
address, cite, dfn, em, var { font-style:normal; }
code, kbd, pre, samp { font-family:couriernew, courier, monospace; }
small{ font-size:12px; }
ul, ol { list-style:none; }
a { text-decoration:none; }
a:hover { text-decoration:underline; }
sup { vertical-align:text-top; }
sub{ vertical-align:text-bottom; }
legend { color:#000; }
fieldset, img { border:0; }
button, input, select, textarea { font-size:100%; }
table { border-collapse:collapse; border-spacing:0; }
```
 <br />腾讯QQ官网 样式初始化
```css
body,ol,ul,h1,h2,h3,h4,h5,h6,p,th,td,dl,dd,form,fieldset,legend,input,textarea,select{margin:0;padding:0}
body{font:12px"宋体","Arial Narrow",HELVETICA;background:#fff;-webkit-text-size-adjust:100%;}
a{color:#2d374b;text-decoration:none}
a:hover{color:#cd0200;text-decoration:underline}
em{font-style:normal}
li{list-style:none}
img{border:0;vertical-align:middle}
table{border-collapse:collapse;border-spacing:0}
p{word-wrap:break-word}
```
 <br />新浪官网 样式初始化
```css
body,ul,ol,li,p,h1,h2,h3,h4,h5,h6,form,fieldset,table,td,img,div{margin:0;padding:0;border:0;}
body{background:#fff;color:#333;font-size:12px; margin-top:5px;font-family:"SimSun","宋体","Arial Narrow";}
ul,ol{list-style-type:none;}
select,input,img,select{vertical-align:middle;}
a{text-decoration:none;}
a:link{color:#009;}
a:visited{color:#800080;}
a:hover,a:active,a:focus{color:#c00;text-decoration:underline;}
```
 <br />网易官网 样式初始化
```css
html {overflow-y:scroll;}
body {margin:0; padding:29px00; font:12px"\5B8B\4F53",sans-serif;background:#ffffff;}
div,dl,dt,dd,ul,ol,li,h1,h2,h3,h4,h5,h6,pre,form,fieldset,input,textarea,blockquote,p{padding:0; margin:0;}
table,td,tr,th{font-size:12px;}
li{list-style-type:none;}
img{vertical-align:top;border:0;}
ol,ul {list-style:none;}
h1,h2,h3,h4,h5,h6{font-size:12px; font-weight:normal;}
address,cite,code,em,th {font-weight:normal; font-style:normal;}
```

<a name="LI3tp"></a>
<div id="7"></div>

### 7、CSS3新增伪类有那些？

1)      p:first-of-type  选择属于其父元素的首个 `<p>` 元素的每个 `<p> `元素。<br />
2)      p:last-of-type   选择属于其父元素的最后 `<p>` 元素的每个 `<p>` 元素。<br />
3)      p:only-of-type  选择属于其父元素唯一的 `<p>` 元素的每个 `<p>` 元素。<br />
4)      p:only-child     选择属于其父元素的唯一子元素的每个 `<p>` 元素。<br />
5)      p:nth-child(2)  选择属于其父元素的第二个子元素的每个 `<p>` 元素。<br />
6)      :enabled :disabled 控制表单控件的禁用状态。<br />
7)      :checked         单选框或复选框被选中。<br />

<a name="KTEa1"></a>
<div id="8"></div>

### 8、::before 和 :after中双冒号和单冒号 有什么区别？

**解释一下这2个伪元素的作用**
单冒号（:）用于CSS3伪类<br />双冒号（::）用于CSS3为元素（伪元素由双冒号和伪元素名称组成）<br />CSS3中为了和伪类区分，所以伪元素就是用双冒号来表示了<br />

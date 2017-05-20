---
title: Frameset、Frame、Iframe 区别
date: 2016-11-19 11:52:50
updated: 2016-11-19 11:52:50
tags:
categories: Html
feature:
---

## 一、框架概念

所谓框架便是网页画面分成几个框窗，同时取得多个 URL。只需要 `<FRAMESET> <FRAME>` 即可，而所有框架标记需要放在一个总起的 html 档，这个档案只记录了该框架 如何划分，不会显示任何资料，所以 **不能** 放入 `<BODY>` 标记，浏览这框架必须读取这档 案而不是其它框窗的档案。`<FRAMESET>` 是用以划分框窗，每一框窗由一个 `<FRAME>` 标 记所标示，`<FRAME>` 必须在 `<FRAMESET>` 范围中使用。如下例：

```html   
<frameset cols="50%,*">   
<frame name="a" src="a.html">   
<frame name="b" src="b.html">   
</frameset>
```
此例中  `<FRAMESET>` 把画面分成左右两相等部分，左便是显示 `a.html`，右边则会显示 `b.html` 这档案，`<FRAME>` 标记所标示的框窗永远是按由: 上 ->下->左->右的次序。 


## 二、`<FRAMESET> <FRAME>` 

1. `<FRAMESET>` 称框架标记，用以宣告 HTML 文件为框架模式，并设定视窗如何分割。 `<FRAME>` 则只是设定某一个框窗内的参数属性。
`<FRAMESET>` 参数设定：
```html   
例子：<frameset rows="90,*" frameborder="0" border=0 framespacing="2" bordercolor="#008000">
```

  - COLS="90,*"   
  垂直切割画面(如分左右两个画面)，接受整数值、百分数， * 则代表占用馀下空 间。数值的个数代表分成的视窗数目且以逗号分隔。

  - ROWS="120,*"   
  就是横向切割，将画面上下分开，数值设定同上。唯 COLS 与 ROWS 两参数尽量 不要同在一个  `<FRAMESET>` 标记中，因 Netacape 偶然不能显示这类形的框架，尽 采用多重分割。 

  - frameborder="0"   
  设定框架的边框，其值只有 0 和 1 ， 0 表示不要边框， 1 表示要显示边框。(避 免使用 yes 或 no )

  - border="0"   
  设定框架的边框厚度，以 pixels 为单位。   

  - bordercolor="#008000"   
  设定框架的边框颜色。  

  - framespacing="5"   
  表示框架与框架间的保留空白的距离。

2. `<FRAME>` 参数设定： 
```html  
例子：<frame name="top" src="a.html" marginwidth="5" marginheight="5" scrolling="Auto" frameborder="0" noresize framespacing="6" bordercolor="#0000FF">
```

  - SRC="a.html"   
  设定此框窗中要显示的网页档案名称，每个框窗一定要对应着一个网页档案。你可 使用绝对路径或相对路径。   

  - NAME="top"   
  设定这个框窗的名称，这样才能指定框架来作连结，必须但任意命名。

  - frameborder=0   
  设定框架的边框，其值只有 0 和 1 ， 0 表示不要边框， 1 表示要显示边框。

  - framespacing="6"   
  表示框架与框架间的保留空白的距离。

  - bordercolor="#008000"   
  设定框架的边框颜色。

  - scrolling="Auto"   
  设定是否要显示卷轴，YES 表示要显示卷轴，NO 表示无论如何都不要显示， AUTO 是视情况显示。

  - noresize   
  设定不让使用者可以改变这个框框的大小，亦没有设定此参数，使用者可以很随 意地拉动框架，改变其大小。

  - marginhight=5   
  表示框架高度部份边缘所保留的空间。

  - marginwidth=5   
  表示框架宽度部份边缘所保留的空间。  

  - target
  表示在指定的框架中打开网页
    - blank   它表示在一个新的窗口中打开链接网页
    - top      它表示在本窗口中打开链接网页
    - parent 在上一层的框架中打开链接网页
    - self      在超链接中打开链接网页

3. 例子
```html
//例子 1   
<frameset rows="80,*">   
<frame name="top" src="a.html">   
<frame name="bottom" src="b.html">   
</frameset>     
//例子 2   
<frameset rows="80,*,80">   
<frame name="top" src="a.html">   
<frame name="middle" src="b.html">   
<frame name="bottom" src="c.html">   
</frameset>
//例子 3   
<frameset cols="150,*">   
<frameset rows="80,*">   
<frame name="upper_left" src="a.html">   
<frame name="lower_left" src="b.html">   
</frameset>   
<frame name="right" src="c.html">   
</frameset>
//例子 4   
<frameset rows="80,*">   
<frame name="top" src="a.html">   
<frameset cols="150,*">   
<frame name="lower_left" src="b.html">   
<frame name="lower_right" src="c.html">   
</frameset>   
</frameset>
//例子 5   
<frameset cols="150,*">   
<frame name="left" src="a.html">   
<frameset rows="80,*">   
<frame name="upper_right" src="b.html">   
<frame name="lower_right" src="c.html">   
</frameset>   
</frameset>   
```

## 三、`<NOFRAMES>`

当别人使用的浏览器太旧，不支援框架这个功能时，他看到的将会是一片空白。为了避免 这种情况，可使用 `<NOFRAMES>` 这个标记，当使用者的浏览器看不到框架时，他就会看到 `<NOFRAMES> 与 </NOFRAMES>` 之间的内容，而不是一片空白。   
应用方法：   
```html
<frameset rows="80,*">   

  <noframes>   
  <body>   
  很抱歉，阁下使用的浏览器不支援框架功能，请转用新的浏览器。   
  </body>   
  </noframes> 

  <frame name="top" src="a.html">   
  <frame name="bottom" src="b.html">   
</frameset>
```

若浏览器支援框架，那麽它不会理会 `<noframes>` 中的东西，但若浏览器不支援框架，由 於不认识所有框架标记，不明的标记会被略过，标记包围的东西便被解读出来，所以放在 `<noframes>` 范围内的文字会被显示。 

## 四、 `<IFRAME>`  

这标记作用是在一页网页中间插入一个框窗以显示另一个文件。它是 一个围堵标记，但围着的字句只有在浏览器不支援 iframe 标记时才会显示，如 `<noframes>` 一样，可以放些提醒字句之类。通常 iframe 配合一个辨认浏览器的 JavaScript 会较好，若 JavaScript 认出该浏览器并非 Internet Explorer 便会切换至另一版本。PS：一定要使用 `</iframe>` 关闭，否则后面的内容显示不出来。
```html
<iframe> 的参数设定如下：   
例子： <iframe src="iframe.html" name="test" align="MIDDLE" width="300" height="100" marginwidth="1" marginheight="1" frameborder="1" scrolling="Yes"> </iframe>
```

- src="iframe.html"   
欲显示於此框窗的文件来源除档案名称，必要加上相对或绝对路径。

- name="test"   
此框窗名称，这是连结标记的 target 参数所需要的。

- align="MIDDLE"   
可选值为 left, right, top, middle, bottom，作用不大

- width="300" height="100"   
框窗的宽及长，以 pixels 为单位。

- marginwidth="1" marginheight="1"   
该插入的文件与框边所保留的空间。

- frameborder="1"   
使用 1 表示显示边框， 0 则不显示。（可以是 yes 或 no） 

- scrolling="Yes"   
使用 Yes 表示容许卷动（内定）， No 则不容许卷动


## 五、frame 和 iframe 的区别

1、frame 不能脱离 frameSet 单独使用，iframe 可以；
2、frame 不能放在 **body** 中；如下可以正常显示：

```html
<!--<body>-->  
<frameset rows="50%,*">  
   <frame   name="frame1"  src="a.htm"/>    
   <frame   name="frame2"  src="b.htm"/>    
</frameset>   
<!--<body>-->
```

如下不能正常显示：
```html
<body>  
<frameset rows="50%,*">  
   <frame   name="frame1"   src="a.htm"/>    
   <frame   name="frame2"   src="b.htm"/>    
</frameset>   
<body>
```

3、嵌套在 frameSet 中的 iframe 必需放在 body 中
```html
如下可以正常显示：
  <body>  
    <frameset>    
      <iframe   name="frame1"   src="a.htm"/>    
      <iframe   name="frame2"   src="b.htm"/>    
    </frameset>    
  </body>
```

如下不能正常显示：
```html
  <!--<body>-->  
    <frameset>    
      <iframe   name="frame1" src="a.htm"/>    
      <iframe   name="frame2" src="b.htm"/>    
    </frameset>    
  <!--</body>-->
```

4、不嵌套在 frameSet 中的 iframe 可以随意使用；  
如下均可以正常显示：
```html
<body>  
   <iframe   name="frame1"   src="a.htm"/>    
   <iframe   name="frame2"   src="b.htm"/>    
</body>  
``` 
``html
<!--<body>-->  
   <iframe   name="frame1"   src="a.htm"/>    
   <iframe   name="frame2"   src="b.htm"/>    
<!--</body>-->
```
5、frame 的高度只能通过 frameSet 控制；iframe 可以自己控制，不能通过 frameSet 控制，如：
```html
<!--<body>-->  
<frameset rows="50%,*">  
   <frame   name="frame1"   src="a.htm"/>    
   <frame   name="frame2"   src="b.htm"/>    
</frameset>   
<!--</body>-->  
```
```html
<body>  
<frameset>  
   <iframe height="30%"  name="frame1"    src="a.htm"/>    
   <iframe height="100"  name="frame2"    src="b.htm"/>    
</frameset>   
</body>
```

## 参考
- [frame,iframe,frameset 之间的关系与区别](http://www.xuebuyuan.com/1385439.html)
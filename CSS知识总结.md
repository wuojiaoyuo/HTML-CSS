# css知识总结

## CSS（级联样式表 ，Cascading Style Sheets）	

​	网页上的内容是由HTML构建的，这些元素如何呈现，设计许多方面，如整个页面的`布局`，`元素的位置`、`距离`、`颜色`、`大小`、`是否显示`、`透明度`等。

## CSS语法

### 语法结构

​	一条CSS央视规则由两个组要部分构成：选择器，以`{}` `包裹的一条或多条声名：

<img src="https://wjy-img.oss-cn-beijing.aliyuncs.com/pic_bed/image-20210418220847861.png" title="这条规则表明一级标题都显示蓝色，字体大小为12像素" alt="css语法结构">



> - 选择器是我需要改变样式的对象（上面的规则就一级标题生效）
> - 每条声明由一个属性和一个值组成。（无论是一条声明或多条，都要用`{}`包裹，且声明用`;`分割）
> - 属性（property）是希望设置的样式属性（style attribute）。每个属性有一个值。属性和值被冒号分开。

在如下例所示：

```CSS
/*这是CSS的注释*/
/*建议每条声明占一行*/
p{
	color:red;
	text-align:center;/*文本居中*/
}
```

### 选择器

一个页面上的元素众多，选择器就用于在页面中找到/选择需要应用这个样式的对象。

除我们前示=的元素选择器外，还有`id`和`class`选择器。其中class选择器使用非常普遍。

#### ID选择器

```CSS
/*注意：id选择器前有#号。*/
#sky{
	color:blue;
}
```

这条规则标名，找到页面上的`ID`为`sky`的那个元素让它呈现蓝色，如下所示的页面，**蓝色的天空**则会几个字就将回事蓝色的。

#### class选择器

``` css
/* 注意：class选择器前有 . 号 */
.center{
    text-align:center;
}
.large{
font-size:30px;
}
.red{
    clolor:red;
}
```

以上代码定义了三条会泽，分别应用于页面上对应的元素，如只要页面上缪额元素的`class`为`red`，那么就让他呈现红色。如下所示的页面：

```html
<p class="center">我会居中显示的</p>
<p class="red">我是红色的</p>
<p class="center large red">我又红又大还居中</p>
<p class="red">我也可以是红的</p>
```

#### 分组选择器

在样式表中，许多据用相同样式的元素。为了减小代码，可以使用分组选择器。

``` html
h1 {
    color:green;
}
h2 {
    color:green;
}
p {
    color:green;
}
```
简化如下：

```html
h1,h2,p
{
    color:green;
}
```

#### 嵌套选择器

适用于选择器内部的选择器样式。

下面例子设置四个样式：

+ **`p{ }`**: 为所有 **p** 元素指定一个样式。

+ **`.marked{ }`**: 为所有 **class="marked"** 的元素指定一个样式。

+ **`.marked p{ }`**: 为所有 **class="marked"** 元素内的 **p** 元素指定一个样式。

+ **`p.marked{ }`**: 为所有 **class="marked"** 的 **p** 元素指定一个样式。

  ``` html
  <style>
  p
  {
  	color:blue;
  	text-align:center;
  }
  .marked
  {
  	background-color:red;
  }
  .marked p
  {
  	color:white;
  }
  p.marked{
      text-decoration:underline;
  }
  </style>
  </head>
  
  <body>
  <p>这个段落是蓝色文本，居中对齐。</p>
  <div class="marked">
  <p>这个段落不是蓝色文本。</p>
  </div>
  <p>所有 class="marked"元素内的 p 元素指定一个样式，但有不同的文本颜色。</p>
  	
  <p class="marked">带下划线的 p 段落。</p>
  </body>
  ```

  ![image-20210527095529947](https://wjy-img.oss-cn-beijing.aliyuncs.com/pic_bed/image-20210527095529947.png)

## CSS如何插入样式表（如何生效）

### 外部样式表

当样式需要应用于很多页面时，外部样式表将是理想的选择。在使用外部样式表的情况夏，你可以通过改变一个文件来改变整个站点的外观。每个页面使用`<link>`标签连接到样式表。`<link>` 标签在（文档的）头部：

``` html
<head>
    <link rel="stylesheet" type="text/css" href="mystyle.css">
</head>	
```

浏览器会从文件mycss.css中读到样式声明，并根据它来格式文档。

外部样式表可以在任何文本编辑器中进行编译。文件不能包含任何的html标签。样式表应该以.css扩展名进行保存。

```css
hr {color:sienna;}
p {margin-left:20px;}
body {background-image:url("/imahes.back40.gif");}
/* 不要在属性值与单位之间留空格（如："margin-left:20 px"）,正确的写法应该是"margin-left:20px"*/
```

### 内部样式表

当单个文档需要特殊的样式时，就因该使用内u样式表。你可以使用`<style>` 标签在文档头部定义内部样式表，就像这样：

``` html
<head>
    <stlye>
        hr {color:sienna;}
        p {margin-left:20xp;}
        body {background-image:url("images/back40.gif")}
    </stlye>
</head>
```
**又例如：**

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <!-- 注意下面这个语句，将导入外部的 mycss.css 样式表文件 -->
  <link rel="stylesheet" type="text/css" href="mycss.css">
  <title>页面标题</title>
  <style>
    body {
      background-color: linen;
      text-align: center;
    }
    h1 {
      color: red;
    }
    .haha {
      margin-top: 100px;
      color: chocolate;
      font-size: 50px;
    }
  </style>
</head>
<body>
  <h1>我是有样式的</h1>
  <hr>
  <p class="haha">还是有点丑：)</p>
</body>
</html>
```

### 内联样式

 由于要将表现个内容混杂在一起，内联样式会损失掉样式表许多又是。请慎用这种方法，例如当样式仅需要在一个元素上应用一次时。

要使用内联样式，你需要在相关的标签内使用样式（style）属性。Style属性可以包含任何css属性。

``` html
<p style="color:sienna;margin-left:200px">这是一个段落</p>
```

​	**效果：**

<p style="color:sienna;margin-left:200px">这是一个段落</p>

> **提示：**内联样式是最不灵活的一种方式，完全将内容和样式合在一起，实际应用中非常少见。

### 多重样式

如果某些属性在不同的演示表中被同样的选择器定义，那么属性值经从更具体的样式表中被继承过来。

例如，外部样式表有针对h3选择器的三个属性：

```css
h3{
    color:red;
    text-aling:left;
    font-size:8pt;
}
```

而内部样式表拥有针对还选择器的两个属性：

```css
h3
{
    text-align:right;
    font-size:20pt;
}
```

假如拥有内部样式表的这个页面同时与内部样式表连接，那么h3得到的样式是：

```css
color:red;
text-align:right;
font-size:20pt;
```



### 多重样式优先级

样式表允许以多种方式规定样式信息。样式可以规定在单个的 HTML 元素中，在 HTML 页的头元素中，或在一个外部的 CSS 文件中。甚至可以在同一个 HTML 文档内部引用多个外部样式表。

一般情况下，优先级如下：

**`（内联样式）Inline style` > `（内部样式）Internal style sheet `>`（外部样式）External style sheet `>` 浏览器默认样式`**

```html
<head>
    <!-- 外部样式 style.css -->
    <link rel="stylesheet" type="text/css" href="style.css"/>
    <!-- 设置：h3{color:blue;} -->
    <style type="text/css">
      /* 内部样式 */
      h3{color:green;}
    </style>
</head>
<body>
    <h3>测试！</h3>
</body>
```

## 颜色，尺寸，对齐

### 颜色

颜色在网页中的重要性不言而喻。

我们可以采用颜色名称也可以使用颜色RGB16进制值，来设定前景或背景的颜色。如：

```html
<!-- 颜色名称 -->
<h3 style="background-color:Tomato;">Tomato</h3>
<h3 style="background-color:Orange;">Orange</h3>
<h3 style="background-color:DodgerBlue;">DodgerBlue</h3>
<h3 style="background-color:MediumSeaGreen;">MediumSeaGreen</h3>
<h3 style="background-color:Gray;">Gray</h3>
<h3 style="background-color:SlateBlue;">SlateBlue</h3>
<h3 style="background-color:Violet;">Violet</h3>
<h3 style="background-color:LightGray;">LightGray</h3>
<hr>
<!-- 颜色值，3个字节分别代表RGB（Red，Green，Blue）的0～255的值 -->
<h3 style="background-color:#ff0000;">#ff0000</h3>
<h3 style="background-color:#0000ff;">#0000ff</h3>
<h3 style="background-color:#3cb371;">#3cb371</h3>
<h3 style="background-color:#ee82ee;">#ee82ee</h3>
<h3 style="background-color:#ffa500;">#ffa500</h3>
<h3 style="background-color:#6a5acd;">#6a5acd</h3>
<!-- 文本颜色 -->
<h3 style="color:Tomato;">Hello World</h3>
<p style="color:DodgerBlue;">Lorem ipsum dolor sit, amet consectetur adipisicing elit.</p>
<p style="color:MediumSeaGreen;">Ad facilis est ducimus rem consectetur, corporis omnis, eveniet esse dolor molestiae numquam odio corrupti, sed obcaecati praesentium accusamus? Tempora, dolor a?</p>
```
***效果:***

<h3 style="background-color:Tomato;">Tomato</h3>
<h3 style="background-color:Orange;">Orange</h3>
<h3 style="background-color:DodgerBlue;">DodgerBlue</h3>
<h3 style="background-color:MediumSeaGreen;">MediumSeaGreen</h3>
<h3 style="background-color:Gray;">Gray</h3>
<h3 style="background-color:SlateBlue;">SlateBlue</h3>
<h3 style="background-color:Violet;">Violet</h3>
<h3 style="background-color:LightGray;">LightGray</h3>
<hr>
<!-- 颜色值，3个字节分别代表RGB（Red，Green，Blue）的0～255的值 -->
<h3 style="background-color:#ff0000;">#ff0000</h3>
<h3 style="background-color:#0000ff;">#0000ff</h3>
<h3 style="background-color:#3cb371;">#3cb371</h3>
<h3 style="background-color:#ee82ee;">#ee82ee</h3>
<h3 style="background-color:#ffa500;">#ffa500</h3>
<h3 style="background-color:#6a5acd;">#6a5acd</h3>
<!-- 文本颜色 -->
<h3 style="color:Tomato;">Hello World</h3>
<p style="color:DodgerBlue;">Lorem ipsum dolor sit, amet consectetur adipisicing elit.</p>
<p style="color:MediumSeaGreen;">Ad facilis est ducimus rem consectetur, corporis omnis, eveniet esse dolor molestiae numquam odio corrupti, sed obcaecati praesentium accusamus? Tempora, dolor a?</p>
颜色可以作为一个网站的标志，例如黄色的淘宝，蓝色的twitter等等，颜色也可以作为区分标志来使用。
***相关配色网站：***

<img style="float:right;" title="ColorDrop" src="https://wjy-img.oss-cn-beijing.aliyuncs.com/pic_bed/image-20210520151818777.png" alt="image-20210520151818777" style="zoom: 20%;" />

<a href="[ColorDrop - New colors](https://colordrop.io/)">ColorDrop</a>

<img style="float:right;" title="LOL Corlors"  src="https://wjy-img.oss-cn-beijing.aliyuncs.com/pic_bed/image-20210520151845701.png" alt="image-20210520151845701" style="zoom:20%;" />

<a href="[LOL Colors - Curated color palette inspiration (webdesignrankings.com)](https://www.webdesignrankings.com/resources/lolcolors/)">LOL  Colors</a>

### 尺寸

使用`height`和`width`设定元素内容占据的尺寸。常见的尺寸单位有：像素px，百分比`%`等。

新建如下HTML文件：

```html
<html>
    <head>
        <link rel="stylesheet" href="./mycss.css">
    </head>
</html>
<body>
    <div class="example-1">
        这个元素高 200 pixels， 占据全部高度
    </div>
    <div class="example-2">
        这个元素宽200像素，高300像素
    </div>
</body>
```

再建立对应css文件：

```css
.example-1{
    width:100%;
    height:200px;
    background-color:powderblue;
    text-align:center;
}
.example-2{
    height:100px;
    width:500px;
    background-color:rgb(73,138,60);
    text-align:right;
}
```

运行结果

![image-20210521220316457](https://wjy-img.oss-cn-beijing.aliyuncs.com/pic_bed/image-20210521220316457.png)

### 对齐

对于**元素中得文本**，我们可以简单得设置`text-align`属性为`left,center,right`即可（缺省的是左对齐）

## 盒子模型

### 盒子模型（Box Model）

所有HTML元素可以看作盒子，在CSS中，"box model"这一术语是用来设计和布局时使用。

CSS盒模型本质上是一个盒子，封装周围的HTML元素，从外到内，它包括：**边距`margin`，边框`border`，填充`padding`，和实际内容`content`**。

盒模型允许我们在其它元素和周围元素边框之间的空间放置元素。

**盒子模型（Box Model）如图：**

![img](https://wjy-img.oss-cn-beijing.aliyuncs.com/pic_bed/box-model.gif)

不同部分**说明**：

+ **Margin（外边距）**-清除边框外区域，外边距是透明的。
+ **Border（边框）**-围绕再内边距和内容外的边框。
+ **Padding（内边距）**-清楚内容周围区域，内边距是透明的。
+ **Content（内容）**-盒子的内容，显示图像和文本。

**例子：**

HTML:

```html
<html>
  <head>
    <link rel="stylesheet" href="./mycss.css">
  </head>
  <body>
    <div class="box1">我是内容一，外面红色的是我的边框。注意边框的内外都有25px的距离。</div>
    <div class="box2">我是内容二，外面蓝色的是我的边框。注意与上面元素的外边距，发生了叠加，不是50px而是25px。</div>
  </body>
</html>
```

CSS:

```css
.box1 {
  height: 200px;
  width: 200px;
  background-color:#615200;
  color: aliceblue;
  border: 10px solid red;
  padding: 25px;
  margin: 25px;
}
.box2 {
  height: 300px;
  width: 300px;
  background-color:#004d61;
  color: aliceblue;
  border: 10px solid blue;
  padding: 25px;
  margin: 25px;
}
```

运行结果：

![image-20210521223817030](https://wjy-img.oss-cn-beijing.aliyuncs.com/pic_bed/image-20210521223817030.png)

所以一个元素实际占据的宽度应该是：

(外边距+边框+内边距)*2 + 内容宽度

`width`属性始至元素的宽度时，实际上只设置了其内容宽度。高度也同理

### 边框与边距

#### 边框属性

CSS边框属性允许你指定一个元素的样式和颜色。

```html
<p style="text-align:center; border: 1px solid black;">在四周都有边框</p>
<p style="text-align:center;border-bottom:2px dotted red ;">红色点线底部边框</p>
<p style="text-align:center;border:1px dashed grey;border-radius: 15px;">虚线圆角边框</p>
<p style="text-align:center;background-color:aqua;border-left:5px double blue;">左侧双边框带宽度，颜色为蓝色</p>
```

![image-20210522102849425](https://wjy-img.oss-cn-beijing.aliyuncs.com/pic_bed/image-20210522102849425.png)

> `border: 1px dotted red`属性是border属性的简写，一次对应border-width、border-style、border-color

#### 边框样式

边框样式属性指定要显示什么样的边界。

![image-20210522111931015](https://wjy-img.oss-cn-beijing.aliyuncs.com/pic_bed/image-20210522111931015.png)

#### 边框宽度

可以通过border-width属性指定宽度。

为边框指定宽度有两种方法：可以指定长度值，比如2px或0.1em（单位为px，pt，cm，em等），或使用3个关键字之一，他们分别是thick、medium（默认值）、和thin。

注意：关键字的具体宽度不确定，不一样的用户可以不一样。

```html
      <style>
          p.one
          {
              border-style:solid;
              border-width:5px;
          }
          p.two
          {
              border-style:solid;
              border-width:medium;
          }
          p.three
          {
              border-style:solid;
              border-width:1px;
          }
      </style>
      <p class="one">文本</p>
      <p class="two">文本</p>
      <p class="three">文本</p>
```



结果：

![image-20210527091113994](https://wjy-img.oss-cn-beijing.aliyuncs.com/pic_bed/image-20210527091113994.png)te

#### 边框颜色

border-color属性用于设置边框颜色。可以通过 name（指定颜色的名称）、RGB（指定RGB值）、HEX（指定16进制值）。

#### 内边框单独设置各边

```html
padding: 20px; /* 上下左右都相同 */
padding-top: 20px;
padding-bottom: 100px;
padding-right: 50px;
padding-left: 80px;
padding: 25px 50px 75px 100px; /* 简写形式，按上，右，下，左顺序设置 */
padding: 25px 10px; /* 简写形式，上下为25px，左右为10px */
```

结果：

![image-20210527093049219](https://wjy-img.oss-cn-beijing.aliyuncs.com/pic_bed/image-20210527093049219.png)

<a href="https://www.runoob.com/css/css-border.html">其他盒子元素参考信息</a>

![image-20210527094242553](https://wjy-img.oss-cn-beijing.aliyuncs.com/pic_bed/image-20210527094242553.png)

## 定位

`position`属性用于对元素进行定位。该属性有一下一些值：

+ static 静态
+ relative 相对
+ fixed 固定
+ absolute 绝对

设置了元素的`position`属性后，我们才能使用`top,bottom,left,right`属性，否则定位无效。

### static

设置静态定位`position:static；`，这是元素的默认定位方式，也即你设置是否元素都将按照正常的页面布局进行。

即，按照元素再HTML出现的先后顺序重上倒下，从左到右进行元素的安排。

### relative 

设置为相对定位`position:relative；`，这将把元素相对于它的静态（正常）位置进行偏移

### fixed

设置为固定定位`positiong:fixed；`，这将是的元素固定不动（即使你上下左右拖动滚动条）。

此时元素固定的位置任由`top,bottom,left,right`属性确定，但是相对的是视角（viewport，就是浏览器屏幕可见区域）

### absolute

设置为绝对定位`position:absolute;`，将使元素相对**与其最近设置了定位属性（非static）的父元素**进行偏移。

如果该元素的所有父元素都没有设置定位属性，那么就相对于`<body>`这个父元素。

> 注意： 绝对定位此处可能有些混淆，请留意其任是相对的，不过是相对**最近的父元素**

## 溢出

当元素内容超过其只当的区域是，我们通过溢出`oerflow`属性来处理这些溢出的部分。

溢出属性由一下几个值：

+ visible 默认值，溢出部分不被裁剪，在区域外面显示
+ hidden 裁剪溢出部分且不可见
+ scroll 裁剪溢出部分，但提供上下和左右滚动条供显示
+ auto 裁剪溢出部分，视情况提供滚动条

## 浮动



在一个区域或容器内，我们可以设置**float**属性让某些元素水平方向上向右或者向左西东，其周围的元素也会重新排列。我们疮痈这种样式来时图文进行合理布局。

![image-20210614215746350](https://wjy-img.oss-cn-beijing.aliyuncs.com/pic_bed/image-20210614215746350.png)

一个浮动元素会尽量向右或向左移动，知道他的边缘碰到包含框或宁一个浮动框位置。

浮动元素之后元素将围绕它。

一个元素浮动后，其他的元素尽可能包围它，或者说出现载这个浮动元素的左或右方。

如果希望浮动元素后面的元素载其下方显示，可使用`clear:both`样式来进行清除。

## 不透明度

我们可以用`opacity`对任何元素（不过常用于图片）设置不透明度。

值在`[0.0-1.0]`之间，值越低，透明度越高，如下图分别是无opacity属性，opacity分别为 0.9，0.6，0.3

![image-20210614222949359](https://wjy-img.oss-cn-beijing.aliyuncs.com/pic_bed/image-20210614222949359.png)


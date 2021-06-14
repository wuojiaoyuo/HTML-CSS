# HTML基础知识总结

##  HTML (Hyper Text Markup Language,超文本标记语言)

> “超文本”（hypertext）是指连接单个网站内或多个网站的连接。

**HTML**定义的网站的内容的含义和结构，**HTML**不是编程语言，而是一种**定义内容结构的标记语言**，其文件后缀为 **`.html`**

## 一个完整的HTML元素

```HTML
<p>这是一个标签</p>
```

1. 开始标签（Opening tag）表示元素从这里开始；
2. 结束标签（Closing tag）表示着元素结束；
3. 内容（Content）元素的内容；
4. 元素（Element）开始标签、结束标签与内容标签相结合，便是一个完整的元素；

## HTML文档结构与相关说明

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <link rel="shortcut icon" href="favicon.ico" type="image/x-icon">
  <title>页面标题</title>
</head>
<body>
  <h1>我的第一个Web页</h1>
  <p>当前有点丑：)</p>
</body>
</html>
```

### 基本结构

- **&lt;!DOCTYPE html>**：声明文档类型。可有可无。
- **&lt;html></html&gt;**:html**根元素**，包裹整个完整的页面，**其他的元素都镶嵌到其中**。

- **&lt;head></head&gt;**：头部，用于描述网页的一些相关信息，比如网页的配置，设置，关键字等等...这些信息不会在浏览器希纳是，但是对网页解析十分重要。

- **&lt;meta charset="utf-8"&gt;**:meta标签，用于描述网页的各种信息，其中&lt;meta charset="utf-8"/>设置网页的编码为UTF-8格式。

   **补充**：

   > ```html
   > 	<meta name="keywords" content="html,网页开发">
   > ```
   >
   > ​	设置**网页关键字**，有助于搜素引擎的搜索。
   > ​     	
   > ​	name="keywords"表示这个meta标签设置的是网页的关键字，
   > ​     	
   > ​	content=""表示关键字的详细信息，多个关键字，用英文逗号分隔；
   > ​     	
   >
   > ```html
   > 	<meta name="description" content="这是第一个网页！">
   > ```
   >
   > ​	设置**网页的描述信息**，搜索引擎搜索时，标题下面的一段文字【非常重要}
   > ​     	
   > ​	name="description"表示这个meta标签设置的是网页的描述信息；
   > ​     	
   > ​	content=""表示描述信息的详细内容

- **&lt;link>**：连接网页的小图标，rel 表示当前link的作用，是连接网页图标；href 表示图标的地址何处。
- **&lt;title></title&gt;**:网页的标题，显示在浏览器选项卡上的文字。
- **&lt;body></body&gt;**;包含能看到的所有内容。
- **&lt;!-- 注释内容 -->**：**注释**，中间为注释内容。

## HTML中的元素

### 元素的属性

  元素是可以又相关属性的，包含一些额外的信息，但是不会在浏览器中显示出来。

  ```html
  <!-- 带属性的段落输入框 -->
  <p title="这是个title属性">鼠标移上来试试！</p>
  <!-- 带属性的输入框 -->
  <input type="text">
  <input type="password">
  ```

  一个元素必须有：

  1. 一个空格，在属性和元素名称间，多个属性间也是空格隔开
  2. 属性名称，后面耕者一个等号。
  3. 一个属性值，有一堆引号（" "）引起来。

### 空元素

一般来说，元素都拥有开始标签、内容、结束标签。但有一些元素只有开始标签，通常用来在次元素所在位置插入/嵌入一些东西，如&lt;br>,&lt;hr>,&lt;input>,&lt;img>等等。我们称其为空元素。

  ```html
  <!-- 换行 -->
  <p>我可以<br>换行</p>
  <!-- 水平分割线 -->
  <hr>
  <!-- 输入框 -->
  <input>
  ```

### 标题

在页面中，标题非常重要：

1. 搜索引擎用标题来索引页面的内容
2. 用户也习惯以标题进行主要内容浏览，以决定是否查看该页面

  ```html
  <h1>一级标题</h1>
  <h2>二级标题</h2>
  <h3>三级标题</h3>
  <h4>四级标题</h4>
  <h5>五级标题</h5>
  <h6>六级标题</h6>
  ```

### 图片

  ```html
<img src="图片路径" width="宽度" height="高度" title="鼠标悬停提示文字" alt="图像无法显示时候的替代文字" />
  ```

对于小尺寸的图片可以才用`base64`编码进行，可以提高页面加载速度。

| 例子                                | 解释                                 |
| :---------------------------------- | :----------------------------------- |
| &lt;img src="picture.jpg">          | 该图片文件与当前文档在同一目录中     |
| &lt;img src="./images/picture.jpg"> | 该图片文件在当前目录下的images目录中 |
| &lt;img src="../picture.jpg">       | 该图片文件在上一级目录中             |

图片的存储大小对网页的加载有影响，可以在不明显改变图片质量的情况下压缩图片。

### 超链接

仍和东西都可以加上超链接，通常是文本，图片；

```html
<a href="要跳转的地址" target="_self/_blank">内容</a>
```

target的属性时 _self时表示在当前页面打开；_blank则时在新的页面打开。

  ### 文本格式中的元素

``` html 
<p>You can use the mark tag to <mark>highlight</mark> text.</p>
<p><del>This line of text is meant to be treated as deleted text.</del></p>
<p><s>This line of text is meant to be treated as no longer accurate.</s></p>
<p><ins>This line of text is meant to be treated as an addition to the document.</ins></p>
<p><u>This line of text will render as underlined</u></p>
<p><small>This line of text is meant to be treated as fine print.</small></p>
<p><strong>This line rendered as bold text.</strong></p>
<p><em>This line rendered as italicized text.</em></p>
```
显示结果如下：
<p>You can use the mark tag to <mark>highlight</mark> text.</p>
<p><del>This line of text is meant to be treated as deleted text.</del></p>
<p><s>This line of text is meant to be treated as no longer accurate.</s></p>
<p><ins>This line of text is meant to be treated as an addition to the document.</ins></p>
<p><u>This line of text will render as underlined</u></p>
<p><small>This line of text is meant to be treated as fine print.</small></p>
<p><strong>This line rendered as bold text.</strong></p>
<p><em>This line rendered as italicized text.</em></p>

### 列表List

**无序列表**

```html
<!-- square，circle，，，-->
<ul type="square">
    <li> Coffee </li>
    <li> Tea </li>
    <li> Milk </li>
</ul>
```

`<ul>`，无序列表，默认使用**实心圆点**作为没想的标志，其他的标志可以是空心圆`circle`，实心方块`square`以及不出现标签。

**有序列表**

```html
<ol>
    <li>Coffee</li>
    <li>Tea</li>
    <li>Milk</li>
</ol>
```

有许列表使用`<ol>`标签，默认是用**数字**作为每项标志，其他的标志可以是大写字母`A`，小写字母`a`，罗马字母`i`等

```html
<ol type="a">
    <li> 内容</li>
</ol>
```



### 表格Table

表格使用的是`<table>`标签，用`<tr>`表示行，`<td>`表示行中的单元，`<th>`表示表头的单元（**加粗显示**）

```html
<table>
    <tr>
        <th align="center">Name</th>
        <th align="center">age</th>
    </tr>
    <tr>
        <td align="center">Zhang sam</td>
        <td align="center">22</td>
    </tr>
    <tr>
        <td align="center">Li sir</td>
        <td align="center">21</td>
    </tr>
</table>
```
> *align*属性规定对其方式

效果如下-

<table>
    <tr>
        <th align="center">Name</th>
        <th align="center">age</th>
    </tr>
    <tr>
        <td align="center">Zhang sam</td>
        <td align="center">22</td>
    </tr>
    <tr>
        <td align="center">Li sir</td>
        <td align="center">21</td>
    </tr>
</table>

### 表单Form

当网站需要获取我们的一些信息如：用户名、密码、选择买什么、买多少、提出意见等等时，我们就需要使用表单（form）来让用户填写或选择。

```html
<form>
  <!-- 文本框，注意有 placeholder 提示符 -->
  用户名：<br>
  <input type="text" name="name" placeholder="请输入用户名"><br>
  <!-- 密码框 -->
  密码：<br>
  <input type="password" name="ps" placeholder="请输入密码"><br>
  年龄：<br>
  <!-- 数字输入框，注意 min 和 value 属性-->
  <input type="number" name="age" min="18" value="18"><br>
  <!-- 单选按钮, 注意 checked 属性 -->
  性别：<br>
  <input type="radio" name="gender" value="male" checked> 男<br>
  <input type="radio" name="gender" value="female"> 女<br>
  <input type="radio" name="gender" value="other"> 其它<br>
  <!-- 下拉列表，注意 selected 属性 -->
  党派：<br>
  <select name="party">
    <option value="D">民主党</option>
    <option value="R" selected>共和党</option>
    <option value="N">无党派</option>
  </select><br>
  <!-- 多选框 -->
  您有哪些交通工具：<br>
  <input type="checkbox" name="vehicle1" value="Bike"> 自行车<br>
  <input type="checkbox" name="vehicle2" value="Motocycle" checked> 摩托车<br>
  <input type="checkbox" name="vehicle3" value="Car"> 轿车<br>
  <input type="checkbox" name="vehicle4" value="Jet"> 飞机<br>
  <!-- 日期选择器 -->
  您的工作日期：<br>
  <input type="date"><br>
  <!-- 文件选择器 -->
  上传您的照片:<br>
  <input type="file" name="photo"><br>
  <!-- 文本输入区域，注意 rows 和 cols 属性 -->
  您的建议：<br>
  <textarea name="message" rows="5" cols="30">
    The cat was playing in the garden.
  </textarea><br><hr>
  <!-- 表单提交/重置按钮，将表单中的数据取消或传输给服务器端进行处理 -->
  <input type="submit" value="提 交">
  <input type="reset" value="重 置">
</form>
```

> **提示：** 当提交时，表单中没有`name`属性的元素将不会提交，比如上面工作日期的选择器。有`name`属性的元素其`value`的值将提交给服务器。

### 其他

<a href="https://www.w3cschool.cn/htmltags/">更多HTML内容</a>
## 第一章 html&CSS

### 1. 网页的组成部分

- 页面由三部分内容组成！分别是内容（结构）、表现、行为。
  - 内容（结构），是我们在页面中可以看到的数据。我们称之为内容。一般内容 我们使用 html 技术来展示。
  - 表现，指的是这些内容在页面上的展示形式。比如说。布局，颜色，大小等等。一般使用CSS 技术实现
  - 行为，指的是页面中元素与输入设备交互的响应。一般使用javascript 技术实现

### 2. HTML 简介

- Hyper Text Markup Language （超文本标记语言）	简写：HTML
- HTML 通过标签来标记要显示的网页中的各个部分。网页文件本身是一种文本文件，通过在文本文件中添加标记符，可以告诉浏览器如何显示其中的内容（如：文字如何处理，画面如何安排，图片如何显示等）

### 3. HTML 文件的书写规范

```html
<html>	表示整个 html 页面的开始
	<head>	头信息
		<title>标题</title>	标题
	</head>
	<body>	body 是页面的主体内容
        页面主体内容
	</body>
</html>	表示整个 html 页面的结束

Html 的代码注释	<!-- 这是 html 注释，可以在页面右键查看源代码中看到 -->
```



### 4. HTML 标签介绍

1. 标签的格式:
   	<标签名>封装的数据</标签名>
2. 标签名大小写不敏感。
3. 标签拥有自己的属性。
   - 分为基本属性：bgcolor="red"	 可以修改简单的样式效果
   - 事件属性： onclick="alert('你好！');"	可以直接设置事件响应后的代码。
4. 标签又分为，单标签和双标签。
   - 单标签格式：	<标签名 />	br 换行	hr 水平线
   - 双标签格式: <标签名> ...封装的数据...</标签名>

5. 标签的语法：

   ```html
   <!-- ①标签不能交叉嵌套 -->
   正确：<div><span>早安，尚硅谷</span></div>
   错误：<div><span>早安，尚硅谷</div></span>
   <hr />
   
   <!-- ②标签必须正确关闭 -->
   <!-- i.有文本内容的标签： -->
   
   正确：<div>早安，尚硅谷</div> 
   错误：<div>早安，尚硅谷
   <hr />
   
   <!-- ii.没有文本内容的标签： -->
   正确：<br />
   错误：<br>
   <hr />
   
   <!-- ③属性必须有值，属性值必须加引号 -->
   正确：<font color="blue">早安，尚硅谷</font> 
   错误：<font color=blue>早安，尚硅谷</font> 
   错误：<font color>早安，尚硅谷</font>
   <hr />
   
   <!-- ④注释不能嵌套 -->
   正确：<!-- 注释内容 --> <br/>
   错误：<!--	<!-- 这是错误的 html 注释	-->	-->
   <hr />
   
   注意事项：
   html 代码不是很严谨。有时候标签不闭合，也不会报错。
   ```



### 5. 常用标签介绍 

#### 1. font 字体标签

```html
<body>
    <!-- 字体标签
    需求1：在网页上显示我是字体标签，并修改字体为宋体，颜色为红色。

    font 标签是字体标签,它可以用来修改文本的字体,颜色,大小(尺寸) 
	color 属性 修改颜色
    face 属性 修改字体
    size 属性 修改文本大小
    -->
	<font color="red" face="宋体" size="7">我是字体标签</font>
</body>
```



#### 2. 特殊字符

- 特殊字符表：

  ![image-20211023193533450](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211023193533450.png)

  ![image-20211023193526474](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211023193526474.png)

#### 3. 标题标签

```html
<body>
    <!-- 标题标签
    需求1：演示标题1 到标题6 的

    h1 - h6 都是标题标签
    	h1 最大
    	h6 最小
    	align 属性是对齐属性
    		left	左对齐(默认)
    		center	剧中
    		right	右对齐
    -->
    <h1 align="left">标题 1</h1>
    <h2 align="center">标题 2</h2>
    <h3 align="right">标题 3</h3>
    <h4>标题 4</h4>
    <h5>标题 5</h5>
    <h6>标题 6</h6>
</body>
```



#### 4. 超链接 （ *重 点 ，必 须 掌 握 * ）

```html
<body>
    <!-- a 标签是 超链接
        href 属性设置连接的地址
        target 属性设置哪个目标进行跳转
            _self	表示当前页面(默认值)
            _blank	表示打开新页面来进行跳转
    -->
	<a href="http://localhost:8080">百度</a><br/>
	<a href="http://localhost:8080" target="_self">百度_self</a><br/>
	<a href="http://localhost:8080" target="_blank">百度_blank</a><br/>
</body>
```



#### 5. 列表标签

```html
<body>
    <!--需求1：使用无序，列表方式，把东北F4，赵四，刘能，小沈阳，宋小宝，展示出来              
        ul 是无序列表
    		type 属性可以修改列表项前面的符号
    	li 是列表项
    -->
    <ul type="none">
        <li>赵四</li>
        <li>刘能</li>
        <li>小沈阳</li>
        <li>宋小宝</li>
    </ul>
</body>
```



#### 6. img 标签

```html
<body>
    <!--需求1：使用img 标签显示一张美女的照片。并修改宽高，和边框属性

    img  标签是图片标签,用来显示图片
		src 属性可以设置图片的路径
		width 属性设置图片的宽度
		height 属性设置图片的高度
		border 属性设置图片边框大小
    	alt 属性设置当指定路径找不到图片时,用来代替显示的文本内容

    在JavaSE 中路径也分为相对路径和绝对路径.
    相对路径:从工程名开始算
    绝对路径:盘符:/目录/文件名

    在web 中路径分为相对路径和绝对路径两种
    相对路径:
        .	表示当前文件所在的目录
        ..	表示当前文件所在的上一级目录
    	文件名	表示当前文件所在目录的文件,相当于 ./文件名      ./ 可以省略
    绝对路径:
    正确格式是: http://ip:port/工程名/资源路径
    错误格式是: 盘符:/目录/文件名
    -->
    <img src="1.jpg" width="200" height="260" border="1" alt="美女找不到"/>
    <img src="../2.jpg" width="200" height="260" />
    <img src="../imgs/3.jpg" width="200" height="260" />
    <img src="../imgs/4.jpg" width="200" height="260" />
    <img src="../imgs/5.jpg" width="200" height="260" />
    <img src="../imgs/6.jpg" width="200" height="260" />
</body>
```



#### 7. 表格标签（ * 重点，必须掌握 * ）

```html
<body>
<!--
	需求 1：做一个 带表头的 ，三行，三列的表格，并显示边框 
	需求 2：修改表格的宽度，高度，表格的对齐方式，单元格间距。

		table 标签是表格标签 
		border 设置表格标签 
		width 设置表格宽度 
		height 设置表格高度 
		align 设置表格相对于页面的对齐方式
		cellspacing 设置单元格间距

	tr 是行标签 
	th 是表头标签 
	td 是单元格标签 
		align 设置单元格文本对齐方式
	b 是加粗标签 
--> 
<table align="center" border="1" width="300" height="300" cellspacing="0">
    <tr>
        <th>1.1</th> 
        <th>1.2</th> 
        <th>1.3</th>
    </tr> 
    <tr>
        <td>2.1</td>
        <td>2.2</td> 
        <td>2.3</td> 
    </tr> 
    <tr>
        <td>3.1</td> 
        <td>3.2</td> 
        <td>3.3</td> 
    </tr> 
    </table>
</body>
```



#### 8. 跨行跨列表格 （次重点，必须掌握）

```html
<body>
<!--	需求 1：
	新建一个五行，五列的表格，
	第一行，第一列的单元格要跨两列， 第二行第一列的单元格跨两行，
	第四行第四列的单元格跨两行两列。

	colspan 属性设置跨列
	rowspan 属性设置跨行
-->

    <table width="500" height="500" cellspacing="0" border="1">
    <tr>
        <td colspan="2">1.1</td>
        <td>1.3</td>
        <td>1.4</td>
        <td>1.5</td>
    </tr>
    <tr>
        <td rowspan="2">2.1</td>
        <td>2.2</td>
        <td>2.3</td>
        <td>2.4</td>
        <td>2.5</td>
    </tr>
    <tr>
        <td>3.2</td>
        <td>3.3</td>
        <td>3.4</td>
        <td>3.5</td>
    </tr>
    <tr>
        <td>4.1</td>
        <td>4.2</td>
        <td>4.3</td>
        <td colspan="2" rowspan="2">4.4</td>
    </tr>
    <tr>
        <td>5.1</td>
        <td>5.2</td>
        <td>5.3</td>
    </tr>
    </table>
</body>
```



#### 9. 了解 iframe 框架标签 (内嵌窗口)

```html
<body>
	我是一个单独的完整的页面<br/><br/>
	<!--ifarme 标签可以在页面上开辟一个小区域显示一个单独的页面
		ifarme 和a 标签组合使用的步骤:
			1在 iframe 标签中使用 name 属性定义一个名称
			2在 a 标签的 target 属性上设置iframe 的 name 的属性值
	-->
	<iframe src="3.标题标签.html" width="500" height="400" name="abc"></iframe>
<br/>

    <ul>
        <li><a href="0-标签语法.html" target="abc">0-标签语法.html</a></li>
        <li><a href="1.font 标签.html" target="abc">1.font 标签.html</a></li>
        <li><a href="2.特殊字符.html" target="abc">2.特殊字符.html</a></li>
    </ul>
</body>   
```



#### 10. 表单标签 （ * 重点 ，必须掌握 * ）

```html
<body> 
    <!--需求 1:创建一个个人信息注册的表单界面。包含用户名，密码，确认密码。性别（单选），兴趣爱好（多选），国籍（下拉列表）。 隐藏域，自我评价（多行文本域）。重置，提交。--> 
    <!--
        form 标签就是表单 
        input type=text 是文件输入框 value 设置默认显示内容 		  input type=password 是密码输入框 value 设置默认显示内容 
		input type=radio 是单选框 name 属性可以对其进行分组 checked="checked"表示默认选中
		input type=checkbox 是复选框 checked="checked"表示默认选中
		input type=reset 是重置按钮 value 属性修改按钮上的文本
		input type=submit 是提交按钮 value 属性修改按钮上的文本
		input type=button 是按钮  value 属性修改按钮上的文本		   input type=file 是文件上传域
		input type=hidden	是隐藏域	当我们要发送某些信息，而这些信息，不需要用户参与，就可以使用隐藏域（提交的时候同时发送给服务器）

		select 标签是下拉列表框
		option 标签是下拉列表框中的选项 selected="selected"设置默认选中

		textarea 表示多行文本输入框 （起始标签和结束标签中的内容是默认值）
			rows 属性设置可以显示几行的高度
			cols 属性设置每行可以显示几个字符宽度
	-->
	<form>
		用户名称：<input type="text" value="默认值"/><br/> 		   用户密码：<input type="password" value="abc"/><br/> 
        确认密码：<input type="password" value="abc"/><br/>

        性别：<input type="radio" name="sex"/>男<input type="radio" name="sex" checked="checked" />女<br/>

        兴趣爱好：<input type="checkbox" checked="checked" />Java<input type="checkbox" />JavaScript<input type="checkbox" />C++<br/>

        国籍：<select>

        	<option>--请选择国籍--</option>
		<option selected="selected">中国</option>
		<option>美国</option>
		<option>小日本</option>
		</select><br/>
		自我评价：<textarea rows="10" cols="20">我才是默认值</textarea><br/>
		<input type="reset" value="abc" />
		<input type="submit"/>
	</form>
</body>
```

- 表单格式化:

  ```html
  <form>
  	<h1 align="center">用户注册</h1>
  	<table align="center">
  		<tr>
  			<td> 用户名称：</td>
  			<td>
  				<input type="text" value="默认值"/>
  			</td>
  		</tr>
  		<tr>
      		<td> 用户密码：</td>
      		<td><input type="password" value="abc"/></td>
      	</tr>
      	<tr>
      		<td>确认密码：</td>
      		<td><input type="password" value="abc"/></td>
      	</tr>
          <tr>
          	<td>性别：</td>
              <td>
                  <input type="radio" name="sex"/>男
                  <input type="radio" name="sex" checked="checked" />女
              </td>
          </tr>
          <tr>
              <td> 兴趣爱好：</td>
              <td>
                  <input type="checkbox" checked="checked" />Java
                  <input type="checkbox" />JavaScript
                  <input type="checkbox" />C++
              </td>
          </tr>
          <tr>
              <td>国籍：</td>
              <td>
                  <select>
                  <option>--请选择国籍--</option>
                  <option selected="selected">中国</option>
                  <option>美国</option>
                  <option>小日本</option>
                  </select>
              </td>
          </tr>
          <tr>
              <td>自我评价：</td>
              <td><textarea rows="10" cols="20">我才是默认值</textarea></td>
          </tr>
          <tr>
              <td><input type="reset" /></td>
              <td align="center"><input type="submit"/></td>
          </tr>
  	</table>
  </form>
  </body>
  ```

- 表单提交细节

  ```html
  <body>
  	<!--
  		form 标签是表单标签
  			action 属性设置提交的服务器地址
  			method 属性设置提交的方式 GET(默认值)或 POST
  
  		表单提交的时候，数据没有发送给服务器的三种情况：
  			1、表单项没有 name 属性值
  			2、单选、复选（下拉列表中的 option 标签）都需要添加 value 属性，以便发送给服务器
  			3、表单项不在提交的 form 标签中
  
  		GET 请求的特点是：
  			1、浏览器地址栏中的地址是：action 属性[+?+请求参数] 请求参数的格式是：name=value&name=value
  			2、不安全
  			3、它有数据长度的限制
  
          POST 请求的特点是：
              1、浏览器地址栏中只有 action 属性值
              2、相对于 GET 请求要安全
              3、理论上没有数据长度的限制
  -->
  
  
  
  	<form action="http://localhost:8080" method="post">
  		<input type="hidden" name="action" value="login" />
  		<h1 align="center">用户注册</h1>
  		<table align="center">
              <tr>
              	<td> 用户名称：</td>
              	<td>
              		<input type="text" name="username" value="默认值"/>
              	</td>
              </tr>
              <tr>
              	<td> 用户密码：</td>
              	<td><input type="password" name="password" value="abc"/></td>
              </tr>
              <tr>
              	<td>性别：</td>
              	<td>
              		<input type="radio" name="sex" value="boy"/>男
              		<input type="radio" name="sex" checked="checked" value="girl" />女
              	</td>
              </tr>
              <tr>
              	<td> 兴趣爱好：</td>
              	<td>
                  	<input name="hobby" type="checkbox" checked="checked" value="java"/>Java
              		<input name="hobby" type="checkbox" value="js"/>JavaScript
              		<input name="hobby" type="checkbox" value="cpp"/>C++
              	</td>
              </tr>
              <tr>
              	<td>国籍：</td>
              	<td>
              		<select name="country">
              			<option value="none">--请选择国籍--</option>
              			<option value="cn" selected="selected">中国</option>
              			<option value="usa">美国</option>
              			<option value="jp">小日本</option>
              		</select>
              	</td>
              </tr>
              <tr>
              	<td>自我评价：</td>
              	<td><textarea name="desc" rows="10" cols="20">我才是默认值</textarea></td>
              </tr>
              <tr>
              	<td><input type="reset" /></td>
              	<td align="center"><input type="submit"/></td>
              </tr>
  		</table>
  	</form>
  </body>
  ```

#### 11. 其他标签

```html
<body> 
    <!--需求 1：div、span、p 标签的演示 
		div 标签 默认独占一行 
		span 标签 它的长度是封装数据的长度
		p 段落标签 默认会在段落的上方或下方各空出一行来（如果已有就不再空） 
	--> 
    <div>div 标签 1</div> 
    <div>div 标签 2</div> 
    <span>span 标签 1</span> 
    <span>span 标签 2</span> 
    <p>p 段落标签 1</p> 
    <p>p 段落标签 2</p>
</body>
```



### 6. **CSS** 技术

- CSS 是「层叠样式表单」。是用于(增强)控制网页样式并允许将样式信息与网页内容分离的一种标记性语言。

- CSS 语法规则：

  - 选择器：浏览器根据“选择器”决定受 CSS 样式影响的 HTML 元素（标签）。 

  - 属性 (property) 是你要改变的样式名，并且每个属性都有一个值。属性和值被冒号分开，并 由花括号包围，这样就组成了一个完整的样式声明（declaration），例如：p {color: blue} 

  - 多个声明：如果要定义不止一个声明，则需要用分号将每个声明分开。虽然最后一条声明的 最后可以不加分号(但尽量在每条声明的末尾都加上分号) 

    例如：p{ 

    ​				color:red;

    ​				font-size:30px; 

    ​			}

    注：一般每行只描述一个属性 

    CSS 注释：/\*注释内容\*/

- CSS 和 HTML 的结合方式

  1. **在标签的 style 属性上设置”key:value value;”，修改标签样式。**

     ```html
     <!DOCTYPE html>
     <html lang="en">
     <head>
         <meta charset="UTF-8">
         <title>Title</title>
     </head>
     <body>
         <!--需求 1：分别定义两个 div、span 标签，分别修改每个 div 标签的样式为：边框 1 个像素，实线，红色。-->
         <div style="border: 1px solid red;">div 标签 1</div>
         <div style="border: 1px solid red;">div 标签 2</div>
         <span style="border: 1px solid red;">span 标签 1</span>
         <span style="border: 1px solid red;">span 标签 2</span>
     </body>
     </html>
     ```

     **这种方式的缺点？** 

     1.如果标签多了。样式多了。代码量非常庞大。 

     2.可读性非常差。 

     3.CSS 代码没什么复用性可方言。

  2. **在 head 标签中，使用 style 标签来定义各种自己需要的 css 样式。** 

     **格式如下：** 

     ​	**xxx {**

     ​		**Key : value value;** 

     ​	**}**

     ```html
     <!DOCTYPE html>
     <html lang="en">
     <head>
         <meta charset="UTF-8">
         <title>Title</title>
         <!--style 标签专门用来定义 css 样式代码-->
         <style type="text/css">
     /* 需求 1：分别定义两个 div、span 标签，分别修改每个 div 标签的样式为：边框 1 个像素，实线，红色。*/
             div{
             	border: 1px solid red;
             }
             span{
             	border: 1px solid red;
             }
     	</style>
     </head>
     
     <body>
         <div>div 标签 1</div>
         <div>div 标签 2</div>
     
         <span>span 标签 1</span>
         <span>span 标签 2</span>
     </body>
     </html>
     ```

     **这种方式的缺点:**

     1.只能在同一页面内复用代码，不能在多个页面中复用 css 代码。 

     2.维护起来不方便，实际的项目中会有成千上万的页面，要到每个页面中去修改。工作量太大了。

  3. **把 css 样式写成一个单独的 css 文件，再通过 link 标签引入即可复用。 **

     **使用 html 的 \<link rel="stylesheet" type="text/css" href="./styles.css" /> 标签  导入 css 样 式文件。**

### 7. CSS选择器

1. **标签名选择器**

   标签名选择器的格式是： 

   ​	标签名{ 

   ​		属性：值; 

   ​	}

   标签名选择器，可以决定哪些标签被动的使用这个样式。

2. **id** **选择器**

   id 选择器的格式是： 

   ​	\#id 属性值{ 

   ​		属性：值; 

   ​	}

   id 选择器，可以让我们通过 id 属性选择性的去使用这个样式。

3. **class** **选择器（类选择器）**

   class 类型选择器的格式是： 

   ​	**.**class 属性值{ 

   ​		属性：值; 

   ​	} 

   class 类型选择器，可以通过 class 属性有效的选择性地去使用这个样式。

4. **组合选择器**

   组合选择器的格式是： 

   ​	选择器 1，选择器 2，选择器 n{ 

   ​		属性：值; 

   ​	} 

   组合选择器可以让多个选择器共用同一个 css 样式代码。



## 第二章 JavaScript

### 1.介绍

- Javascript 语言诞生主要是完成页面的数据验证。因此它运行在客户端，需要运行浏览器来解析执行 JavaScript 代码。 

  JS 是 Netscape 网景公司的产品，最早取名为 LiveScript;为了吸引更多 java 程序员。更名为 JavaScript。 

  JS 是弱类型，Java 是强类型。 

  特点： 

  1. 交互性（它可以做的就是信息的动态交互） 

  2. 安全性（不允许直接访问本地硬盘） 

  3. 跨平台性（只要是可以解释 JS 的浏览器都可以执行，和平台无关）

### 2. **JavaScript** **和** **html** **代码的结合方式**

1. 只需要在 head 标签中，或者在 body 标签中， 使用 script 标签 来书写 JavaScript 代码

   ```html
   <!DOCTYPE html> 
   <html lang="en">
       <head> 
           <meta  charset="UTF-8">
           <title>Title</title> 
           <script type="text/javascript"> 
               // alert 是 JavaScript 语言提供的一个警告框函数。 
               // 它可以接收任意类型的参数，这个参数就是警告框的提示信息 
               alert("hello javaScript!"); 
           </script> 
       </head> 
       <body> 
       </body> 
   </html>
   ```

2. 使用 script 标签引入 单独的 JavaScript 代码文件

   ```html
   <!DOCTYPE html> 
   <html lang="en"> 
       <head> 
           <meta charset="UTF-8"> 
           <title>Title</title> 
           <!--
   			现在需要使用 script 引入外部的 js 文件来执行 				src 属性专门用来引入 js 文件路径（可以是相对路径，也可以是绝对路径） 
   			 script 标签可以用来定义 js 代码，也可以用来引入 js 文件 但是，两个功能二选一使用。不能同时使用两个功能 
   		--> 
           <script type="text/javascript" src="1.js">
           </script> 
           <script type="text/javascript">
               alert("国哥现在可以帅了"); 
           </script> 
       </head>
       <body> 
       </body> 
   </html>
   ```



### 3. 变量

- 什么是变量？变量是可以存放某些值的内存的命名。 

- JavaScript 的变量类型： 

  数值类型： number 

  字符串类型： string 

  对象类型： object 

  布尔类型： boolean 

  函数类型： function 

- JavaScript 里特殊的值： 

  undefined  未定义，所有 js 变量未赋于初始值的时候，默认值都是 undefined. 

  null   空值 

  NaN  全称是：Not a Number。非数字。非数值。 

- JS 中的定义变量格式： 

  var 变量名; 

  var 变量名 = 值;

### 4. **关系（比较）运算**

- 等于： ==  等于是简单的做字面值的比较 
- 全等于： ===   除了做字面值的比较之外，还会比较两个变量的数据类型

### 5. **逻辑运算**

- 且运算： && 

  或运算： || 

  取反运算： ! 

- 在 JavaScript 语言中，所有的变量，都可以做为一个 boolean 类型的变量去使用。 

  ​	0 、null、 undefined、””(空串) 都认为是 false； 

- && 且运算。 

  有两种情况： 

  ​	第一种：当表达式全为真的时候。返回最后一个表达式的值。 

  ​	第二种：当表达式中，有一个为假的时候。返回第一个为假的表达式的值 

- || 或运算 

  ​	第一种情况：当表达式全为假时，返回最后一个表达式的值 

  ​	第二种情况：只要有一个表达式为真。就会返回第一个为真的表达式的值 

- 并且 && 与运算 和 ||或运算 有短路。 

  ​	短路就是说，当这个&&或||运算有结果了之后 。后面的表达式不再执行 。

### 7. 数组（重点）

- JS 中 数组的定义： 

  ​	格式： 

  ​	var 数组名 = [];  						// 空数组 

  ​	var 数组名 = [1 , ’abc’ , true];   // 定义数组同时赋值元素

  ```html
  <!DOCTYPE html> 
  <html lang="en"> 
      <head> 
          <meta charset="UTF-8"> 
          <title>Title</title> 
          <script type="text/javascript"> 
              var arr = [true,1]; 
              // alert( arr.length ); // 2 
              arr[0] = 12; 
              // alert( arr[0] );//12 
              // javaScript 语言中的数组，只要我们通过数组下标赋值，那么最大的下标值，就会自动的给数组做扩容操作。 
              arr[3] = "abc"; 
              alert(arr.length); //4 
              // alert(arr[2]);// undefined 
              // 数组的遍历 
              for (var i = 0; i < arr.length; i++){ 
                  alert(arr[i]); 
              }
          </script>
      </head>
      <body>  
      </body>
  </html>
  ```

### 8. 函数（重点）

- **函数的二种定义方式**

  **第一种，可以使用** **function** **关键字来定义函数。** 

  使用的格式如下: 

  ​		function 函数名(形参列表){ 

  ​				函数体 

  ​		}

  在 JavaScript 语言中，如何定义带有返回值的函数？ 

  只需要在函数体内直接使用 return 语句返回值即可！

  ```html
  <!DOCTYPE html> 
  <html lang="en"> 
      <head> <meta charset="UTF-8"> 
          <title>Title</title> 
          <script type="text/javascript"> 
              // 定义一个无参函数 
              function fun(){ 
                  alert("无参函数 fun()被调用了"); 
              }
              // 函数调用===才会执行 
              // fun(); 
              function fun2(a ,b) { 
                  alert("有参函数 fun2()被调用了 a=>" + a + ",b=>"+b); }
              // fun2(12,"abc"); 
              // 定义带有返回值的函数
  
              function sum(num1,num2) { 
                  var result = num1 + num2;
                  return result; 
              }
              alert( sum(100,50) ); 
          </script>
      </head>
      <body> 
      </body> 
  </html>
  ```

  **函数的第二种定义方式，格式如下：**

  使用格式如下： 

  var 函数名 = function(形参列表)  { 函数体 }

  

  **注：在 Java 中函数允许重载。但是在 JS 中函数的重载会直接覆盖掉上一次的定义**

- **函数的** **arguments** **隐形参数（只在** **function** **函数内）**

  就是在 function 函数中不需要定义，但却可以直接用来获取所有参数的变量。我们管它叫隐形参数。 

  隐形参数特别像 java 基础的可变长参数一样。 

  public void fun( Object ... args ); 

  可变长参数其实是一个数组。 

  那么 js 中的隐形参数也跟 java 的可变长参数一样。操作类似数组。

  ```html
  <!DOCTYPE html> 
  <html lang="en"> 
      <head> 
          <meta charset="UTF-8">
          <title>Title</title> 
          <script type="text/javascript"> 
              function fun(a) { 
                  alert( arguments.length );//可看参数个数 
                  alert( arguments[0] ); 
                  alert( arguments[1] ); 
                  alert( arguments[2] ); 
                  alert("a = " + a); 
                  for (var i = 0; i < arguments.length; i++){ 
                      alert( arguments[i] ); 
                  }
                  alert("无参函数 fun()"); 
              }
              // fun(1,"ad",true);
              // 需求：要求 编写 一个函数。用于计算所有参数相加的和并返回 
              function sum(num1,num2) { 
                  var result = 0; 
                  for (var i = 0; i < arguments.length; i++) {
                      if (typeof(arguments[i]) == "number") { 
                          result += arguments[i]; 
                      } 
                  }
                  return result; 
              }
              alert( sum(1,2,3,4,"abc",5,6,7,8,9) ); 
          </script> 
      </head>
      <body> 
      </body>
  </html>
  ```

### 9. **JS** 中的自定义对象（扩展内容）

1. **Object** **形式的自定义对象**

   - 对象的定义： 

     ​	var 变量名 = new Object();  // 对象实例（空对象） 

     ​	变量名.属性名 = 值;  // 定义一个属性 

     ​	变量名.函数名 = function(){}  // 定义一个函数 

   - 对象的访问： 

     ​	变量名.属性 / 函数名();

   ```html
   <!DOCTYPE html> 
   <html lang="en">
       <head> 
           <meta charset="UTF-8"> 
           <title>Title</title> 
           <script type="text/javascript">
               // 对象的定义： 
               // var 变量名 = new Object(); // 对象实例（空对象） 
               // 变量名.属性名 = 值; // 定义一个属性 
               // 变量名.函数名 = function(){} // 定义一个函数 
               var obj = new Object(); 
               obj.name = "华仔"; 
               obj.age = 18; 
               obj.fun = function () { alert("姓名：" + this.name + " , 年龄：" + this.age); }
               // 对象的访问： 
               // 变量名.属性 / 函数名(); 
               // alert( obj.age ); 
               obj.fun(); 
           </script> 
       </head> 
       <body>
       </body>
   </html>
   ```

2. **{}花括号形式的自定义对象**

   - 对象的定义： 

     ​	var 变量名 = {   // 空对象 

     ​		属性名：值,   // 定义一个属性 

     ​		属性名：值,   // 定义一个属性 

     ​		函数名：function(){}  // 定义一个函数 

     ​	}; 

   - 对象的访问： 

     ​		变量名.属性 / 函数名();

   ```html
   <!DOCTYPE html> 
   <html lang="en"> 
       <head> <meta charset="UTF-8"> 
           <title>Title</title>
           <script type="text/javascript">
               // 对象的定义： 
               // var 变量名 = { // 空对象 
               // 属性名：值, // 定义一个属性 
               // 属性名：值, // 定义一个属性 
               // 函数名：function(){} // 定义一个函数 
               // }; 
               var obj = { 
                   name:"国哥", 
                   age:18, 
                   fun : function () { alert("姓名：" + this.name + " , 年龄：" + this.age);
                                     } 
               };
               // 对象的访问： 
               // 变量名.属性 / 函数名(); 
               alert(obj.name); 
               obj.fun(); 
           </script> 
       </head> 
       <body>
       </body>
   </html>
   ```

### 10. **js** **中的事件** （重点）

- 什么是事件？事件是电脑输入设备与页面进行交互的响应。我们称之为事件。 

- **常用的事件：** 

onload 加载完成事件： 

​	页面加载完成之后，常用于做页面 js 代码初始化操作 

onclick 单击事件： 

​	常用于按钮的点击响应操作。 

onblur 失去焦点事件： 

​	常用用于输入框失去焦点后验证其输入内容是否合法。 

onchange 内容发生改变事件： 

​	常用于下拉列表和输入框内容发生改变后操作 

onsubmit 表单提交事件： 

​	常用于表单提交前，验证所有表单项是否合法。 

- **事件的注册又分为静态注册和动态注册两种：** 

什么是事件的注册（绑定）？ 

​	其实就是告诉浏览器，当事件响应后要执行哪些操作代码，叫事件注册或事件绑定。 

**静态注册事件**：通过 html 标签的事件属性直接赋于事件响应后的代码，这种方式我们叫静态注册。 

**动态注册事件**：是指先通过 js 代码得到标签的 dom 对象，然后再通过 dom 对象.事件名 = function(){} 这种形式赋于事件响应后的代码，叫动态注册。 

​	动态注册基本步骤： 

​		1、获取标签对象 

​		2、标签对象.事件名 = fucntion(){}

- **onload** **加载完成事件**

  ```html
  <!DOCTYPE html> 
  <html lang="en"> 
      <head> <meta charset="UTF-8"> 
          <title>Title</title>
          <script type="text/javascript"> 
              // onload 事件的方法 
              function onloadFun() { 
                  alert('静态注册 onload 事件，所有代码'); 
              }
  
              // onload 事件动态注册。是固定写法 
              window.onload = function () { 
                  alert("动态注册的 onload 事件"); 
              } 
          </script> 
      </head> 
      <!--静态注册 onload 事件 
  		onload 事件是浏览器解析完页面之后就会自动触发的事件 		  <body onload="onloadFun();"> 
  	--> 
      <body>
      </body>
  </html>
  ```

- **onclick** **单击事件**

  ```html
  <!DOCTYPE html> 
  <html lang="en"> 
      <head> <meta charset="UTF-8"> 
          <title>Title</title> 
          <script type="text/javascript"> 
              function onclickFun() { 
                  alert("静态注册 onclick 事件"); 
              }
              // 动态注册 onclick 事件 
              window.onload = function () { 
                  // 1 获取标签对象 
                  /*
                  * document 是 JavaScript 语言提供的一个对象（文档）<br/> 
                  * get 获取 
                  * Element 元素（就是标签） 
                  * By 通过。。 由。。经。。。 
                  * Id id 属性 
                  *
                  * getElementById 通过 id 属性获取标签对象 
                  **/ 
                  var btnObj = 
      			document.getElementById("btn01"); 
                  // alert( btnObj ); 
                  // 2 通过标签对象.事件名 = function(){} 
                  btnObj.onclick = function () { 
                      alert("动态注册的 onclick 事件"); 
                  } 
              }
  
          </script> 
      </head> 
      <body> 
          <!--静态注册 onClick 事件--> 
          <button onclick="onclickFun();">按钮 1</button> 
          <button id="btn01">按钮 2</button> 
      </body> 
  </html>
  ```

- **onblur** **失去焦点事件**

  ```html
  <!DOCTYPE html> 
  <html lang="en"> 
      <head> <meta charset="UTF-8"> 
          <title>Title</title> 
          <script type="text/javascript"> 
              // 静态注册失去焦点事件 
              function onblurFun() { 
                  // console 是控制台对象，是由 JavaScript 语言提供，专门用来向浏览器的控制器打印输出， 用于测试使用 
                  // log() 是打印的方法 
                  console.log("静态注册失去焦点事件"); 
              }
              // 动态注册 onblur 事件
              window.onload = function () {
                  //1 获取标签对象 
                  var passwordObj = 
                  document.getElementById("password"); 
                  // alert(passwordObj); 
                  //2 通过标签对象.事件名 = function(){}; 
                  passwordObj.onblur = function () { 
                      console.log("动态注册失去焦点事件"); 
                  } 
              } 
          </script> 
      </head> 
      <body> 
          用户名:<input type="text" onblur="onblurFun();"><br/> 
          密码:<input id="password" type="text" ><br/> 
      </body> 
  </html>
  ```

- **onchange** **内容发生改变事件**

  ```html
  <!DOCTYPE html> 
  <html lang="en"> 
      <head> <meta charset="UTF-8"> 
          <title>Title</title> 
          <script type="text/javascript"> 
              function onchangeFun() { 
                  alert("女神已经改变了");
              }
              window.onload = function () { 
                  //1 获取标签对象 
                  var selObj =                                 			document.getElementById("sel01"); 
                  // alert( selObj );
                  //2 通过标签对象.事件名 = function(){} 
                  selObj.onchange = function () { 
                      alert("男神已经改变了"); 
                  } 
              } 
          </script> 
      </head> 
      <body> 
          请选择你心中的女神： 
          <!--静态注册 onchange 事件--> 
          <select onchange="onchangeFun();"> 
              <option>--女神--</option> 
              <option>芳芳</option>
              <option>佳佳</option>
              <option>娘娘</option> 
          </select> 
          请选择你心中的男神： 
          <select id="sel01">
              <option>--男神--</option>
              <option>国哥</option> 
              <option>华仔</option>
              <option>富城</option> 
          </select>
      </body> 
  </html>
  ```

- **onsubmit** **表单提交事件**

  ```html
  <!DOCTYPE html> 
  <html lang="en">
      <head> 
          <meta charset="UTF-8"> 
          <title>Title</title> 
          <script type="text/javascript" > 
              // 静态注册表单提交事务 
              function onsubmitFun(){ 
                  // 要验证所有表单项是否合法，如果，有一个不合法就阻止表单提交 
                  alert("静态注册表单提交事件----发现不合法"); 
                  return flase; 
              }
              
              window.onload = function () { 
                  //1 获取标签对象 
                  var formObj = 				
                    document.getElementById("form01"); 
                  //2 通过标签对象.事件名 = function(){} 
                  formObj.onsubmit = function () { 
                      // 要验证所有表单项是否合法，如果，有一个不合法就阻止表单提交 
                      alert("动态注册表单提交事件----发现不合法"); 
                      return false; 
                  } 
              } 
          </script> 
      </head> 
      <body> 
          <!--return false 可以阻止 表单提交 --> 
          <form action="http://localhost:8080" method="get" onsubmit="return onsubmitFun();"> 
              <input type="submit" value="静态注册"/> 
          </form> 
          
          <form action="http://localhost:8080" id="form01"> 
              <input type="submit" value="动态注册"/> 
          </form> 
      </body> 
  </html>
  ```

### 11. DOM 模型（重点）

DOM 全称是 Document Object Model 文档对象模型 

大白话，就是把文档中的标签，属性，文本，转换成为对象来管理。 

那么 它们是如何实现把标签，属性，文本转换成为对象来管理呢。这就是我们马上要学习的重点。

#### 1. **Document** **对象（重点）**

![image-20211024165555364](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211024165555364.png)

**Document** **对象的理解：** 

**第一点：Document它管理了所有的 HTML 文档内容。**

**第二点：document 它是一种树结构的文档。有层级关系。**

**第三点：它让我们把所有的标签 都 对象化** 

**第四点：我们可以通过 document 访问所有的标签对象。**



#### 2. **Document** **对象中的方法介绍**

- **document.getElementById(elementId)** 

  通过标签的 id 属性查找标签 dom 对象，elementId 是标签的 id 属性值 

- **document.getElementsByName(elementName)** 

  通过标签的 name 属性查找标签 dom 对象，elementName 标签的 name 属性值 

- **document.getElementsByTagName(tagname)** 

  通过标签名查找标签 dom 对象。tagname 是标签名 

- **document.createElement( tagName)** 

  方法，通过给定的标签名，创建一个标签对象。tagName 是要创建的标签名

**注：**

document 对象的三个查询方法，如果有 id 属性，优先使用 **getElementById** 方法来进行查询 

如果没有 id 属性，则优先使用 **getElementsByName** 方法来进行查询 

如果 id 属性和 name 属性都没有最后再按标签名查 **getElementsByTagName** 

以上三个方法，一定要在页面加载完成之后执行，才能查询到标签对象。

- **getElementById** **方法示例代码：**

  ```html
  <!DOCTYPE html>
  <html lang="en"> 
      <head> <meta charset="UTF-8"> 
          <title>Title</title> 
          <script type="text/javascript" > 
              /** 需求：当用户点击了较验按钮，要获取输出框中的内容。然后验证其是否合法。<br/> 
              * 验证的规则是：必须由字母，数字。下划线组成。并且长度是 5 到 12 位。 
              * */ 
              function onclickFun() { 
                  // 1 当我们要操作一个标签的时候，一定要先获取这个标签对象。 
                  var usernameObj = 		                  			document.getElementById("username"); 
                  // [object HTMLInputElement] 它就是 dom 对象 
                  var usernameText = usernameObj.value; 
                  // 如何 验证 字符串，符合某个规则 ，需要使用正则表达式技术 
                  var patt = /^\w{5,12}$/; 
                  /*
                  * test()方法用于测试某个字符串，是不是匹配我的规则  
                  * 匹配就返回 true。不匹配就返回 false. 
                  * */ 
                  var usernameSpanObj = document.getElementById("usernameSpan"); 
                  // innerHTML 表示起始标签和结束标签中的内容 
                  // innerHTML 这个属性可读，可写 
                  usernameSpanObj.innerHTML = "国哥真可爱！"; 
                  if (patt.test(usernameText)) { 
                      // alert("用户名合法！"); 
                      // usernameSpanObj.innerHTML = "用户名合法！"; 
                      usernameSpanObj.innerHTML = "<img src=\"right.png\" width=\"18\" height=\"18\">"; 
                  } else { 
                      // alert("用户名不合法！"); 
                      // usernameSpanObj.innerHTML = "用户名不合法！"; 
                      usernameSpanObj.innerHTML = "<img src=\"wrong.png\" width=\"18\" height=\"18\">"; 
                  } 
              } 
          </script>
      </head> 
      <body>
          用户名：<input type="text" id="username" value="wzg"/> 
          <span id="usernameSpan" style="color:red;"> 
          </span> 
          <button onclick="onclickFun()">较验</button>
  
      </body>
  </html>
  ```

- **getElementsByName** **方法示例代码：**

  ```html
  <!DOCTYPE html> 
  <html lang="en"> 
      <head> <meta charset="UTF-8"> 
          <title>Title</title> 
          <script type="text/javascript"> 
              // 全选 
              function checkAll() { 
                  // 让所有复选框都选中 
                  // document.getElementsByName();是根据 指定的 name 属性查询返回多个标签对象集合 
                  // 这个集合的操作跟数组 一样 
                  // 集合中每个元素都是 dom 对象 
                  // 这个集合中的元素顺序是他们在 html 页面中从上到下的顺序 
                  var hobbies = document.getElementsByName("hobby"); 
                  // checked 表示复选框的选中状态。如果选中是 true，不选中是 false 
                  // checked 这个属性可读，可写 
                  for (var i = 0; i < hobbies.length; i++){ 
                      hobbies[i].checked = true; 
                  } 
              }
              //全不选 
              function checkNo() { 
                  var hobbies = document.getElementsByName("hobby"); 
                  // checked 表示复选框的选中状态。如果选中是 true，不选中是 false 
                  // checked 这个属性可读，可写 
                  for (var i = 0; i < hobbies.length; i++){ 
                      hobbies[i].checked = false; 
                  } 
              }
              // 反选 
              function checkReverse() { 
                  var hobbies = document.getElementsByName("hobby"); 
                  for (var i = 0; i < hobbies.length; i++) { 
                      hobbies[i].checked = !hobbies[i].checked; 
                      // if (hobbies[i].checked) { 
                      // hobbies[i].checked = false; 
                      // }else { 
                      // hobbies[i].checked = true; 
                      // }
  
                  } 
              } 
          </script> 
      </head> 
      <body> 
          兴趣爱好： 
          <input type="checkbox" name="hobby" value="cpp" checked="checked">C++ 
          <input type="checkbox" name="hobby" value="java">Java 
          <input type="checkbox" name="hobby" value="js">JavaScript 
          <br/> 
          <button onclick="checkAll()">全选</button> 
          <button onclick="checkNo()">全不选</button> 
          <button onclick="checkReverse()">反选</button> 
      </body> 
  </html>
  ```

- **getElementsByTagName** **方法示例代码：**

  ```html
  <!DOCTYPE html> 
  <html lang="en"> 
      <head> <meta charset="UTF-8"> 
          <title>Title</title>
          <script type="text/javascript"> 
              // 全选 
              function checkAll() {                          	  //document.getElementsByTagName("input"); 
                  // 是按照指定标签名来进行查询并返回集合 
                  // 这个集合的操作跟数组 一样
                  // 集合中都是 dom 对象 
                  // 集合中元素顺序 是他们在 html 页面中从上到下的顺序。 
                  var inputs = document.getElementsByTagName("input"); 
                  for (var i = 0; i < inputs.length; i++){ 
                      inputs[i].checked = true; 
                  } 
              }
          </script>
      </head> 
      <body>
          兴趣爱好：
          <input type="checkbox" value="cpp" checked="checked">C++ 
          <input type="checkbox" value="java">Java 
          <input type="checkbox" value="js">JavaScript
  
          <br/> 
          <button onclick="checkAll()">全选</button> 
      </body>
  </html>
  ```

- **createElement** **方法示例代码：**

  ```html
  <!DOCTYPE html> 
  <html lang="en">
      <head> <meta charset="UTF-8"> 
          <title>Title</title> 
          <script type="text/javascript"> 
              window.onload = function () { 
                  // 现在需要我们使用 js 代码来创建 html 标签，并显示在页面上 
                  // 标签的内容就是：<div>国哥，我爱你</div> 
                  var divObj = document.createElement("div"); // 在内存中 <div></div> 
                  var textNodeObj = document.createTextNode("国哥，我爱你"); // 有一个文本节点对象 #国哥，我 爱你 
                  divObj.appendChild(textNodeObj); // <div>国哥，我爱你</div> 
                  // divObj.innerHTML = "国哥，我爱你"; // <div>国哥，我爱你</div>,但，还只是在内存中 
                  // 添加子元素 
                  document.body.appendChild(divObj); 
              } 
          </script> 
      </head> 
      <body>
      </body> 
  </html>
  ```

#### 3. **节点的常用属性和方法**

- 节点就是标签对象

  - **方法：** 

    通过具体的元素节点调用 getElementsByTagName() 方法，获取当前节点的指定标签名孩子节点 

    appendChild( oChildNode ) 方法，可以添加一个子节点，oChildNode 是要添加的孩子节点

  - **属性：** 

    childNodes 属性，获取当前节点的所有子节点 

    firstChild 属性，获取当前节点的第一个子节点 

    lastChild 属性，获取当前节点的最后一个子节点 

    parentNode 属性，获取当前节点的父节点 

    nextSibling 属性，获取当前节点的下一个节点 

    previousSibling 属性，获取当前节点的上一个节点 

    className 用于获取或设置标签的 class 属性值 

    innerHTML 属性，表示获取/设置起始标签和结束标签中的内容 

    innerText 属性，表示获取/设置起始标签和结束标签中的文本

  - **.DOM** **查询练习**

  ```html
  <!DOCTYPE html> 
  <html> 
      <head>
          <meta charset="UTF-8"> 
          <title>dom 查询</title> 
          <link rel="stylesheet" type="text/css" href="style/css.css" /> 
          <script type="text/javascript"> 
              window.onload = function(){ 
                  //1.查找#bj 节点                
                  document.getElementById("btn01").onclick = function () { 
                      var bjObj = document.getElementById("bj"); 
                      alert(bjObj.innerHTML); }
          
                  //2.查找所有 li 节点 
                  var btn02Ele = document.getElementById("btn02"); 
                  btn02Ele.onclick = function(){ 
                      var lis = document.getElementsByTagName("li"); 
                      alert(lis.length) 
                  };
                  //3.查找 name=gender 的所有节点 
                  var btn03Ele = document.getElementById("btn03"); 
                  btn03Ele.onclick = function(){ 
                      var genders = document.getElementsByName("gender"); 
                      alert(genders.length) 
                  };
                  //4.查找#city 下所有 li 节点 
                  var btn04Ele = document.getElementById("btn04"); 
                  btn04Ele.onclick = function(){ 
                      //1 获取 id 为 city 的节点 
                      //2 通过 city 节点.getElementsByTagName 按标签名查子节点 
                      var lis = document.getElementById("city").getElementsByTagName("li"); 
                      alert(lis.length) 
                  };
                  //5.返回#city 的所有子节点 
                  var btn05Ele = document.getElementById("btn05"); 
                  btn05Ele.onclick = function(){ 
                      //1 获取 id 为 city 的节点 
                      //2 通过 city 获取所有子节点 
                      alert(document.getElementById("city").childNodes.length);
                  };
                  //6.返回#phone 的第一个子节点 
                  var btn06Ele = document.getElementById("btn06");
                  btn06Ele.onclick = function(){ 
                      // 查询 id 为 phone 的节点 
                      alert( document.getElementById("phone").firstChild.innerHTML ); 
                  };
                  //7.返回#bj 的父节点 
                  var btn07Ele = document.getElementById("btn07"); 
                  btn07Ele.onclick = function(){ 
                      //1 查询 id 为 bj 的节点 
                      var bjObj = document.getElementById("bj"); 
                      //2 bj 节点获取父节点 
                      alert( bjObj.parentNode.innerHTML ); 
                  };
                  //8.返回#android 的前一个兄弟节点 
                  var btn08Ele = document.getElementById("btn08");
                  btn08Ele.onclick = function(){ 
                      // 获取 id 为 android 的节点
                      // 通过 android 节点获取前面兄弟节点 
                      alert( 
                       document.getElementById("android").previousSibling.innerHTML ); 
                  };
  
                  //9.读取#username 的 value 属性值 
                  var btn09Ele = document.getElementById("btn09");
                  btn09Ele.onclick = function(){ 
                      alert(document.getElementById("username").value); };
                  //10.设置#username 的 value 属性值 
                  var btn10Ele = document.getElementById("btn10"); 
                  btn10Ele.onclick = function(){ 
                      document.getElementById("username").value = "国哥你真牛逼"; };
                  //11.返回#bj 的文本值 
                  var btn11Ele = document.getElementById("btn11");
                  btn11Ele.onclick = function(){ 
                      alert(document.getElementById("city").innerHTML); // alert(document.getElementById("city").innerText); 
                  }; 
              }; 
          </script>
      </head>
      <body>
          <div id="total"> 
              <div class="inner"> 
                  <p>你喜欢哪个城市? </p>
                  <ul id="city">
                      <li id="bj">北京</li>
                      <li>上海</li> 
                      <li>东京</li> 
                      <li>首尔</li>
                  </ul> 
                  <br> 
                  <br> 
                  <p>你喜欢哪款单机游戏? </p> 
                  <ul id="game"> 
                      <li id="rl">红警</li>
                      <li>实况</li> 
                      <li>极品飞车</li>
                      <li>魔兽</li> 
                  </ul> 
                  <br /> 
                  <br />
  
                  <p>你手机的操作系统是? </p> 
                  <ul id="phone">
                      <li>IOS</li>
                      <li id="android">Android</li>
                      <li>Windows Phone</li>
                  </ul> 
              </div> 
              <div class="inner"> 
                  gender: 
                  <input type="radio" name="gender" value="male"/> 
                  Male 
                  <input type="radio" name="gender" value="female"/> 
                  Female 
                  <br> 
                  <br> 
                  name: 
                  <input type="text" name="name" id="username" value="abcde"/> 
              </div> 
          </div> 
          <div id="btnList"> 
              <div><button id="btn01">查找#bj 节点</button></div> 
              <div><button id="btn02">查找所有 li 节点</button></div> 
              <div><button id="btn03">查找 name=gender 的所有节点</button></div> 
              <div><button id="btn04">查找#city 下所有 li 节点</button></div> 
              <div><button id="btn05">返回#city 的所有子节点</button></div> 
              <div><button id="btn06">返回#phone 的第一个子节点</button></div> 
              <div><button id="btn07">返回#bj 的父节点</button></div> 
              <div><button id="btn08">返回#android 的前一个兄弟节点</button></div> 
              <div><button id="btn09">返回#username 的 value 属性值</button></div> 
              <div><button id="btn10">设置#username 的 value 属性值</button></div>
              <div><button id="btn11">返回#bj 的文本值</button></div> 
          </div> 
      </body> 
  </html>
  ```



## 第三章 jQuery

### 1. **jQuery** **介绍**

- **什么是** **jQuery ?** 

  jQuery，顾名思义，也就是 JavaScript 和查询（Query），它就是辅助 JavaScript 开发的 js 类库。 

- **jQuery** **核心思想！！！** 

  它的核心思想是 write less,do more(写得更少,做得更多)，所以它实现了很多浏览器的兼容问题。 

- **jQuery** **流行程度** 

  jQuery 现在已经成为最流行的 JavaScript 库，在世界前 10000 个访问最多的网站中，有超过 55%在使用 jQuery。 

- **jQuery 好处！！！** 

  jQuery 是免费、开源的，jQuery 的语法设计可以使开发更加便捷，例如操作文档对象、选择 DOM 元素、 制作动画效果、事件处理、使用 Ajax 以及其他功能。

### 2. **jQuery** **的初体验！！！**

- 需求：使用 jQuery 给一个按钮绑定单击事件?

  ```html
  <!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd"> 
  <html> 
      <head>
          <meta http-equiv="Content-Type" content="text/html; charset=UTF-8"> 
          <title>Insert title here</title>
          <script type="text/javascript" src="../script/jquery-1.7.2.js"></script>
          <script type="text/javascript"> 
              // window.onload = function () { 
              	// var btnObj = document.getElementById("btnId"); 
              	// // alert(btnObj);//[object HTMLButtonElement] ====>>> dom 对象 
              	// btnObj.onclick = function () {
              		// alert("js 原生的单击事件"); 
              	// } 
              // } 
              
              $(function () { // 表示页面加载完成 之后，相当 window.onload = function () {} 
                  var $btnObj = $("#btnId"); // 表示按 id 查询标签对象 
                  $btnObj.click(function () { // 绑定单击事件 
                      alert("jQuery 的单击事件"); 
                  }); 
              }); 
          </script> 
      </head> 
      <body>
          <button id="btnId">SayHello</button> 
      </body>
  </html>
  ```

- 常见问题

  1、使用 jQuery 一定要引入 jQuery 库吗？ 

  ​	答案： 是，必须 

  2、jQuery 中的$到底是什么？ 

  ​	答案： 它是一个函数 

  3、怎么为按钮添加点击响应函数的？ 

  ​	答案： 

  ​		1、使用 jQuery 查询到标签对象 

  ​		2、使用标签对象.click( function(){} );

### 3.**jQuery** **核心函数**

\$ 是 jQuery 的核心函数，能完成 jQuery 的很多功能。\$()就是调用$这个函数

1. 传入参数为 [ 函数 ] 时： 

   表示页面加载完成之后。相当于 window.onload = function(){} 

2. 传入参数为 [ HTML 字符串 ] 时： 

   会对我们创建这个 html 标签对象 

3. 传入参数为 [ 选择器字符串 ] 时： 

   $(“#id 属性值”);      id 选择器，根据 id 查询标签对象 

   $(“标签名”);             标签名选择器，根据指定的标签名查询标签对象 

   $(“.class 属性值”);   类型选择器，可以根据 class 属性查询标签对象 

4. 传入参数为 [ DOM 对象 ] 时： 

   会把这个 dom 对象转换为 jQuery 对象

### 4. **jQuery** **对象和** **dom** **对象区分**

- **什么是** **jQuery** **对象，什么是** **dom** **对象** 

  - **Dom** **对象** 

    1. 通过 getElementById()查询出来的标签对象是 Dom 对象 

    2. 通过 getElementsByName()查询出来的标签对象是 Dom 对象 

    3. 通过 getElementsByTagName()查询出来的标签对象是 Dom 对象 

    4. 通过 createElement() 方法创建的对象，是 Dom 对象 

    DOM 对象 Alert 出来的效果是：*[object HTML* *标签名* *Element]*

  - **jQuery** **对象** 

    5. 通过 JQuery 提供的 API 创建的对象，是 JQuery 对象 

    6. 通过 JQuery 包装的 Dom 对象，也是 JQuery 对象 

    7. 通过 JQuery 提供的 API 查询到的对象，是 JQuery 对象 

    jQuery 对象 Alert 出来的效果是：[object Object]

- **问题：jQuery对象的本质是什么？** 

  jQuery 对象是 dom 对象的数组 + jQuery 提供的一系列功能函数。

- **jQuery** **对象和** **Dom** **对象使用区别** 

  jQuery 对象不能使用 DOM 对象的属性和方法 

  DOM 对象也不能使用 jQuery 对象的属性和方法

- **Dom** **对象和** **jQuery** **对象互转** 

  **1、dom对象转化为 jQuery 对象（重点）** 

  1. 先有 DOM 对象 

  2. $( DOM 对象 ) 就可以转换成为 jQuery 对象 

  **2、jQuery 对象转为dom对象（重点）** 

  1. 先有 jQuery 对象 

  2. jQuery 对象[下标]取出相应的 DOM 对象

  ![image-20211025140650125](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211025140650125.png)

  

### 5. **jQuery** **选择器（***重点）

- **基本选择器**

  \#ID 选择器：根据 id 查找标签对象 

  .class 选择器：根据 class 查找标签对象 

  element 选择器：根据标签名查找标签对象 

  \* 选择器：表示任意的，所有的元素 

  selector1，selector2 组合选择器：合并选择器 1，选择器 2 的结果并返回

  

- **层级选择器**

  ancestor descendant 

  后代选择器 ：在给定的祖先元素下匹配所有的后代元素 

  parent > child 

  子元素选择器：在给定的父元素下匹配所有的子元素 

  prev + next 

  相邻元素选择器：匹配所有紧接在 prev 元素后的 next 元素 

  prev ~ sibings 

  之后的兄弟元素选择器：匹配 prev 元素之后的所有 siblings 元素

  

- **过滤选择器**

  - **基本过滤器：**

    **:first** 

    获取第一个元素 

    **:last** 

    获取最后个元素 

    :not(selector) 

    去除所有与给定选择器匹配的元素 

    :even 

    匹配所有索引值为偶数的元素，从 0 开始计数 

    :odd 

    匹配所有索引值为奇数的元素，从 0 开始计数 

    **:eq(index)** 

    匹配一个给定索引值的元素 

    :gt(index) 

    匹配所有大于给定索引值的元素 

    :lt(index) 

    匹配所有小于给定索引值的元素 

    :header 

    匹配如 h1, h2, h3 之类的标题元素 

    :animated 

    匹配所有正在执行动画效果的元素

    

  - **内容过滤器：**

    :contains(text) 

    匹配包含给定文本的元素 

    :empty 

    匹配所有不包含子元素或者文本的空元素 

    :parent 

    匹配含有子元素或者文本的元素 

    :has(selector) 

    匹配含有选择器所匹配的元素的元素

    

  - **属性过滤器：**

    **[attribute]** 

    **匹配包含给定属性的元素。** 

    **[attribute=value]** 

    **匹配给定的属性是某个特定值的元素** 

    [attribute!=value] 

    匹配所有不含有指定的属性，或者属性不等于特定值的元素。 

    [attribute^=value] 

    匹配给定的属性是以某些值开始的元素 

    [attribute$=value] 

    匹配给定的属性是以某些值结尾的元素 

    [attribute*=value] 

    匹配给定的属性是以包含某些值的元素 

    \[attrSel1]\[attrSel2][attrSelN] 

    复合属性选择器，需要同时满足多个条件时使用。

    

  - **表单过滤器：**

    :input 

    匹配所有 input, textarea, select 和 button 元素 

    **:text** 

    匹配所有 文本输入框 

    **:password** 

    匹配所有的密码输入框 

    **:radio** 

    匹配所有的单选框 

    **:checkbox** 

    匹配所有的复选框 

    :submit 

    匹配所有提交按钮 

    :image 

    匹配所有 img 标签 

    :reset 

    匹配所有重置按钮 

    :button 

    匹配所有 input type=button \<button>按钮 

    :file 

    匹配所有 input type=file 文件上传 

    :hidden 

    匹配所有不可见元素 display:none 或 input type=hidden

    

  - **表单对象属性过滤器：**

    :enabled 

    匹配所有可用元素 

    :disabled 

    匹配所有不可用元素 

    **:checked** 

    **匹配所有选中的单选，复选，和下拉列表中选中的** **option** **标签对象** 

    **:selected** 

    **匹配所有选中的** **option**

    

### 6. **jQuery** **元素筛选**

1. eq()    获取给定索引的元素                  功能跟 :eq() 一样 
2. first()  获取第一个元素                         功能跟 :first 一样 
3. last()   获取最后一个元素                     功能跟 :last 一样 
4. filter(exp)  留下匹配的元素 
5. is(exp)   判断是否匹配给定的选择器，只要有一个匹配就返回，true 
6. has(exp)   返回包含有匹配选择器的元素的元素                 功能跟 :has 一样 
7. not(exp)    删除匹配选择器的元素                                        功能跟 :not 一样 
8. children(exp) 返回匹配给定选择器的子元素        功能跟 parent>child 一样 
9. find(exp)  返回匹配给定选择器的后代元素    功能跟 ancestor descendant 一样
10. next()   返回当前元素的下一个兄弟元素          功能跟 prev + next 功能一样 
11. nextAll()  返回当前元素后面所有的兄弟元素   功能跟 prev ~ siblings 功能一样 
12. nextUntil()   返回当前元素到指定匹配的元素为止的后面元素 
13. parent()  返回父元素 
14. prev(exp)  返回当前元素的上一个兄弟元素 
15. prevAll()  返回当前元素前面所有的兄弟元素 
16. prevUnit(exp) 返回当前元素到指定匹配的元素为止的前面元素 
17. siblings(exp)  返回所有兄弟元素 
18. add()    把 add 匹配的选择器的元素添加到当前 jquery 对象中



### 7. **jQuery** **的属性操作**

![image-20211025225855677](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211025225855677.png)

- html() 

  它可以设置和获取起始标签和结束标签中的内容。 

  跟 dom 属性 innerHTML 一样。 

- text() 

  它可以设置和获取起始标签和结束标签中的文本。 

  跟 dom 属性 innerText 一样。 

- val() 

  它可以设置和获取表单项的 value 属性值。 

  跟 dom 属性 value 一样

![image-20211025230119965](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211025230119965.png)

- attr() 

  可以设置和获取属性的值，不推荐操作 checked、readOnly、selected、disabled 等等 

  attr 方法还可以操作非标准的属性。比如自定义属性：abc,bbj 

- prop() 

  可以设置和获取属性的值,只推荐操作 checked、readOnly、selected、disabled 等等

### 8. **DOM** **的增删改**

![image-20211025230350486](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211025230350486.png)

**内部插入：** 

- appendTo() 

  a.appendTo(b) 

  把 a 插入到 b 子元素末尾，成为最后一个子元素

- prependTo() 

  a.prependTo(b) 

  把 a 插到 b 所有子元素前面，成为第一个子元素 

**外部插入：** 

- insertAfter() 

  a.insertAfter(b) 

  得到 ba 

- insertBefore() 

  a.insertBefore(b) 

  得到 ab 

**替换**: 

- replaceWith() 

  a.replaceWith(b) 

  用 b 替换掉 a 

- replaceAll() 

  a.replaceAll(b) 

  用 a 替换掉所有 b 

**删除：** 

- remove() 

  a.remove(); 

  删除 a 标签 

- empty() 

  a.empty(); 

  清空 a 标签里的内容



### 9. **CSS** **样式操作**

1. addClass()   向被选元素添加CSS样式 
2. removeClass()  删除样式 
3. toggleClass()     有就删除，没有就添加样式。 
4. offset()     获取和设置元素的坐标。



### 10 .**jQuery** **动画**

- **基本动画** 
  - show()     将隐藏的元素显示 
  - hide()      将可见的元素隐藏。 
  - toggle()        可见就隐藏，不可见就显示。 

  以上动画方法都可以添加参数。 

  1、第一个参数是动画 执行的时长，以毫秒为单位 

  2、第二个参数是动画的回调函数 (动画完成后自动调用的函数) 

- **淡入淡出动画** 
  - fadeIn()   淡入（慢慢可见） 
  - fadeOut()  淡出（慢慢消失） 
  - fadeTo()   在指定时长内慢慢的将透明度修改到指定的值。0 透明，1 完成可见，0.5 半透明 
  - fadeToggle()    淡入/淡出 切换



### 11. **jQuery** **事件操作**

- **$( function(){} );** **和** **window.onload = function(){}** **的区别？**

  - 他们分别是在什么时候触发？ 

    1、jQuery 的页面加载完成之后是浏览器的内核解析完页面的标签创建好 DOM 对象之后就会马上执行。 

    2、原生 js 的页面加载完成之后，除了要等浏览器内核解析完标签创建好 DOM 对象，还要等标签显示时需要的内容加载完成。

  - 他们触发的顺序？ 

    1、jQuery 页面加载完成之后 先执行 

    2、原生 js 的页面加载完成之后 

  - 他们执行的次数？ 

    1、原生 js 的页面加载完成之后，只会执行最后一次的赋值函数。 

    2、jQuery 的页面加载完成之后是全部把注册的 function 函数，依次顺序全部执行。

- **jQuery** **中其他的事件处理方法：**

  - click()  它可以绑定单击事件，以及 触发单击事件 

  - mouseover()  鼠标移入事件 

  - mouseout() 鼠标移出事件 

  - bind() 可以给元素一次性绑定一个或多个事件。 

  - one()  使用上跟 bind 一样。但是 one 方法绑定的事件只会响应一次。 

  - unbind() 跟 bind 方法相反的操作，解除事件的绑定 

  - live() 也是用来绑定事件。它可以用来绑定选择器匹配的所有元素的事件。哪怕这个元素是后面动态创建出来的也有效 。

- **事件的冒泡** 

  - 什么是事件的冒泡？ 

    事件的冒泡是指，父子元素同时监听同一个事件。当触发子元素的事件的时候，同一个事件也被传递到了父元素的事件里去响应。 

  - 那么如何阻止事件冒泡呢？ 

    在子元素事件函数体内，return false; 可以阻止事件的冒泡传递。

- **javaScript** **事件对象** 

  事件对象，是封装有触发的事件信息的一个 javascript 对象。 

  我们重点关心的是怎么拿到这个 javascript 的事件对象。以及使用。

   

  如何获取呢 javascript 事件对象呢？ 

  在给元素绑定事件的时候，在事件的 function( event ) 参数列表中添加一个参数，这个参数名，我们习惯取名为 event。 

  这个 event 就是 javascript 传递参事件处理函数的事件对象。



比如：

//1.原生 javascript 获取 事件对象

```html
window.onload = function () { 	
document.getElementById("areaDiv").onclick = function (event) { 
	console.log(event); 
	} 
}
```

//2.jQuery 代码获取 事件对象

```html
$(function () {
	$("#areaDiv").click(function (event) { 		
		console.log(event); 
	});
});
```

//3.使用 bind 同时对多个事件绑定同一个函数。怎么获取当前操作是什么事件。

```html
$("#areaDiv").bind("mouseover mouseout",function (event) { 
	if (event.type == "mouseover") { 
		console.log("鼠标移入"); 
	} else if (event.type == "mouseout") { 		
		console.log("鼠标移出");
	} 
});
```



## 第四章 XML

### 1. **XML** **简介**

- xml 是可扩展的标记性语言。

- **xml** **的作用** 

  xml 的主要作用有： 

  1、用来保存数据，而且这些数据具有自我描述性 

  2、它还可以做为项目或者模块的配置文件 

  3、还可以做为网络传输数据的格式（现在 JSON 为主）。

### 2. **xml** **语法**

1. 文档声明 

2. 元素（标签） 

3. xml 属性 

4. xml 注释 

5. 文本区域（CDATA 区）

我们先创建一个简单 XML 文件，用来描述图书信息。

```xml
<?xml version="1.0" encoding="UTF-8"?> 
<!-- xml 声明 version 是版本的意思 encoding 是编码 --> <books> <!-- 这是 xml 注释 -->
	<book id="SN123123413241"> <!-- book 标签描述一本图书 id 属性描述 的是图书 的编号 --> 
        <name>java 编程思想</name> <!-- name 标签描述 的是图书 的信息 --> 
        <author>华仔</author> <!-- author 单词是作者的意思 ，描述图书作者 --> 
        <price>9.9</price> <!-- price 单词是价格，描述的是图书 的价格 --> 
    </book> 
    <book id="SN12341235123"> <!-- book 标签描述一本图书 id 属性描述 的是图书 的编号 --> 
        <name>葵花宝典</name> <!-- name 标签描述 的是图书 的信息 -->
        <author>班长</author> <!-- author 单词是作者的意思 ，描述图书作者 --> 
        <price>5.5</price><!-- price 单词是价格，描述的是图书 的价格 --> 
    </book> 
</books>
```

\<?xml version=*"1.0"* encoding=*"UTF-8"*?> xml 声明。 

\<!-- xml 声明 version 是版本的意思 encoding 是编码 --> 

而且这个<?xml 要连在一起写，否则会有报错

- **属性**

  version 是版本号 

  encoding 是 xml 的文件编码 

  standalone="yes/no" 表示这个 xml 文件是否是独立的 xml 文件;

- 在浏览器中可以查看到xml文档

- **xml 注释**

  html 和 XML 注释 一样 : \<!-- html 注释 -->

- **元素（标签）**

  咱们先回忆一下: 

  - html 标签： 

    格式：<标签名>封装的数据</标签名> 

    单标签: <标签名 />   \<br /> 换行 \<hr />水平线 

    双标签 <标签名>封装的数据</标签名> 

    标签名大小写不敏感 

    标签有属性，有基本属性和事件属性 

    标签要闭合（不闭合 ，html 中不报错。但我们要养成良好的书写习惯。闭合）

  - xml 元素

    - ![image-20211028140827115](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211028140827115.png)

    - XML 命名规则

      1. 名称可以含字母、数字以及其他的字符

      2. 名称不能以数字或者标点符号开始
      3. 名称不能以字符 “xml”（或者 XML、Xml）开始
      4. 名称不能包含空格

    - xml 中的元素（标签）也 分成 单标签和双标签：

      1. 单标签

         格式： <标签名 属性=”值” 属性=”值” ...... /> 

      2. 双标签

         格式：< 标签名 属性=”值” 属性=”值” ......>文本数据或子标签</标签名>

- **xml** **属性**

  ![image-20211028141313192](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211028141313192.png)

- **语法规则**

  1. **所有** **XML** **元素都须有关闭标签（也就是闭合）**

  2. **XML** **标签对大小写敏感**

  3. **XML** **必须正确地嵌套**

  4. **XML** **文档必须有根元素**

     根元素就是顶级元素， 

     没有父标签的元素，叫顶级元素。 

     根元素是没有父标签的顶级元素，而且是唯一一个才行。

  5. **XML** **的属性值须加引号**

  6. **XML** **中的特殊字符**

     ![image-20211028141621858](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211028141621858.png)

  7. **文本区域（CDATA 区）**

     CDATA 语法可以告诉 xml 解析器，我 CDATA 里的文本内容，只是纯文本，不需要 xml 语法解析 ;

     CDATA 格式： 

     **<![CDATA[** 这里可以把你输入的字符原样显示，不会解析 xml **]]>**

     

### 3. **xml** **解析技术介绍**

- xml 可扩展的标记语言。 

  不管是 html 文件还是 xml 文件它们都是标记型文档，都可以使用 w3c 组织制定的 dom 技术来解析;

  ![image-20211028141923097](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211028141923097.png)

  document 对象表示的是整个文档（可以是 html 文档，也可以是 xml 文档）

- **早期** **JDK** **为我们提供了两种** **xml** **解析技术** **DOM** **和** **Sax** **简介（已经过时，但我们需要知道这两种技术）**

  dom 解析技术是 W3C 组织制定的，而所有的编程语言都对这个解析技术使用了自己语言的特点进行实现。 

  Java 对 dom 技术解析标记也做了实现。 

  sun 公司在 JDK5 版本对 dom 解析技术进行升级：SAX（ Simple API for XML ） 

  SAX 解析，它跟 W3C 制定的解析不太一样。它是以类似事件机制通过回调告诉用户当前正在解析的内容。 

  它是一行一行的读取 xml 文件进行解析的。不会创建大量的 dom 对象。 

  所以它在解析 xml 的时候，在内存的使用上。和性能上。都优于 Dom 解析。

- 第三方的解析 

  1. jdom 在 dom 基础上进行了封装 、 

  2. **dom4j** 又对 jdom 进行了封装。 

  3. pull 主要用在 Android 手机开发，是在跟 sax 非常类似都是事件机制解析 xml 文件。 

  这个 Dom4j 它是第三方的解析技术。我们需要使用第三方给我们提供好的类库才可以解析 xml 文件。

- **dom4j** **解析技术（重点）**

  - 由于 dom4j 它不是 sun 公司的技术，而属于第三方公司的技术，我们需要使用 dom4j 就需要到 dom4j 官网下载 dom4j 的 jar 包。

  - **dom4j** **编程步骤：**

    第一步： 先加载 xml 文件创建 Document 对象 

    第二步：通过 Document 对象拿到根元素对象 

    第三步：通过根元素.elelemts(标签名); 可以返回一个集合，这个集合里放着所有你指定的标签名的元素对象 

    第四步：找到你想要修改、删除的子元素，进行相应在的操作 

    第五步，保存到硬盘上

  - 示例：

    ```xml
    <?xml version="1.0" encoding="UTF-8"?> 
    <books> 
        <book sn="SN12341232"> 
            <name>辟邪剑谱</name>
            <price>9.9</price>
    
            <author>班主任</author>
        </book> <book sn="SN12341231">
            <name>葵花宝典</name> 
            <price>99.99</price> 
            <author>班长</author> 
        </book> 
    </books>
    ```

    ```java
    /** 读取 xml 文件中的内容 */ 
    @Test 
    public void readXML() throws DocumentException { 
        // 需要分四步操作: 
        // 第一步，通过创建 SAXReader 对象。来读取 xml 文件，获取 Document 对象 
        // 第二步，通过 Document 对象。拿到 XML 的根元素对象 
        // 第三步，通过根元素对象。获取所有的 book 标签对象 
        // 第四步，遍历每个 book 标签对象。然后获取到 book 标签对象内的每一个元素，再通过 getText() 方法拿到起始标签和结束标签之间的文本内容 
        
        // 第一步，通过创建 SAXReader 对象。来读取 xml 文件，获取 Document 对象 
        SAXReader reader = new SAXReader(); 
        Document document = 
            reader.read("src/books.xml"); 
        // 第二步，通过 Document 对象。拿到 XML 的根元素对象 
        Element root = document.getRootElement(); 
        // 打印测试 
        // Element.asXML() 它将当前元素转换成为 String 对象 
        // System.out.println( root.asXML() ); 
        // 第三步，通过根元素对象。获取所有的 book 标签对象 
        // Element.elements(标签名)它可以拿到当前元素下的指定的子元素的集合
        List<Element> books = root.elements("book"); 
        // 第四步，遍历每个 book 标签对象。然后获取到 book 标签对象内的每一个元素， 
        for (Element book : books) { 
            // 测试 
            // System.out.println(book.asXML());
            // 拿到 book 下面的 name 元素对象 
            Element nameElement = 
                book.element("name"); 
            // 拿到 book 下面的 price 元素对象 
            Element priceElement = 
                book.element("price"); 
            // 拿到 book 下面的 author 元素对象 
            Element authorElement = 
                book.element("author"); 
            // 再通过 getText() 方法拿到起始标签和结束标签之间的文本内容 
            System.out.println("书名" + 
                               nameElement.getText() 
                               + " , 价格:" + 
                               priceElement.getText() 
                               + ", 作者：" +                         authorElement.getText());
        } 
    }
    ```

    

## 第五章 Tomcat

### 1. **JavaWeb** **的概念**

- JavaWeb 是指，所有通过 Java 语言编写可以通过浏览器访问的程序的总称，叫 JavaWeb。 

  JavaWeb 是基于请求和响应来开发的。

  - 请求是指客户端给服务器发送数据，叫请求 Request。
  - 响应是指服务器给客户端回传数据，叫响应 Response。
  - 请求和响应是成对出现的，有请求就有响应。

  ![image-20211028152259836](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211028152259836.png)

- Web 资源的分类

  web 资源按实现的技术和呈现的效果的不同，又分为静态资源和动态资源两种。 

  静态资源： html、css、js、txt、mp4 视频 , jpg 图片 

  动态资源： jsp 页面、Servlet 程序

- 常用的 Web 服务器

  Tomcat：由 Apache 组织提供的一种 Web 服务器，提供对 jsp 和 Servlet 的支持。它是一种轻量级的 javaWeb 容器（服务器），也是当前应用最广的 JavaWeb 服务器（免费）。 

  Jboss：是一个遵从 JavaEE 规范的、开放源代码的、纯 Java 的 EJB 服务器，它支持所有的 JavaEE 规范（免费）。 

  GlassFish： 由 Oracle 公司开发的一款 JavaWeb 服务器，是一款强健的商业服务器，达到产品级质量（应用很少）。 

  Resin：是 CAUCHO 公司的产品，是一个非常流行的服务器，对 servlet 和 JSP 提供了良好的支持，性能也比较优良，resin 自身采用 JAVA 语言开发（收费，应用比较多）。 

  WebLogic：是 Oracle 公司的产品，是目前应用最广泛的 Web 服务器，支持 JavaEE 规范，而且不断的完善以适应新的开发要求，适合大型项目（收费，用的不多，适合大公司）

### 2. **Tomcat** **的使用**

1. **目录介绍** 

   bin 	专门用来存放 Tomcat 服务器的可执行程序 

   conf 	专门用来存放 Tocmat 服务器的配置文件 

   lib 	专门用来存放 Tomcat 服务器的 jar 包 

   logs 	专门用来存放 Tomcat 服务器运行时输出的日记信息 

   temp 	专门用来存放 Tomcdat 运行时产生的临时数据 

   webapps 	专门用来存放部署的 Web 工程。 

   work 	是 Tomcat 工作时的目录，用来存放 Tomcat 运行时 jsp 翻译为 Servlet 的源码，和 Session 钝化(序列化)的目录。

2. **如何启动** **Tomcat** **服务器** 

   - 找到 Tomcat 目录下的 bin 目录下的 startup.bat 文件，双击，就可以启动 Tomcat 服务器。 

     如何测试 Tomcat 服务器启动成功？？？ 

     打开浏览器，在浏览器地址栏中输入以下地址测试： 

     1、http://localhost:8080 

     2、http://127.0.0.1:8080 

     3、http://真实 ip:8080 

     当出现如下界面，说明 Tomcat 服务器启动成功！！！

     ![image-20211028153406315](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211028153406315.png)

   - 另一种启动 tomcat 服务器的方式

     1、打开命令行 

     2、cd 到 你的 Tomcat 的 bin 目录下

     ![image-20211028153536096](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211028153536096.png)

     3、敲入启动命令： catalina run

3. **如何修改** **Tomcat** **的端口号**

   - Mysql 默认的端口号是：3306 

     Tomcat 默认的端口号是：8080 

     找到 Tomcat 目录下的 conf 目录，找到 server.xml 配置文件。

     ![image-20211028153750596](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211028153750596.png)

     注意：平时上百度：http://www.baidu.com:80 

     ​			HTTP 协议默认的端口号是：80

4. **如何部暑** **web** **工程到** **Tomcat** **中**

   - 第一种部署方法：只需要把 web 工程的目录拷贝到 Tomcat 的 webapps 目录下即可。

     - 如何访问 Tomcat 下的 web 工程

       只需要在浏览器中输入访问地址格式如下： 

       ​	http://ip:port/工程名/目录下/文件名

   - 第二种部署方法：

     找到 Tomcat 下的 conf 目录\Catalina\localhost\ 下,创建如下的配置文件：

     ```xml
     <!-- Context 表示一个工程上下文 
     		path 表示工程的访问路径:/abc 
     		docBase 表示你的工程目录在哪里
      --> 
     <Context path="/abc" docBase="E:\book" />
     ```

     访问这个工程的路径如下:http://ip:port/abc/ 

     就表示访问 E:\book 目录

   

5. **手托 html 页面到浏览器和在浏览器中输入http://ip:端口号/工程名/访问的区别**

   - 手托 html 页面的原理：

     ![image-20211028154629697](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211028154629697.png)

   - 输入访问地址访问的原因：(访问服务器：客户端请求 服务器响应！！)

     ![image-20211028154640348](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211028154640348.png)

6. **ROOT** **的工程的访问，以及 默认** **index.html** **页面的访问**

   当我们在浏览器地址栏中输入访问地址如下： 

   http://ip:port/ ====>>>> 没有工程名的时候，默认访问的是 ROOT 工程。 

   当我们在浏览器地址栏中输入的访问地址如下： 

   http://ip:port/工程名/ ====>>>> 没有资源名，默认访问 index.html 页面

7. **IDEA** **整合** **Tomcat** **服务器**

   操作的菜单如下：File | Settings | Build, Execution, Deployment | Application Servers

8. **IDEA** **中动态** **web** **工程的操作**

   - 创建

   - Web 工程的目录介绍

     ![image-20211028155258152](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211028155258152.png)

   - 如何在 IDEA 中部署工程到 Tomcat 上运行

     1. 建议修改web工程对应的Tomcat运行实例名称

     2. 确认你的Tomcat实例中有你要部署运行的web工程模块：

        ![image-20211028162723586](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211028162723586.png)

     3. 你还可以修改你的Tomcat实例启动后默认的访问地址

     4. 在IDEA中如何运行，和停止Tomcat实例

        ![image-20211028162841851](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211028162841851.png)

        

        

## 第六章  **Servlet**

### 1. **Servlet** **技术**

- **什么是** **Servlet** 

  1、Servlet 是 JavaEE 规范之一。规范就是接口 

  2、Servlet 就 JavaWeb 三大组件之一。三大组件分别是：Servlet 程序、Filter 过滤器、Listener 监听器。 

  3、Servlet 是运行在服务器上的一个 java 小程序，它可以接收客户端发送过来的请求，并响应数据给客户端。

- **手动实现** **Servlet** **程序** 

  1、编写一个类去实现 Servlet 接口 

  2、实现 service 方法，处理请求，并响应数据 

  3、到 web.xml 中去配置 servlet 程序的访问地址

  ```java
  public class HelloServlet implements Servlet { 
      /**
      * service 方法是专门用来处理请求和响应的 
      * @param servletRequest 
      * @param servletResponse 
      * @throws ServletException 
      * @throws IOException 
      */ 
      @Override 
      public void service(ServletRequest servletRequest, ServletResponse servletResponse) throws ServletException, IOException { 
          System.out.println("Hello Servlet 被访问了"); 
      } 
  }
  ```

  ```xml
  <?xml version="1.0" encoding="UTF-8"?>
  <web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee" 
           xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee                      http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd" 
           version="4.0"> 
      <!-- servlet 标签给 Tomcat 配置 Servlet 程序 --> 
      <servlet> 
          <!--servlet-name 标签 Servlet 程序起一个别名（一般是类名） --> 
          <servlet-name>HelloServlet</servlet-name> 
          <!--servlet-class 是 Servlet 程序的全类名--> 
          <servlet-class>com.atguigu.servlet.HelloServlet</servlet-class>
      </servlet> 
      <!--servlet-mapping 标签给 servlet 程序配置访问地址--> 
      <servlet-mapping> 
          <!--servlet-name 标签的作用是告诉服务器，我当前配置的地址给哪个 Servlet 程序使用--> 
          <servlet-name>HelloServlet</servlet-name> <!--url-pattern 标签配置访问地址 <br/> 
  / 斜杠在服务器解析的时候，表示地址为：http://ip:port/工程路径 <br/> 
  /hello 表示地址为：http://ip:port/工程路径/hello <br/> 
  --> 
          <url-pattern>/hello</url-pattern> 
      </servlet-mapping>
  </web-app>
  ```

- **url** **地址到** **Servlet** **程序的访问**

  ![image-20211029132351380](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211029132351380.png)

- **Servlet** **的生命周期** 

  1、执行 Servlet 构造器方法 

  2、执行 init 初始化方法 

  ​	第一、二步，是在第一次访问的时候创建 Servlet 程序会调用。 

  3、执行 service 方法 

  ​	第三步，每次访问都会调用。 

  4、执行 destroy 销毁方法 

  ​	第四步，在 web 工程停止的时候调用。

- **GET** **和** **POST** **请求的分发处理**

  ```java
  public class HelloServlet implements Servlet { 
      /**
      * service 方法是专门用来处理请求和响应的 
      * @param servletRequest 
      * @param servletResponse 
      * @throws ServletException 
      * @throws IOException 
      */ 
      @Override 
      public void service(ServletRequest servletRequest, ServletResponse servletResponse) throws ServletException, IOException { 
          System.out.println("3 service === Hello Servlet 被访问了"); 
          // 类型转换（因为它有 getMethod()方法） 
          HttpServletRequest httpServletRequest = (HttpServletRequest) servletRequest; 
          // 获取请求的方式 
          String method = 
              httpServletRequest.getMethod(); 
          if ("GET".equals(method)) { 
              doGet(); 
          } else if ("POST".equals(method)) { 
              doPost(); 
          } 
      }
      /**
      * 做 get 请求的操作 
      */ 
      public void doGet(){ 
          System.out.println("get 请求"); 
          System.out.println("get 请求"); }
      /*
      ** 做 post 请求的操作 
      */ 
      public void doPost(){ 
          System.out.println("post 请求"); 
          System.out.println("post 请求"); 
      } 
  }
  ```

- **通过继承** **HttpServlet** **实现** **Servlet** **程序** 

  一般在实际项目开发中，都是使用继承 HttpServlet 类的方式去实现 Servlet 程序。 

  1、编写一个类去继承 HttpServlet 类 

  2、根据业务需要重写 doGet 或 doPost 方法 

  3、到 web.xml 中的配置 Servlet 程序的访问地址

  ```java
  public class HelloServlet2 extends HttpServlet { 
      /*
      ** doGet（）在 get 请求的时候调用 
      * @param req 
      * @param resp 
      * @throws ServletException 
      * @throws IOException 
      */ 
      @Override 
      protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException { 
          System.out.println("HelloServlet2 的 doGet 方法"); 
      }
      /*
      ** doPost（）在 post 请求的时候调用
      * @param req 
      * @param resp 
      * @throws ServletException 
      * @throws IOException
      */ 
      @Override 
      protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException { 
          System.out.println("HelloServlet2 的 doPost 方法"); 
      } 
  }
  ```

- **使用** **IDEA** **创建** **Servlet** **程序** 

  菜单：new ->Servlet 程序

- **Servlet** **类的继承体系**

  ![image-20211029133355969](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211029133355969.png)

  

### 2. **ServletConfig** **类**

ServletConfig 类从类名上来看，就知道是 Servlet 程序的配置信息类。 

Servlet 程序和 ServletConfig 对象都是由 Tomcat 负责创建，我们负责使用。 

Servlet 程序默认是第一次访问的时候创建，ServletConfig 是每个 Servlet 程序创建时，就创建一个对应的 ServletConfig 对象。

- **ServletConfig** **类的三大作用** 

  1、可以获取 Servlet 程序的别名 servlet-name 的值 

  2、获取初始化参数 init-param 

  3、获取 ServletContext 对象

  ```xml
  <!-- servlet 标签给 Tomcat 配置 Servlet 程序 -->
      <servlet>
          <!--servlet-name 标签 Servlet 程序起一个别名（一般是类名） -->
          <servlet-name>HelloServlet</servlet-name>
          <!--servlet-class 是 Servlet 程序的全类名-->
          <servlet-class>com.yt.servlet_.HelloServlet</servlet-class>
          <!--init-param 是初始化参数-->
          <init-param>
              <!--是参数名-->
              <param-name>username</param-name>
              <!--是参数值-->
              <param-value>root</param-value>
          </init-param>
          <!--init-param 是初始化参数-->
          <init-param>
              <!--是参数名-->
              <param-name>url</param-name>
              <!--是参数值-->
              <param-value>jdbc:mysql://localhost:3306/test</param-value>
          </init-param>
      </servlet>
      <!--servlet-mapping 标签给 servlet 程序配置访问地址-->
      <servlet-mapping>
          <!--servlet-name 标签的作用是告诉服务器，我当前配置的地址给哪个 Servlet 程序使用-->
          <servlet-name>HelloServlet</servlet-name>
          <!--url-pattern 标签配置访问地址 <br/>
              / 斜杠在服务器解析的时候，表示地址为：http://ip:port/工程路径 <br/>
              /hello 表示地址为：http://ip:port/工程路径/hello <br/> -->
          <url-pattern>/hello</url-pattern>
      </servlet-mapping>
  ```

  ```java
  @Override 
  public void init(ServletConfig servletConfig) throws ServletException { 
      System.out.println("2 init 初始化方法"); 
      // 1、可以获取 Servlet 程序的别名 servlet-name 的值 
      System.out.println("HelloServlet 程序的别名是:" + servletConfig.getServletName()); 
      // 2、获取初始化参数 init-param 
      System.out.println("初始化参数 username 的值是;" + servletConfig.getInitParameter("username")); 
      System.out.println("初始化参数 url 的值是;" + servletConfig.getInitParameter("url")); 
      // 3、获取 ServletContext 对象   
      System.out.println(servletConfig.getServletContext()); 
  }
  ```

  

### 3.**ServletContext** **类**

- **什么是** **ServletContext?** 

  1、ServletContext 是一个接口，它表示 Servlet 上下文对象 

  2、一个 web 工程，只有一个 ServletContext 对象实例。 

  3、ServletContext 对象是一个域对象。 

  4、ServletContext 是在 web 工程部署启动的时候创建。在 web 工程停止的时候销毁。 

  - 什么是域对象? 

    域对象，是可以像 Map 一样存取数据的对象，叫域对象。 

    这里的域指的是存取数据的操作范围，整个 web 工程。 

    ​	    存数据    		       取数据  					 删除 数据 

  Map        put()                      get()                          remove() 

  域对象    setAttribute()       getAttribute()          removeAttribute();

- **ServletContext** **类的四个作用** 

  1、获取 web.xml 中配置的上下文参数 context-param 

  2、获取当前的工程路径，格式: /工程路径 

  3、获取工程部署后在服务器硬盘上的绝对路径 

  4、像 Map 一样存取数据

  ```java
  protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException { 
      // 1、获取 web.xml 中配置的上下文参数 context-param 
      ServletContext context = 
          getServletConfig().getServletContext(); 
      String username = 
          context.getInitParameter("username"); 
      System.out.println("context-param 参数 username 的值是:" + username); 
      System.out.println("context-param 参数 password 的值是:" + context.getInitParameter("password")); 
      
      // 2、获取当前的工程路径，格式: /工程路径
  
      System.out.println( "当前工程路径:" + context.getContextPath() ); 
      
      // 3、获取工程部署后在服务器硬盘上的绝对路径 
      /**
      * / 斜杠被服务器解析地址为:http://ip:port/工程名/ 映射到 IDEA 代码的 web 目录<br/> 
      */ 
      System.out.println("工程部署的路径是:" + context.getRealPath("/")); 
      System.out.println("工程下 css 目录的绝对路径是:" + context.getRealPath("/css")); 
      System.out.println("工程下 imgs 目录 1.jpg 的绝对路径是:" + context.getRealPath("/imgs/1.jpg")); }
  ```

  ```xml
  <!--context-param 是上下文参数(它属于整个 web 工程)--> <context-param> 
      <param-name>username</param-name>
      <param-value>context</param-value> 
  </context-param>
  <!--context-param 是上下文参数(它属于整个 web 工程)--> <context-param>
      <param-name>password</param-name> 
      <param-value>root</param-value> 
  </context-param>
  ```

  ServletContext 像 Map 一样存取数据： 

  ContextServlet1 代码：

  ```java
  public class ContextServlet1 extends HttpServlet {
      protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException { 
          // 获取 ServletContext 对象 
          ServletContext context = getServletContext(); 
          System.out.println(context); 
          System.out.println("保存之前: Context1 获取 key1 的值是:"+ context.getAttribute("key1")); 
          context.setAttribute("key1", "value1"); 
          System.out.println("Context1 中获取域数据 key1 的值是:"+ context.getAttribute("key1"));
      } 
  }
  ```

  ContextServlet2 代码：

  ```java
  protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException { 
      ServletContext context = getServletContext();
  
      System.out.println(context); 
      System.out.println("Context2 中获取域数据 key1 的值是:"+ context.getAttribute("key1")); // null
  }
  ```



### 4. **HTTP** **协议**

- **什么是** **HTTP** **协议** 

  什么是协议? 

  ​		协议是指双方，或多方，相互约定好，大家都需要遵守的规则，叫协议。 

  所谓 HTTP 协议，就是指，客户端和服务器之间通信时，发送的数据，需要遵守的规则，叫 HTTP 协议。 

  HTTP 协议中的数据又叫报文。

- **请求的** **HTTP** **协议格式** 

  客户端给服务器发送数据叫请求。 

  服务器给客户端回传数据叫响应。 

  请求又分为 GET 请求，和 POST 请求两种 

  **i. GET** **请求** 

  1、请求行 

  ​	(1) 请求的方式   											 GET 

  ​	(2) 请求的资源路径[+?+请求参数] 

  ​	(3) 请求的协议的版本号 								HTTP/1.1 

  2、请求头 

  ​	key : value 				组成不同的键值对，表示不同的含义。

  ![image-20211029140755699](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211029140755699.png)

  **ii. POST** **请求** 

  1、请求行

  ​	(1) 请求的方式										 POST 

  ​	(2) 请求的资源路径[+?+请求参数] 

  ​	(3) 请求的协议的版本号 						 HTTP/1.1 

  2、请求头

  ​	key : value      不同的请求头，有不同的含义 

  ​	空行

  3、请求体 ===>>> 就是发送给服务器的数据

  ![image-20211029141043126](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211029141043126.png)

  **iii.** **常用请求头的说明** 

  ​	Accept: 表示客户端可以接收的数据类型 

  ​	Accpet-Languege: 表示客户端可以接收的语言类型 

  ​	User-Agent: 表示客户端浏览器的信息 

  ​	Host： 表示请求时的服务器 ip 和端口号

  **iv.** **哪些是** **GET** **请求，哪些是** **POST** **请求** 

  GET 请求有哪些： 

  1. form 标签 method=get 

  2. a 标签 

  3. link 标签引入 css 

  4. Script 标签引入 js 文件 

  5. img 标签引入图片 

  6. iframe 引入 html 页面 

  7. 在浏览器地址栏中输入地址后敲回车 

  POST 请求有哪些： 

  8. form 标签 method=post

- **响应的** **HTTP** **协议格式** 

  1、响应行 

  ​	(1) 响应的协议和版本号 

  ​	(2) 响应状态码 

  ​	(3) 响应状态描述符 

  2、响应头 

  ​	(1) key : value   		不同的响应头，有其不同含义 

  ​	空行 

  3、响应体 	---->>> 		就是回传给客户端的数据

  ![image-20211029141622149](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211029141622149.png)

- **常用的响应码说明** 

  200 

  表示请求成功 

  302 

  表示请求重定向 

  404 

  表示请求服务器已经收到了，但是你要的数据不存在（请求地址错误） 

  500 

  表示服务器已经收到请求，但是服务器内部错误（代码错误）

- **MIME** **类型说明** 

  MIME 是 HTTP 协议中数据类型。 

  MIME 的英文全称是"Multipurpose Internet Mail Extensions" 多功能 Internet 邮件扩充服务。MIME 类型的格式是“大类型/小类型”，并与某一种文件的扩展名相对应。

  常见的 MIME 类型：

  ![image-20211029141939495](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211029141939495.png)

  ![image-20211029141947303](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211029141947303.png)

- 谷歌浏览器如何查看 HTTP 协议：

  ![image-20211029142105541](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211029142105541.png)

  

### 5. **HttpServletRequest** **类**

- **HttpServletRequest** **类有什么作用**

  每次只要有请求进入 Tomcat 服务器，Tomcat 服务器就会把请求过来的 HTTP 协议信息解析好封装到 Request 对象中。 然后传递到 service 方法（doGet 和 doPost）中给我们使用。我们可以通HttpServletRequest 对象，获取到所有请求的信息。

- **HttpServletRequest** **类的常用方法** 

  i. getRequestURI()   获取请求的资源路径 

  ii. getRequestURL() 获取请求的统一资源定位符（绝对路径） 

  iii. getRemoteHost() 获取客户端的 ip 地址 

  iv. getHeader() 获取请求头 

  v. getParameter() 获取请求的参数 

  vi. getParameterValues() 获取请求的参数（多个值的时候使用） 

  vii. getMethod() 获取请求的方式 GET 或 POST 

  viii. setAttribute(key, value); 设置域数据 

  ix. getAttribute(key); 获取域数据 

  x. getRequestDispatcher() 获取请求转发对象

  常用 API 示例代码：

  ```java
  public class RequestAPIServlet extends HttpServlet { 
      @Override 
      protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException { 
          // i.getRequestURI() 获取请求的资源路径 
          System.out.println("URI => " + req.getRequestURI()); 
          // ii.getRequestURL() 获取请求的统一资源定位符（绝对路径） 
          System.out.println("URL => " + req.getRequestURL());
  
          // iii.getRemoteHost() 获取客户端的 ip 地址 
          /**
          * 在 IDEA 中，使用 localhost 访问时，得到的客户端 ip 地址是 ===>>> 127.0.0.1<br/> 
          * 在 IDEA 中，使用 127.0.0.1 访问时，得到的客户端 ip 地址是 ===>>> 127.0.0.1<br/> 
          * 在 IDEA 中，使用 真实 ip 访问时，得到的客户端 ip 地址是 ===>>> 真实的客户端 ip 地址<br/> 
          */ 
          System.out.println("客户端 ip 地址 => " + req.getRemoteHost()); 
          // iv.getHeader() 获取请求头 
          System.out.println("请求头 User-Agent ==>> " + req.getHeader("User-Agent")); 
          // vii.getMethod() 获取请求的方式 GET 或 POST 
          System.out.println( "请求的方式 ==>> " + req.getMethod() ); 
      }
  }
  ```

- **如何获取请求参数**

  ```html
  <body> 
      <form action="http://localhost:8080/07_servlet/parameterServlet" method="get"> 
          用户名：<input type="text" name="username"><br/> 
          密码：<input type="password" name="password"><br/> 
          兴趣爱好：
          <input type="checkbox" name="hobby" value="cpp">C++ 
          <input type="checkbox" name="hobby" value="java">Java 
          <input type="checkbox" name="hobby" value="js">JavaScript<br/> 
          <input type="submit"> 
      </form> 
  </body>
  ```

  ```java
  public class ParameterServlet extends HttpServlet { 
      @Override 
      protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException { 
          // 获取请求参数 
          String username = 
              req.getParameter("username"); 
          String password = 
              req.getParameter("password"); 
          String[] hobby = 
              req.getParameterValues("hobby"); 
          System.out.println("用户名：" + username); 
          System.out.println("密码：" + password); 
          System.out.println("兴趣爱好：" + 
                             Arrays.asList(hobby));
      }
  }
  ```

  **doGet** **请求的中文乱码解决：**

  ```java
  // 获取请求参数 
  String username = req.getParameter("username"); 
  //1 先以 iso8859-1 进行编码 
  //2 再以 utf-8 进行解码 
  username = new String(username.getBytes("iso-8859-1"), "UTF-8");
  ```

- **POST** **请求的中文乱码解决**

  ```java
  @Override 
  protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException { 
      // 设置请求体的字符集为 UTF-8，从而解决 post 请求的中文乱码问题 
      req.setCharacterEncoding("UTF-8"); 
      System.out.println("-------------doPost------------"); 
      // 获取请求参数 
      String username = req.getParameter("username"); 
      String password = req.getParameter("password"); 
      String[] hobby = req.getParameterValues("hobby"); 
      System.out.println("用户名：" + username); 
      System.out.println("密码：" + password); 
      System.out.println("兴趣爱好：" + Arrays.asList(hobby)); 
  }
  ```

- **请求的转发** 

  什么是请求的转发? 

  请求转发是指，服务器收到请求后，从一次资源跳转到另一个资源的操作叫请求转发。

  ![image-20211029144140265](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211029144140265.png)

  Servlet1 代码：

  ```java
  public class Servlet1 extends HttpServlet { 
      @Override 
      protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
      
          // 获取请求的参数（办事的材料）查看 
          String username = 
              req.getParameter("username"); 
          System.out.println("在 Servlet1（柜台 1）中查看参数（材料）：" + username); 
          // 给材料 盖一个章，并传递到 Servlet2（柜台 2）去查看 
          req.setAttribute("key1","柜台 1 的章"); 
          // 问路：Servlet2（柜台 2）怎么走 
          /**
          * 请求转发必须要以斜杠打头，/ 斜杠表示地址为：http://ip:port/工程名/ , 映射到 IDEA 代码的 web 目录 <br/> 
          *
          */ 
          RequestDispatcher requestDispatcher = 
              req.getRequestDispatcher("/servlet2"); 
          // RequestDispatcher requestDispatcher = req.getRequestDispatcher("http://www.baidu.com"); 
          // 走向 Sevlet2（柜台 2） 
          requestDispatcher.forward(req,resp);
  
      } 
  }
  ```

  Servlet2 代码：

  ```java
  public class Servlet2 extends HttpServlet { 
      @Override 
      protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException { 
          // 获取请求的参数（办事的材料）查看 
          String username = 
              req.getParameter("username"); 
          System.out.println("在 Servlet2（柜台 2）中查看参数（材料）：" + username); 
          // 查看 柜台 1 是否有盖章 
          Object key1 = req.getAttribute("key1"); 
          System.out.println("柜台 1 是否有章：" + key1); 
          // 处理自己的业务 
          System.out.println("Servlet2 处理自己的业务 ");
      }
  }
  ```

- **base** **标签的作用**

  ![image-20211029144946236](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211029144946236.png)

  ```java
  <!DOCTYPE html> 
      <html lang="zh_CN"> 
      <head>
      <meta charset="UTF-8"> 
      <title>Title</title> 
      <!--base 标签设置页面相对路径工作时参照的地址 
      href 属性就是参数的地址值
      --> 
      <base href="http://localhost:8080/07_servlet/a/b/"> 
      </head> 
      <body> 这是 a 下的 b 下的 c.html 页面<br/> 
      <a href="../../index.html">跳回首页</a><br/> 
      </body> 
      </html>
  ```

- **Web** **中的相对路径和绝对路径** 

  在 javaWeb 中，路径分为相对路径和绝对路径两种： 

  相对路径是： 

  . 				  表示当前目录 

  .. 				 表示上一级目录 

  资源名 		表示当前目录/资源名 

  绝对路径： 	

  ​	http://ip:port/工程路径/资源路径 

  在实际开发中，路径都使用绝对路径，而不简单的使用相对路径。 

  ​	1、绝对路径 

  ​	2、base+相对

- **web** **中** **/** **斜杠的不同意义** 

  在 web 中 / 斜杠 是一种绝对路径。 

  / 斜杠 如果被浏览器解析，得到的地址是：http://ip:port/ 

  \<a href="/">斜杠\</a> 

  / 斜杠 如果被服务器解析，得到的地址是：http://ip:port/工程路径 

  ​	1、<**url-pattern**>/servlet1</**url-pattern**> 

  ​	2、servletContext.getRealPath(“/”); 

  ​	3、request.getRequestDispatcher(“/”); 

  特殊情况： response.sendRediect(“/”); 

  ​	把斜杠发送给浏览器解析。得到 http://ip:port/



### 6. **HttpServletResponse** **类**

- **HttpServletResponse** **类的作用** 

  HttpServletResponse 类和 HttpServletRequest 类一样。每次请求进来，Tomcat 服务器都会创建一个 Response 对象传递给 Servlet 程序去使用。HttpServletRequest 表示请求过来的信息，HttpServletResponse 表示所有响应的信息，我们如果需要设置返回给客户端的信息，都可以通过 HttpServletResponse 对象来进行设置;

- **两个输出流的说明** 

  字节流 	 getOutputStream(); 	常用于下载（传递二进制数据） 

  字符流 	 getWriter();  				  常用于回传字符串（常用） 

  两个流同时只能使用一个。 

  使用了字节流，就不能再使用字符流，反之亦然，否则就会报错。

- **如何往客户端回传数据**

  ```java
  public class ResponseIOServlet extends HttpServlet { 
      @Override 
      protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException { 
          // 要求 ： 往客户端回传 字符串 数据。 
          PrintWriter writer = resp.getWriter(); 
          writer.write("response's content!!!"); 
      }
  }
  ```

- **响应的乱码解决**

  ```java
  // 它会同时设置服务器和客户端都使用 UTF-8 字符集，还设置了响应头 
  // 此方法一定要在获取流对象之前调用才有效 
  resp.setContentType("text/html; charset=UTF-8");
  ```

- **请求重定向** 

  请求重定向，是指客户端给服务器发请求，然后服务器告诉客户端说。我给你一些地址。你去新地址访问。叫请求重定向（因为之前的地址可能已经被废弃）。

  ![image-20211029151749937](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211029151749937.png)

  - 请求重定向的第一种方案： 

    ​	*//* *设置响应状态码* *302* *，表示重定向，（已搬迁）* 

    ​	resp.setStatus(302); 

    ​	*//* *设置响应头，说明 新的地址在哪里* 

    ​	resp.setHeader(**"Location"**, **"http://localhost:8080"**); 

  - 请求重定向的第二种方案（推荐使用）： 

    ​	resp.sendRedirect(**"http://localhost:8080"**);

  

### 7. 书城项目重点笔记

- **JavaEE** **项目的三层架构**

  ![image-20211030201331426](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211030201331426.png)

  分层的目的是为了解耦。解耦就是为了降低代码的耦合度。方便项目后期的维护和升级。

- **IDEA** **中** **Debug** **调试的使用**

  - **Debug** **调试代码，首先需要两个元素：断点** **+ Debug** **启动服务器** 

    1、断点，只需要在代码需要停的行的左边上单击，就可以添加和取消 

    2、Debug 启动 Tomcat 运行代码

  - **测试工具栏：**

    ![image-20211030201604961](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211030201604961.png)

    ![image-20211030201612886](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211030201612886.png)

  - **变量窗口**

    变量窗口：它可以查看当前方法范围内所有有效的变量。

    ![image-20211030201641227](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211030201641227.png)

  - **方法调用栈窗口** 

    1、方法调用栈可以查看当前线程有哪些方法调用信息 

    2、下面的调用上一行的方法

    ![image-20211030201658442](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211030201658442.png)

  - **其他常用调试相关按钮：**

    ![image-20211030201733866](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211030201733866.png)




- **MVC** **概念** 

  MVC 全称：Model 模型、 View 视图、 Controller 控制器。 

  MVC 最早出现在 JavaEE 三层中的 Web 层，它可以有效的指导 Web 层的代码如何有效分离，单独工作。 

  View 视图：只负责数据和界面的显示，不接受任何与显示数据无关的代码，便于程序员和美工的分工合作—— JSP/HTML。

  Controller 控制器：只负责接收请求，调用业务层的代码处理请求，然后派发页面，是一个“调度者”的角色——Servlet。 转到某个页面。或者是重定向到某个页面。 

  Model 模型：将与业务逻辑相关的数据封装为具体的 JavaBean 类，其中不掺杂任何与数据处理相关的代码—— JavaBean/domain/entity/pojo。 

  **MVC** **是一种思想** 

  MVC 的理念是将软件代码拆分成为组件，单独开发，组合使用（**目的还是为了降低耦合度**）。

  ![image-20211102161311187](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211102161311187.png)



- **表单重复提交之-----验证码** 

  表单重复提交有三种常见的情况： 

  一：提交完表单。服务器使用请求转发来进行页面跳转。这个时候，用户按下功能键 F5，就会发起最后一次的请求。 

  造成表单重复提交问题。解决方法：使用重定向来进行跳转 

  二：用户正常提交服务器，但是由于网络延迟等原因，迟迟未收到服务器的响应，这个时候，用户以为提交失败，就会着急，然后多点了几次提交操作，也会造成表单重复提交。 

  三：用户正常提交服务器。服务器也没有延迟，但是提交完成后，用户回退浏览器。重新提交。也会造成表单重复提交。

  ![image-20211104215158355](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211104215158355.png)

- **谷歌** **kaptcha** **图片验证码的使用** 

  谷歌验证码 kaptcha 使用步骤如下： 

  ​	1、导入谷歌验证码的 jar 包 

  ​					kaptcha-2.3.2.jar

  ​	2、在 web.xml 中去配置用于生成验证码的 Servlet 程序

  ```xml
  <servlet> 
      <servlet-name>KaptchaServlet</servlet-name> <servlet-class>com.google.code.kaptcha.servlet.KaptchaServlet</servlet-class> 
  </servlet>
  <servlet-mapping> 
      <servlet-name>KaptchaServlet</servlet-name> 
      <url-pattern>/kaptcha.jpg</url-pattern> 
  </servlet-mapping>
  ```

  ​	3、在表单中使用 img 标签去显示验证码图片并使用它

  ```jsp
  <form action="http://localhost:8080/tmp/registServlet" method="get"> 
      用户名：<input type="text" name="username" > <br> 
      验证码：<input type="text" style="width: 80px;" name="code"> 
      <img src="http://localhost:8080/tmp/kaptcha.jpg" alt="" style="width: 100px; height: 28px;"> <br> 
      <input type="submit" value="登录"> 
  </form>
  ```

  ​	4、在服务器获取谷歌生成的验证码和客户端发送过来的验证码比较使用。	

  ```java
  @Override 
  protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException { 
      // 获取 Session 中的验证码 
      String token = (String) req.getSession().getAttribute(KAPTCHA_SESSION_KEY); 
      // 删除 Session 中的验证码 
      req.getSession().removeAttribute(KAPTCHA_SESSION_KEY); 
      String code = req.getParameter("code"); 
      // 获取用户名 
      String username = req.getParameter("username"); 
      if (token != null && token.equalsIgnoreCase(code)) { 
          System.out.println("保存到数据库：" + username); 
          resp.sendRedirect(req.getContextPath() + "/ok.jsp"); 
      } else { 
          System.out.println("请不要重复提交表单"); 
      }
  }
  ```

  切换验证码：

  ```javascript
  // 给验证码的图片，绑定单击事件 
  $("#code_img").click(function () { 
      // 在事件响应的 function 函数中有一个 this 对象。这个 this 对象，是当前正在响应事件的 dom 对象 
      // src 属性表示验证码 img 标签的 图片路径。它可读，可写 
      // alert(this.src); 
      this.src = "${basePath}kaptcha.jpg?d=" + new Date(); 
  });
  ```




- **注意很重要！！！！！**

  - ```java
    //超级重要：数据库表中的列名一定要和相应实体类的属性名对应，不然会出现数据库能查到数据，
    // 而Java这边查不到（老韩有讲过原理，底层会通过数据库表的列名去调用实体类的getXXX()方法，
    // 如果两边名称不一样就调用不到，则为NULL）
    ```



## 第七章 jsp

### 1. **什么是** jsp，它有什么用?

​	jsp 的全称是 java server pages。Java 的服务器页面。 

​	jsp 的主要作用是代替 Servlet 程序回传 html 页面的数据。 

​	因为 Servlet 程序回传 html 页面数据是一件非常繁锁的事情。开发成本和维护成本都极高。

Servlet 回传 html 页面数据的代码：

```java
public class PringHtml extends HttpServlet { 
    @Override protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException { 
        // 通过响应的回传流回传 html 页面数据 
        resp.setContentType("text/html; charset=UTF-8"); 
        PrintWriter writer = resp.getWriter(); 
        writer.write("<!DOCTYPE html>\r\n"); 
        writer.write(" <html lang=\"en\">\r\n"); 
        writer.write(" <head>\r\n"); 
        writer.write(" <meta charset=\"UTF-8\">\r\n"); 
        writer.write(" <title>Title</title>\r\n"); 
        writer.write(" </head>\r\n"); 
        writer.write(" <body>\r\n");
        writer.write(" 这是 html 页面数据 \r\n"); 
        writer.write(" </body>\r\n"); 
        writer.write("</html>\r\n"); 
        writer.write("\r\n"); 
    } 
}
```

jsp 回传一个简单 html 页面的代码： 

```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %> 
<html> 
    <head> 
        <title>Title</title> 
    </head> 
    <body> 这是 html 页面数据 </body> 
</html>
```

### 2. **jsp** **的本质是什么。** 

jsp 页面本质上是一个 Servlet 程序。 

当我们第一次访问 jsp 页面的时候。Tomcat 服务器会帮我们把 jsp 页面翻译成为一个 java 源文件。并且对它进行编译成为.class 字节码程序。我们打开 java 源文件不难发现其里面的内容是：

![image-20211031155749726](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211031155749726.png)

我们跟踪原代码发现，HttpJspBase 类。它直接地继承了 HttpServlet 类。也就是说。jsp 翻译出来的 java 类，它间接了继承了 HttpServlet 类。也就是说，翻译出来的是一个 Servlet 程序

![image-20211031155810364](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211031155810364.png)

**总结**：通过翻译的 java 源代码我们就可以得到结果：jsp 就是 Servlet 程序。 

大家也可以去观察翻译出来的 Servlet 程序的源代码，不难发现。其底层实现，也是通过输出流。把 html 页面数据回传给客户端。



### 3.**jsp** **的三种语法** 

#### 1. **jsp** **头部的** **page** **指令**

jsp 的 page 指令可以修改 jsp 页面中一些重要的属性，或者行为。

![image-20211031155902529](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211031155902529.png)

![image-20211031155929373](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211031155929373.png)

![image-20211031155935604](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211031155935604.png)

#### 2. **jsp** **中的常用脚本** 

- **声明脚本(极少使用)** 

声明脚本的格式是： **<%!** 声明 java 代码 **%>** 

作用：可以给 jsp 翻译出来的 java 类定义属性和方法甚至是静态代码块。内部类等。 

练习：

1、声明类属性 

2、声明 static 静态代码块 

3、声明类方法 

4、声明内部类

声明脚本代码翻译对照：

![image-20211031160137723](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211031160137723.png)


- **表达式脚本（常用）** 

  表达式脚本的格式是：**<%=**表达式**%>** 

  表达式脚本的作用是： jsp 页面上输出数据。 

  表达式脚本的特点： 

  ​	1、所有的表达式脚本都会被翻译到_jspService() 方法中 

  ​	2、表达式脚本都会被翻译成为 out.print()输出到页面上 

  ​	3、由于表达式脚本翻译的内容都在_jspService() 方法中,所以_jspService()方法中的对象都可以直接使用。 

  ​	4、表达式脚本中的表达式不能以分号结束。

  练习：

  1. 输出整型 

  2. 输出浮点型 

  3. 输出字符串 

  4. 输出对象

     ```jsp
     <%=12 %> <br>
     <%=12.12 %> <br> 
     <%="我是字符串" %> <br> 
     <%=map%> <br> <%=request.getParameter("username")%>
     ```

     

- **代码脚本** 

  代码脚本的格式是： 

  **<%** 

  ​	java 语句 

  **%>** 

  代码脚本的作用是：可以在 jsp 页面中，编写我们自己需要的功能（写的是 java 语句）。 

  代码脚本的特点是： 

  ​	1、代码脚本翻译之后都在_jspService 方法中 

  ​	2、代码脚本由于翻译到_jspService()方法中，所以在_jspService()方法中的现有对象都可以直接使用。 

  ​	3、还可以由多个代码脚本块组合完成一个完整的 java 语句。 

  ​	4、代码脚本还可以和表达式脚本一起组合使用，在 jsp 页面上输出数据 

  练习：

  1. 代码脚本----if 语句 

  2. 代码脚本----for 循环语句 

  3. 翻译后 java 文件中_jspService 方法内的代码都可以写

  ```jsp
  <%--练习：--%> 
  <%--1.代码脚本----if 语句--%> 
  <%
  	int i = 13 ; 
  	if (i == 12) { 
  %> 
  <h1>国哥好帅</h1> 
  <% 
  	} else { 
  %> 
  <h1>国哥又骗人了！</h1> 
  <% 
  	} 
  %> 
  <br>
  
  <%--2.代码脚本----for 循环语句--%> 
  <table border="1" cellspacing="0"> 
      <% 
      	for (int j = 0; j < 10; j++) { 
      %> 
      	<tr>
              <td>第 <%=j + 1%>行</td> 
      	</tr> 
      <% 
      	} 
      %>
  </table> 
  
  <%--3.翻译后 java 文件中_jspService 方法内的代码都可以写--%> 
  <% 
      String username = request.getParameter("username"); 		
  	System.out.println("用户名的请求参数值是：" + username); 
  %>
  ```


#### 3. **jsp** **中的三种注释** 

- **html** **注释** 

  *<!--* *这是* *html* *注释* *-->*

  html 注释会被翻译到 java 源代码中。在_jspService 方法里，以 out.writer 输出到客户端。

- **java** **注释**

  **<%** 

  *//* *单行* *java* *注释* 

  */** *多行* *java* *注释* **/* 

  **%>**

  java 注释会被翻译到 java 源代码中。

- **jsp** **注释**

  *<%--* *这是* *jsp* *注释* *--%>* 

  jsp 注释可以注掉，jsp 页面中所有代码。

  

### 4. **jsp** **九大内置对象** 

jsp 中的内置对象，是指 Tomcat 在翻译 jsp 页面成为 Servlet 源代码后，内部提供的九大对象，叫内置对象。

![image-20211031161156933](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211031161156933.png)



### 5. **jsp** **四大域对象**

![image-20211031161458591](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211031161458591.png)



### 6. **jsp** **中的** **out** **输出和** **response.getWriter** **输出的区** 别

response 中表示响应，我们经常用于设置返回给客户端的内容（输出） 

out 也是给用户做输出使用的。

![image-20211031161623602](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211031161623602.png)

由于 jsp 翻译之后，底层源代码都是使用 out 来进行输出，所以一般情况下。我们在 jsp 页面中**统一使用 out 来进行输出**。避免打乱页面输出内容的顺序。 

​	out.write() 输出字符串没有问题 

​	out.print() 输出任意数据都没有问题（都转换成为字符串后调用的 write 输出） 

深入源码，浅出结论：**在 jsp 页面中，可以统一使用 out.print()来进行输出**

### 7.**jsp** **的常用标签**

- **jsp** **静态包含** 

  示例说明： 

  *<%--*

  ​	*<%@ include file=""%>* *就是静态包含* 

  ​		*file* *属性指定你要包含的* *jsp* *页面的路径* 

  ​		*地址中第一个斜杠* */* *表示为* *http://ip:port/*工程路径*/* *映射到代码的* *web* *目录* 

  *静态包含的特点：* 

  ​	1、静态包含不会翻译被包含的 *jsp* *页面。* 

  ​	2、静态包含其实是把被包含的*jsp* *页面的代码拷贝到包含的位置执行输出。*

  *--%>*

- **jsp** **动态包含**

  ![image-20211031162245064](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211031162245064.png)

  ![image-20211031162320207](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211031162320207.png)

- **jsp** **标签-转发**

  ![image-20211031162454262](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211031162454262.png)

### 8. **什么是** **Listener** **监听器？** 

1、Listener 监听器它是 JavaWeb 的三大组件之一。JavaWeb 的三大组件分别是：Servlet 程序、Filter 过滤器、Listener 监听器。

2、Listener 它是 JavaEE 的规范，就是接口 

3、监听器的作用是，监听某种事物的变化。然后通过回调函数，反馈给客户（程序）去做一些相应的处理。



- **ServletContextListener** **监听器** 

  ServletContextListener 它可以监听 ServletContext 对象的创建和销毁。 

  ServletContext 对象在 web 工程启动的时候创建，在 web 工程停止的时候销毁。 

  监听到创建和销毁之后都会分别调用 ServletContextListener 监听器的方法反馈。

  ![image-20211031163024261](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211031163024261.png)

  如何使用 ServletContextListener 监听器监听 ServletContext 对象。 

  使用步骤如下： 

  1、编写一个类去实现 ServletContextListener 

  2、实现其两个回调方法 

  3、到 web.xml 中去配置监听器

  监听器实现类：

  ```java
  public class MyServletContextListenerImpl implements ServletContextListener {
      @Override 
      public void contextInitialized(ServletContextEvent sce) { 		
          System.out.println("ServletContext 对象被创建了"); }
      @Override 
      public void contextDestroyed(ServletContextEvent sce) { 
          System.out.println("ServletContext 对象被销毁了"); 
      } 
  }
  ```

  web.xml 中的配置：

  ```xml
  <!--配置监听器--> 
  <listener> 
      <listener-class>com.atguigu.listener.MyServletContextListenerImpl</listener-class>
  </listener>
  ```



## 第八章 EL表达式 & JSTL标签库 & 文件的上传和下载

### 1. **EL** **表达式**

#### 1. **什么是** **EL** **表达式，EL 表达式的作用?** 

EL 表达式的全称是：Expression  Language。是表达式语言。 

EL 表达式的什么作用：EL 表达式主要是**代替 jsp 页面中的表达式脚本在 jsp 页面中进行数据的输出。** 

因为 EL 表达式在输出数据的时候，要比 jsp 的表达式脚本要简洁很多。

```jsp
<body> 
    <% 
    	request.setAttribute("key","值"); 
    %>
    表达式脚本输出 key 的值是： <%=request.getAttribute("key1")==null?"":request.getAttribute("key1")%><br/> 
    EL 表达式输出 key 的值是：${key1} 
</body>
```

EL 表达式的格式是：${表达式} 

EL 表达式在输出 null 值的时候，输出的是空串。jsp 表达式脚本输出 null 值的时候，输出的是 null 字符串.

#### 2. **EL** **表达式搜索域数据的顺序** 

EL 表达式主要是在 jsp 页面中输出数据。 

主要是输出域对象中的数据。 

当四个域中都有相同的 key 的数据的时候，EL 表达式会按照四个域的从小到大的顺序去进行搜索，找到就输出。

#### 3. **EL** **表达式输出** **Bean** **的普通属性，数组属性。List** **集**合属性，map 集合属性

- 需求——输出 Person 类中普通属性，数组属性。list 集合属性和 map 集合属性。

  ```java
  public class Person { 
      // i.需求——输出 Person 类中普通属性，数组属性。list 集合属性和 map 集合属性。
      private String name; 
      private String[] phones; 
      private List<String> cities;
      private Map<String,Object> map;
      public int getAge() { 
          return 18; 
      }
  } 
  ```

  ```jsp
  <body> 
      <% 
      	Person person = new Person(); 
  		person.setName("国哥好帅！"); 		
  		person.setPhones(new String[]		{"18610541354","18688886666","18699998888"}); 	
  		List<String> cities = new ArrayList<String>(); 
          cities.add("北京"); 
          cities.add("上海"); 
          cities.add("深圳"); 
          person.setCities(cities); 
          Map<String,Object>map = new HashMap<>(); 
          map.put("key1","value1"); 
          map.put("key2","value2"); 
          map.put("key3","value3"); 
          person.setMap(map);
  
          pageContext.setAttribute("p", person); 
      %>
      
      输出 Person：${ p }<br/> 
      输出 Person 的 name 属性：${p.name} <br> 
      输出 Person 的 pnones 数组属性值：${p.phones[2]} <br> 
      输出 Person 的 cities 集合中的元素值：${p.cities} <br> 
      输出 Person 的 List 集合中个别元素值：${p.cities[2]} <br> 
      输出 Person 的 Map 集合: ${p.map} <br> 
      输出 Person 的 Map 集合中某个 key 的值: ${p.map.key3} <br> 
      输出 Person 的 age 属性：${p.age} <br>
  </body>  
  ```

#### 4. **EL** **表达式——运算** 

语法：${ 运算表达式 } ， EL 表达式支持如下运算符：

![image-20211031164624071](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211031164624071.png)

![image-20211031164642345](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211031164642345.png)

![image-20211031164649176](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211031164649176.png)

- **empty** **运算** 

  empty 运算可以判断一个数据是否为空，如果为空，则输出 true,不为空输出 false。 

  以下几种情况为空： 

  1、值为 null 值的时候，为空 

  2、值为空串的时候，为空 

  3、值是 Object 类型数组，长度为零的时候 

  4、list 集合，元素个数为零 

  5、map 集合，元素个数为零

- **三元运算** 

  表达式 1？表达式 2：表达式 3 

  如果表达式 1 的值为真，返回表达式 2 的值，如果表达式 1 的值为假，返回表达式 3 的值。

- **“.”点运算 和** **[]** **中括号运算符** 

  . 点运算，可以输出 Bean 对象中某个属性的值。 

  []中括号运算，可以输出有序集合中某个元素的值。 

  并且[]中括号运算，还可以输出 map 集合中 key 里含有特殊字符的 key 的值。

  ```jsp
  <body> 
      <% 
      Map<String,Object> map = new HashMap<String, Object>(); 
      map.put("a.a.a", "aaaValue"); 
      map.put("b+b+b", "bbbValue"); 
      map.put("c-c-c", "cccValue"); 
      request.setAttribute("map", map); 
      %> 
      
      ${ map['a.a.a'] } <br> 
      ${ map["b+b+b"] } <br> 
      ${ map['c-c-c'] } <br>
  </body>
  ```

#### 5. **EL** **表达式的** **11** **个隐含对象** 

EL 个达式中 11 个隐含对象，是 EL 表达式中自己定义的，可以直接使用。

![image-20211031165312475](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211031165312475.png)

![image-20211031165323102](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211031165323102.png)

![image-20211031165557865](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211031165557865.png)

![image-20211031165632309](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211031165632309.png)

![image-20211031165649215](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211031165649215.png)

![image-20211031170050511](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211031170050511.png)

![image-20211031170119655](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211031170119655.png)

![image-20211031170129203](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211031170129203.png)



### 2. **JSTL** **标签库**

JSTL 标签库 全称是指 JSP Standard Tag Library JSP 标准标签库。是一个不断完善的开放源代码的 JSP 标签库。

**EL 表达式主要是为了替换 jsp 中的表达式脚本**，**而标签库则是为了替换代码脚本。这样使得整个 jsp 页面变得更佳简洁**。

![image-20211031170436261](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211031170436261.png)

在 jsp 标签库中使用 taglib 指令引入标签库 

CORE 标签库 

<%@ taglib prefix=*"c"* uri=*"http://java.sun.com/jsp/jstl/core"* %> 

XML 标签库

<%@ taglib prefix=*"x"* uri=*"http://java.sun.com/jsp/jstl/xml"* %> 

FMT 标签库 

<%@ taglib prefix=*"fmt"* uri=*"http://java.sun.com/jsp/jstl/fmt"* %> 

SQL 标签库 

<%@ taglib prefix=*"sql"* uri=*"http://java.sun.com/jsp/jstl/sql"* %> 

FUNCTIONS 标签库 

<%@ taglib prefix=*"fn"* uri=*"http://java.sun.com/jsp/jstl/functions"* %>

#### 1. **JSTL** **标签库的使用步骤** 

1、先导入 jstl 标签库的 jar 包。 

​	taglibs-standard-impl-1.2.1.jar 

​	taglibs-standard-spec-1.2.1.jar 

2、第二步，使用 taglib 指令引入标签库。

<%@ taglib prefix=*"c"* uri=*"http://java.sun.com/jsp/jstl/core"* %> 

#### 2. **core** **核心库使用**

![image-20211031170834362](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211031170834362.png)

![image-20211031170849881](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211031170849881.png)

![image-20211031171004271](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211031171004271.png)

![image-20211031171145073](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211031171145073.png)

![image-20211031171212782](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211031171212782.png)

![image-20211031171411213](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211031171411213.png)

![image-20211031171421858](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211031171421858.png)

![image-20211031171744170](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211031171744170.png)

![image-20211031171754093](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211031171754093.png)

### 3. **文件的上传和下载**

#### 1. **文件的上传介绍（重点）**

1、要有一个 form 标签，method=post 请求 

2、form 标签的 encType 属性值必须为 multipart/form-data 值 

3、在 form 标签中使用 input type=file 添加上传的文件 

4、编写服务器代码（Servlet 程序）接收，处理上传的数据。

 

encType=multipart/form-data 表示提交的数据，以多段（每一个表单项一个数据段）的形式进行拼接，然后以二进制流的形式发送给服务器；

- **文件上传，HTTP** **协议的说明。**

  ![image-20211031173506975](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211031173506975.png)

- **commons-fileupload.jar** **常用** **API** **介绍说明**

  ![image-20211031173550997](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211031173550997.png)

  ![image-20211031173556738](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211031173556738.png)

- **fileupload** **类库的使用：**

  ![image-20211031174314593](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211031174314593.png)

  ![image-20211031174327836](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211031174327836.png)

  

#### 2. **文件下载**

- **下载的常用** **API** **说明：** 

  response.getOutputStream(); 

  servletContext.getResourceAsStream(); 

  servletContext.getMimeType(); 

  response.setContentType(); 

  

  response.setHeader("Content-Disposition", "attachment; fileName=1.jpg"); 

  这个响应头告诉浏览器。这是需要下载的。而 attachment 表示附件，也就是下载的一个文件。fileName=后面， 表示下载的文件名。 

  完成上面的两个步骤，下载文件是没问题了。但是如果我们要下载的文件是中文名的话。你会发现，下载无法正确显示出正确的中文名。 

  原因是在响应头中，不能包含有中文字符，只能包含 ASCII 码。

  ![image-20211031175315615](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211031175315615.png)

- **附件中文名乱码问题解决方案：**

  ![image-20211031180153906](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211031180153906.png)

  ![image-20211031180213100](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211031180213100.png)

  **因为火狐使用的是** **BASE64** **的编解码方式还原响应中的汉字。所以需要使用** **BASE64Encoder** **类进行编码操作。**

  ![image-20211031180517705](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211031180517705.png)

  

  

## 第九章 **Cookie** **和** **Session**

### 1. **Cookie**

- **什么是** **Cookie?** 

  1、Cookie 翻译过来是饼干的意思。 

  2、**Cookie 是服务器通知客户端保存键值对的一种技术**。 

  3、客户端有了 Cookie 后，每次请求都发送给服务器。 

  4、每个 Cookie 的大小不能超过 4kB

- **如何创建** **Cookie**

  ![image-20211104190657001](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211104190657001.png)

  ```java
  protected void createCookie(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException { 
      //1 创建 Cookie 对象
      Cookie cookie = new Cookie("key4", "value4"); 
      //2 通知客户端保存 Cookie 
      resp.addCookie(cookie); 
      
      //1 创建 Cookie 对象 
      Cookie cookie1 = new Cookie("key5", "value5"); 
      //2 通知客户端保存 Cookie 
      resp.addCookie(cookie1); 
      
      resp.getWriter().write("Cookie 创建成功"); }
  ```

  

- **服务器如何获取** **Cookie** 

  服务器获取客户端的 Cookie 只需要一行代码：req.getCookies():Cookie[]

  ![image-20211104191052924](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211104191052924.png)

  ```java
  //Cookie 的工具类：
  public class CookieUtils { 
      /**
      * 查找指定名称的 Cookie 对象 
      * @param name 
      * @param cookies 
      * @return
      */ 
      public static Cookie findCookie(String name , Cookie[] cookies){ 
          if (name == null || cookies == null || cookies.length == 0) {
              return null; 
          }
          for (Cookie cookie : cookies) { 
              if (name.equals(cookie.getName())) { 
                  return cookie;
              } 
          }
          return null; 
      } 
  }
  ```

  ```java
  //Servlet 程序中的代码：
  protected void getCookie(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException { 
      Cookie[] cookies = req.getCookies(); 
      for (Cookie cookie : cookies) { 
          // getName 方法返回 Cookie 的 key（名） 
          // getValue 方法返回 Cookie 的 value 值 
          resp.getWriter().write("Cookie[" + cookie.getName() + "=" + cookie.getValue() + "] <br/>"); 
      }
      
      Cookie iWantCookie = 
          CookieUtils.findCookie("key1", cookies); 
      // for (Cookie cookie : cookies) { 
      // if ("key2".equals(cookie.getName())) { 
      // iWantCookie = cookie; 
      // break; 
      // } 
      // } 
      
      // 如果不等于 null，说明赋过值，也就是找到了需要的 Cookie 
      if (iWantCookie != null) { 
          resp.getWriter().write("找到了需要的 Cookie");
      } 
  }
  ```

- **Cookie** **值的修改** 

  方案一： 

  1、先创建一个要修改的同名（指的就是 key）的 Cookie 对象 

  2、在构造器，同时赋于新的 Cookie 值。 

  3、调用 response.addCookie( Cookie );

  方案二： 

  1、先查找到需要修改的 Cookie 对象 

  2、调用 setValue()方法赋于新的 Cookie 值。 

  3、调用 response.addCookie()通知客户端保存修改

- **浏览器查看 Cookie**：

  **谷歌浏览器如何查看Cookie：**

  ![image-20211104191837262](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211104191837262.png)

  **火狐浏览器如何查看Cookie：**

  ![image-20211104191904750](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211104191904750.png)

  

- **Cookie** **生命控制** 

  Cookie 的生命控制指的是如何管理 Cookie 什么时候被销毁（删除） 

  

  setMaxAge() 

  ​	正数，表示在指定的秒数后过期 

  ​	负数，表示浏览器一关，Cookie 就会被删除（默认值是-1） 

  ​	零，表示马上删除 Cookie

  ```java
  /**
  * 设置存活 1 个小时的 Cooie 
  * @param req 
  * @param resp 
  * @throws ServletException
  * @throws IOException 
  */
  protected void life3600(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException { 
      Cookie cookie = new Cookie("life3600", "life3600"); 
      cookie.setMaxAge(60 * 60); 
      // 设置 Cookie 一小时之后被删除。无效 
      resp.addCookie(cookie); 
      resp.getWriter().write("已经创建了一个存活一小时的 Cookie"); 
  }
  
  /**
  * 马上删除一个 Cookie
  * @param req
  * @param resp
  * @throws ServletException 
  * @throws IOException 
  */ 
  protected void deleteNow(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
  
      // 先找到你要删除的 Cookie 对象 
      Cookie cookie = CookieUtils.findCookie("key4", req.getCookies()); 
      if (cookie != null) { 
          // 调用 setMaxAge(0); 
          cookie.setMaxAge(0); 
          // 表示马上删除，都不需要等待浏览器关闭 
          // 调用 response.addCookie(cookie); 
          resp.addCookie(cookie); 
          resp.getWriter().write("key4 的 Cookie 已经被删除");
      } 
  }
  /**
  * 默认的会话级别的 Cookie
  * @param req 
  * @param resp
  * @throws ServletException 
  * @throws IOException 
  */ 
  protected void defaultLife(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException { 
      Cookie cookie = new 
          Cookie("defalutLife","defaultLife"); 
      cookie.setMaxAge(-1); //设置存活时间 
      resp.addCookie(cookie);
  }
  ```

- **Cookie** **有效路径** **Path** **的设置** 

  Cookie 的 path 属性可以有效的过滤哪些 Cookie 可以发送给服务器。哪些不发。 

  path 属性是通过请求的地址来进行有效的过滤。 

  CookieA 			path=/工程路径 

  CookieB 			path=/工程路径/abc

  

  请求地址如下： 

  http://ip:port/工程路径/a.html 

  ​	CookieA 发送 

  ​	CookieB 不发送 

  http://ip:port/工程路径/abc/a.html 

  ​	CookieA 发送 

  ​	CookieB 发送

  ```java
  protected void testPath(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
  
      Cookie cookie = new Cookie("path1", "path1"); 
      // getContextPath() ===>>>> 得到工程路径 
      cookie.setPath( req.getContextPath() + "/abc" ); // ===>>>> /工程路径/abc
      resp.addCookie(cookie); 
      resp.getWriter().write("创建了一个带有 Path 路径的 Cookie");
  }
  ```

  

- **Cookie** **练习---免输入用户名登录**

  ![image-20211104192628034](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211104192628034.png)

  ```jsp
  <%--login.jsp 页面--%>
  <form action="http://localhost:8080/13_cookie_session/loginServlet" method="get"> 
      用户名：<input type="text" name="username" value="${cookie.username.value}"> <br>
      密码：<input type="password" name="password"> <br> 
      <input type="submit" value="登录"> 
  </form> 
  ```

  ```java
  //LoginServlet 程序： 
  
  @Override
  protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException { 
      String username = req.getParameter("username"); 
      String password = req.getParameter("password");
      if ("wzg168".equals(username) && 
          "123456".equals(password)) { 
          //登录 成功 
          Cookie cookie = new Cookie("username", username); 
          cookie.setMaxAge(60 * 60 * 24 * 7);//当前 Cookie 一周内有效 
          resp.addCookie(cookie); 
          System.out.println("登录 成功");
      } else {
          // 登录 失败 
          System.out.println("登录 失败"); 
      } 
  }
  ```

  

### 2. **Session** **会话**

- **什么是** **Session** **会话?** 

  1、Session 就一个接口（HttpSession）。 

  2、Session 就是会话。它是用来维护一个客户端和服务器之间关联的一种技术。 

  3、**每个客户端都有自己的一个 Session 会话。** 

  4、Session 会话中，我们经常用来保存用户登录之后的信息。

- **如何创建** **Session** **和获取(id 号,是否为新)** 

  如何创建和获取 Session。它们的 API 是一样的。 

  request.getSession() 

  ​		第一次调用是：创建 Session 会话 

  ​		之后调用都是：获取前面创建好的 Session 会话对象。 

  isNew(); 判断到底是不是刚创建出来的（新的） 

  ​		true 表示刚创建 

  ​		false 表示获取之前创建 

  每个会话都有一个身份证号。也就是 ID 值。而且这个 ID 是唯一的。 

  getId() 得到 Session 的会话 id 值。

- **Session** **域数据的存取**

  ```java
  /**
  * 往 Session 中保存数据 
  * @param req
  * @param resp
  * @throws ServletException 
  * @throws IOException 
  */ 
  protected void setAttribute(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException { 
      req.getSession().setAttribute("key1", "value1"); 
      resp.getWriter().write("已经往 Session 中保存了数据"); }
  
  /**
  * 获取 Session 域中的数据
  * @param req 
  * @param resp 
  * @throws ServletException
  * @throws IOException 
  */ 
  protected void getAttribute(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException { 
      Object attribute = 
          req.getSession().getAttribute("key1"); 
      resp.getWriter().write("从 Session 中获取出 key1 的数据是：" + attribute);
  }
  ```

- **Session** **生命周期控制** 

  public void setMaxInactiveInterval(int interval) 设置 Session 的超时时间（以秒为单位），超过指定的时长，Session 就会被销毁。

  ​			值为正数的时候，设定 Session 的超时时长。 

  ​			负数表示永不超时（极少使用） 

  public int getMaxInactiveInterval()  获取 Session 的超时时间 

  public void invalidate()   让当前 Session 会话马上超时无效。 

  

  Session 默认的超时时长是多少！ 

  ​			Session 默认的超时时间长为 30 分钟。 

  ​			因为在 Tomcat 服务器的配置文件 web.xml中默认有以下的配置，它就表示配置了当前 Tomcat 服务器下所有的 Session 超时配置默认时长为：30 分钟。 

  ​	\<session-config> 

  ​		\<session-timeout>30\</session-timeout> 

  ​	\</session-config>

  如果说。你希望你的 web 工程，默认的 Session 的超时时长为其他时长。你可以在你自己的 web.xml 配置文件中做以上相同的配置。就可以修改你的 web 工程所有 Seession 的默认超时时长。

  ```xml
  <!--表示当前 web 工程。创建出来 的所有 Session 默认是 20 分钟 超时时长--> 
  <session-config> 
      session-timeout>20</session-timeout> 
  </session-config>
  ```

  如果你想只修改个别 Session 的超时时长。就可以使用上面的 API。setMaxInactiveInterval(int interval)来进行单独的设置。session.setMaxInactiveInterval(int interval)单独设置超时时长。

  ```java
  protected void life3(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException { 
      // 先获取 Session 对象 
      HttpSession session = req.getSession(); 
      // 设置当前 Session 3 秒后超时 
      session.setMaxInactiveInterval(3); 
      resp.getWriter().write("当前 Session 已经设置为 3 秒后超时"); 
  }
  
  //Session 马上被超时示例：
  protected void deleteNow(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException { 
      // 先获取 Session 对象 
      HttpSession session = req.getSession(); 
      // 让 Session 会话马上超时 
      session.invalidate(); 
      resp.getWriter().write("Session 已经设置为超时（无效）"); 
  }
  ```

- **浏览器和** **Session** **之间关联的技术内幕** 

  Session 技术，底层其实是基于 Cookie 技术来实现的。

  <img src="E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211104195350955.png" alt="image-20211104195350955" style="zoom:200%;" />

  

## 第十章  **Filter** **过滤器**

### 1. **Filter**  **什么是过滤器** 

​	1、Filter 过滤器它是 JavaWeb 的三大组件之一。三大组件分别是：Servlet 程序、Listener 监听器、Filter 过滤器 

​	2、Filter 过滤器它是 JavaEE 的规范。也就是接口 

​	3、Filter 过滤器它的作用是：**拦截请求**，过滤响应。 

​	拦截请求常见的应用场景有： 

​			1、权限检查 

​			2、日记操作 

​			3、事务管理 

​			……等等

### 2. **Filter** **的初体验** 

要求：在你的 web 工程下，有一个 admin 目录。这个 admin 目录下的所有资源（html 页面、jpg 图片、jsp 文件、等等）都必须是用户登录之后才允许访问。 

思考：根据之前我们学过内容。我们知道，用户登录之后都会把用户登录的信息保存到 Session 域中。所以要检查用户是否登录，可以判断 Session 中否包含有用户登录的信息即可！！！

- Filter 的工作流程图：

  ![image-20211111171128634](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211111171128634.png)

- Filter 的代码：

  ```java
  public class AdminFilter implements Filter { 
      /**
      * doFilter 方法，专门用于拦截请求。可以做权限检查 
      */
      @Override 
      public void doFilter(ServletRequest servletRequest, ServletResponse servletResponse, FilterChain filterChain) throws IOException, ServletException { 
          HttpServletRequest httpServletRequest = (HttpServletRequest) servletRequest; 
          HttpSession session = httpServletRequest.getSession(); 
          Object user = session.getAttribute("user"); 
          // 如果等于 null，说明还没有登录 
          if (user == null) { servletRequest.getRequestDispatcher("/login.jsp").forward(servletRequest,servletResponse); 
                             return; 
                            } else { 
              // 让程序继续往下访问用户的目标资源 
              filterChain.doFilter(servletRequest,servletResponse); 
          } 
      } 
  }
  ```

- web.xml 中的配置：

  ```xml
  <!--filter 标签用于配置一个 Filter 过滤器--> 
  <filter> 
      <!--给 filter 起一个别名--> 
      <filter-name>AdminFilter</filter-name> 
      <!--配置 filter 的全类名--> 
      <filter-class>com.atguigu.filter.AdminFilter</filter-class> 
  </filter>
  <!--filter-mapping 配置 Filter 过滤器的拦截路径--> <filter-mapping> 
      <!--filter-name 表示当前的拦截路径给哪个 filter 使用--> 
      <filter-name>AdminFilter</filter-name> 
      <!--url-pattern 配置拦截路径
   		/ 表示请求地址为：http://ip:port/工程路径/ 映射到 IDEA 的 web 目录 
  		/admin/* 表示请求地址为：http://ip:port/工程路径/admin/* 
  --> <url-pattern>/admin/*</url-pattern> 
  </filter-mapping>
  ```

- Filter 过滤器的使用步骤： （如果客户端请求的资源是Filter所拦截的，就要先经过Filter检验）

  1、编写一个类去实现 Filter 接口 

  2、实现过滤方法 doFilter() 

  3、到 web.xml 中去配置 Filter 的拦截路径

### 3. **Filter** **的生命周期** 

Filter 的生命周期包含几个方法 

​		1、构造器方法 

​		2、init 初始化方法 

​				第 1，2 步，在 web 工程启动的时候执行（Filter 已经创建） 

​		3、doFilter 过滤方法 

​				第 3 步，每次拦截到请求，就会执行 

​		4、destroy 销毁 

​				第 4 步，停止 web 工程的时候，就会执行（停止 web 工程，也会销毁 Filter 过滤器）

### 4. **FilterConfig** **类** 

FilterConfig 类见名知义，它是 Filter 过滤器的配置文件类。 Tomcat 每次创建 Filter 的时候，也会同时创建一个 FilterConfig 类，这里包含了 Filter 配置文件的配置信息。 

FilterConfig 类的作用是获取 filter 过滤器的配置内容 

​		1、获取 Filter 的名称 filter-name 的内容 

​		2、获取在 Filter 中配置的 init-param 初始化参数 

​		3、获取 ServletContext 对象

```java
@Override 
public void init(FilterConfig filterConfig) throws ServletException { 
    System.out.println("2.Filter 的 init(FilterConfig filterConfig)初始化"); 
    // 1、获取 Filter 的名称 filter-name 的内容 
    System.out.println("filter-name 的值是：" + filterConfig.getFilterName()); 
    // 2、获取在 web.xml 中配置的 init-param 初始化参数 
    System.out.println("初始化参数 username 的值是：" + filterConfig.getInitParameter("username")); 
    System.out.println("初始化参数 url 的值是：" + filterConfig.getInitParameter("url")); 
    // 3、获取 ServletContext 对象 
    System.out.println(filterConfig.getServletContext()); 
}
```

```xml
<!--filter 标签用于配置一个 Filter 过滤器--> 
<filter> 
    <!--给 filter 起一个别名--> 
    <filter-name>AdminFilter</filter-name> 
    <!--配置 filter 的全类名-->
	<filter-class>com.atguigu.filter.AdminFilter</filter-class> 
    <init-param> 
        <param-name>username</param-name> 
        <param-value>root</param-value> 
    </init-param> 
    <init-param> 
        <param-name>url</param-name> 
        <param-value>jdbc:mysql://localhost3306/test</param-value>
    </init-param>
</filter>
```

### 5.**FilterChain** **过滤器链** 

​	Filter   过滤器 

​	Chain    链，链条 

​	FilterChain 就是过滤器链（多个过滤器如何一起工作）

![image-20211111200346884](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211111200346884.png)

### 6. **Filter** **的拦截路径** 

**--精确匹配** 

<**url-pattern**>/target.jsp</**url-pattern**> 

以上配置的路径，表示请求地址必须为：http://ip:port/工程路径/target.jsp 

**--目录匹配** 

<**url-pattern**>/admin/*</**url-pattern**> 

以上配置的路径，表示请求地址必须为：http://ip:port/工程路径/admin/* 

**--后缀名匹配** 

<**url-pattern**>*.html</**url-pattern**> 

以上配置的路径，表示请求地址必须以.html 结尾才会拦截到 

<**url-pattern**>*.do</**url-pattern**> 

以上配置的路径，表示请求地址必须以.do 结尾才会拦截到 

<**url-pattern**>*.action</**url-pattern**> 

以上配置的路径，表示请求地址必须以.action 结尾才会拦截到 

**Filter 过滤器它只关心请求的地址是否匹配，不关心请求的资源是否存在！！！**



### 7. 书城项目应用：**ThreadLocal** **的使用**  (重要！！)  

- ThreadLocal 的作用，它可以解决多线程的数据安全问题。 

- ThreadLocal 它可以给当前线程关联一个数据（可以是普通变量，可以是对象，也可以是数组，集合） 

- ThreadLocal 的特点： 

  1、ThreadLocal 可以为当前线程关联一个数据。（它可以像 Map 一样存取数据，key 为当前线程） 

  2、每一个 ThreadLocal 对象，只能为当前线程关联一个数据，如果要为当前线程关联多个数据，就需要使用多个ThreadLocal 对象实例。 

  3、每个 ThreadLocal 对象实例定义的时候，一般都是 static 类型 

  4、ThreadLocal 中保存数据，在线程销毁后。会由 JVM 虚拟自动释放。

- 测试类：

  ```java
  public class OrderService { 
      public void createOrder(){ 
          String name = Thread.currentThread().getName(); 
          System.out.println("OrderService 当前线程[" + name + "]中保存的数据是：" + 
                             ThreadLocalTest.threadLocal.get()); 
          new OrderDao().saveOrder(); 
      } 
  }
  public class OrderDao { 
      public void saveOrder(){ 
          String name = Thread.currentThread().getName(); 
          System.out.println("OrderDao 当前线程[" + name + "]中保存的数据是：" + 
                             ThreadLocalTest.threadLocal.get()); 
      } 
  }
  public class ThreadLocalTest { 
      // public static Map<String,Object> data = new Hashtable<String,Object>(); 
      public static ThreadLocal<Object> threadLocal = new ThreadLocal<Object>(); 
      private static Random random = new Random();
  
      public static class Task implements Runnable { 
          @Override 
          public void run() { 
              // 在 Run 方法中，随机生成一个变量（线程要关联的数据），然后以当前线程名为 key 保存到 map 中 
              Integer i = random.nextInt(1000); 
              // 获取当前线程名 
              String name = Thread.currentThread().getName();
              System.out.println("线程["+name+"]生成的随机数是：" + i); 
              // data.put(name,i); 
              threadLocal.set(i); 
              try {
                  Thread.sleep(3000);
              } catch (InterruptedException e) { 
                  e.printStackTrace();
              }
              new OrderService().createOrder(); 
              // 在 Run 方法结束之前，以当前线程名获取出数据并打印。查看是否可以取出操作 
              // Object o = data.get(name); 
              Object o = threadLocal.get(); 
              System.out.println("在线程["+name+"]快结束时取出关联的数据是：" + o); 
          } 
      }
      public static void main(String[] args) { 
          for (int i = 0; i < 3; i++){ 
              new Thread(new Task()).start();
          }
      } 
  }
  ```



### 8. **使用** **Filter** **和** **ThreadLocal** **组合管理事务**，具体看项目

1. **使用** **ThreadLocal** **来确保所有** **dao** **操作都在同一个** **Connection** **连接对象中完成** 

   原理分析图：

   ![image-20211112124810533](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211112124810533.png)

2. **使用** **Filter** **过滤器统一给所有的** **Service** **方法都加上** **try-catch。来进行实现的管理**。 

   原理分析图：

   ![image-20211112125446794](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211112125446794.png)

3. **将所有异常都统一交给** **Tomcat**，**让** **Tomcat** **展示友好的错误信息页面。**

   在 web.xml 中我们可以通过错误页面配置来进行管理。

4. 





## 第十一章   **JSON**、**AJAX**、**i18n**

### 1. **什么是** **JSON?** 

**JSON** (JavaScript Object Notation) 是一种轻量级的数据交换格式。易于人阅读和编写。同时也易于机器解析和生成。JSON采用完全独立于语言的文本格式，而且很多语言都提供了对 json 的支持（包括 C, C++, C#, Java, JavaScript, Perl, Python 等）。 这样就使得 JSON 成为理想的数据交换格式。 

json 是一种轻量级的数据交换格式。 

轻量级指的是跟 xml 做比较。 

数据交换指的是客户端和服务器之间业务数据的传递格式。



### 2. **JSON** **在** **JavaScript** **中的使用**

- **json** **的定义** 

  json 是由键值对组成，并且由花括号（大括号）包围。每个键由引号引起来，键和值之间使用冒号进行分隔，多组键值对之间进行逗号进行分隔。

  json 定义示例：

  ```javascript
  var jsonObj = {
      "key1":12, 
      "key2":"abc",
      "key3":true, 
      "key4":[11,"arr",false],
      "key5":{ 
          "key5_1" : 551,
          "key5_2" : "key5_2_value" 
      },
      "key6":[
          { "key6_1_1":6611, 
           "key6_1_2":"key6_1_2_value"
  
          },{
              "key6_2_1":6621, 
              "key6_2_2":"key6_2_2_value" 
          }] 
  };
  ```

- **json** **的访问** 

  json 本身是一个对象。 

  json 中的 key 我们可以理解为是对象中的一个属性。 

  json 中的 key 访问就跟访问对象的属性一样： json 对象.key 

  json 访问示例：

  ```javascript
  alert(typeof(jsonObj));// object json 就是一个对象 
  alert(jsonObj.key1); //12 
  alert(jsonObj.key2); // abc 
  alert(jsonObj.key3); // true 
  alert(jsonObj.key4);// 得到数组[11,"arr",false] 
  // json 中 数组值的遍历 
  for(var i = 0; i < jsonObj.key4.length; i++) { 
      alert(jsonObj.key4[i]); 
  }
  alert(jsonObj.key5.key5_1);//551 
  alert(jsonObj.key5.key5_2);//key5_2_value 
  alert( jsonObj.key6 );// 得到 json 数组 
  // 取出来每一个元素都是 json 对象 
  var jsonItem = jsonObj.key6[0]; 
  // alert( jsonItem.key6_1_1 ); //6611 
  alert( jsonItem.key6_1_2 ); //key6_1_2_value
  ```

- **json** **的两个常用方法** 

  json 的存在有两种形式。 

  一种是：对象的形式存在，我们叫它 json 对象。 

  一种是：字符串的形式存在，我们叫它 json 字符串。 

  **一般我们要操作 json 中的数据的时候，需要 json 对象的格式**。 

  **一般我们要在客户端和服务器之间进行数据交换的时候，使用 json 字符串**。 

     JSON.stringify() 

  ​		把 json 对象转换成为 json 字符串 

     JSON.parse() 

  ​		把 json 字符串转换成为 json 对象

  示例代码：

  ```javascript
  // 把 json 对象转换成为 json 字符串 
  var jsonObjString = JSON.stringify(jsonObj); // 特别像 Java 中对象的 toString 
  alert(jsonObjString)
  
  // 把 json 字符串 转换成为 json 对象 
  var jsonObj2 = JSON.parse(jsonObjString); alert(jsonObj2.key1);// 12 
  alert(jsonObj2.key2);// abc
  ```

  

### 3. **JSON** **在** **Java** **中的使用**

- **javaBean** **和** **json** **的互转**

  ```java
  @Test
  public void test1(){ 
      Person person = new Person(1,"国哥好帅!"); 
      // 创建 Gson 对象实例 
      Gson gson = new Gson(); 
      // toJson 方法可以把 java 对象转换成为 json 字符串 
      String personJsonString = gson.toJson(person); 
      System.out.println(personJsonString); 
      
      // fromJson 把 json 字符串转换回 Java 对象 
      // 第一个参数是 json 字符串 
      // 第二个参数是转换回去的 Java 对象类型 
      Person person1 = 
          gson.fromJson(personJsonString, Person.class);
      System.out.println(person1);
  }
  ```

- **List** **和** **json** **的互转**

  ```java
  // 1.2.2、List 和 json 的互转 
  @Test 
  public void test2() {
      List<Person> personList = new ArrayList<>(); 
      personList.add(new Person(1, "国哥")); 
      personList.add(new Person(2, "康师傅")); 
      Gson gson = new Gson(); 
      // 把 List 转换为 json 字符串 String 
      personListJsonString = gson.toJson(personList); 
      System.out.println(personListJsonString);
  	// 把 json 字符串 转换为 List<Person> 
      List<Person> list = 
          gson.fromJson(personListJsonString, new TypeToken<ArrayList<Person>>(){}.getType()); 
      System.out.println(list); 
      Person person = list.get(0); 
      System.out.println(person); 
  }
  ```

- **map** **和** **json** **的互转**

  ```java
  // 1.2.3、map 和 json 的互转 
  @Test 
  public void test3(){ 
      Map<Integer,Person> personMap = new HashMap<>(); 
      personMap.put(1, new Person(1, "国哥好帅")); 
      personMap.put(2, new Person(2, "康师傅也好帅")); 
      Gson gson = new Gson(); 
      // 把 map 集合转换成为 json 字符串 
      String personMapJsonString = 
          gson.toJson(personMap); 
      System.out.println(personMapJsonString);
      
      // Map<Integer,Person> personMap2 = gson.fromJson(personMapJsonString, new PersonMapType().getType()); 
      //使用匿名内部类
      Map<Integer,Person> personMap2 = 
          gson.fromJson(personMapJsonString, new TypeToken<HashMap<Integer,Person>>(){}.getType()); 
      System.out.println(personMap2); 
      Person p = personMap2.get(1); 
      System.out.println(p); 
  }
  ```

  

### 4. **什么是** **AJAX** **请求** 

AJAX 即“**A**synchronous **J**avascript **A**nd **X**ML”（异步 JavaScript 和 XML），是指一种**创建交互式网页应用的网页开发技术**。

**ajax 是一种浏览器通过 js 异步发起请求，局部更新页面的技术。** 

**Ajax 请求的局部更新，浏览器地址栏不会发生变化** 

**局部更新不会舍弃原来页面的内容**



### 5. **原生** **AJAX** **请求的示例：**

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html> 
    <head>
        <meta http-equiv="pragma" content="no-cache" /> 
        <meta http-equiv="cache-control" content="no-cache" /> 
        <meta http-equiv="Expires" content="0" /> 
        <meta http-equiv="Content-Type" content="text/html; charset=UTF-8"> 
        <title>Insert title here</title>
        <script type="text/javascript"> 
            // 在这里使用 javaScript 语言发起 Ajax 请求，访问服务器 AjaxServlet 中 javaScriptAjax 
            function ajaxRequest() { 
                // 1、我们首先要创建 XMLHttpRequest 
                var xmlhttprequest = new XMLHttpRequest(); 
                // 2、调用 open 方法设置请求参数 
                xmlhttprequest.open("GET","http://localhost:8080/16_json_ajax_i18n/ajaxServlet?action=javaScriptAjax",true) 
                // 4、在 send 方法前绑定 onreadystatechange 事件，处理请求完成后的操作。 
                xmlhttprequest.onreadystatechange = function(){ 
                    if (xmlhttprequest.readyState == 4 && xmlhttprequest.status == 200) { 
                        var jsonObj = JSON.parse(xmlhttprequest.responseText); 
                        // 把响应的数据显示在页面上 
                        document.getElementById("div01").innerHTML = "编号：" + jsonObj.id + " , 姓名：" + jsonObj.name; 
                    } 
                } 
                // 3、调用 send 方法发送请求 
                xmlhttprequest.send(); 
            } 
        </script> 
    </head> 
    <body>
        <button onclick="ajaxRequest()">ajax request</button> 
        <div id="div01"> 
        </div> 
    </body> 
</html>
```

### 6. **jQuery** **中的** **AJAX** **请求** 

- **$.ajax 方法** 

​	url 表示请求的地址 

​	type 表示请求的类型 GET 或 POST 请求 

​	data 表示发送给服务器的数据 

​		格式有两种： 

​			一：name=value&name=value 

​			二：{key:value} 

​	success 请求成功，响应的回调函数 

​	dataType 响应的数据类型 

​		常用的数据类型有： 

​			text 表示纯文本 

​			xml 表示 xml 数据 

​			json 表示 json 对象

```javascript
$("#ajaxBtn").click(function(){ 
    $.ajax({ 			       		 
            url:"http://localhost:8080/16_json_ajax_i18n/ajaxServlet", 
            // data:"action=jQueryAjax", 
            data:{action:"jQueryAjax"}, 
            type:"GET", 
            success:function (data) { 
                // alert("服务器返回的数据是：" + data); 
                // var jsonObj = JSON.parse(data); 
                $("#msg").html("编号：" + data.id + " , 姓名：" + data.name); 
            },
            dataType : "json" 
           }); 
});
```

- **$.get 方法和 \$.post 方法** 

​	url 请求的 url 地址 

​	data 发送的数据 

​	callback 成功的回调函数 

​	type 返回的数据类型

```javascript
// ajax--get 请求 
$("#getBtn").click(function(){ 	$.get("http://localhost:8080/16_json_ajax_i18n/ajaxServlet","action=jQueryGet",function (data) { $("#msg").html(" get 编号：" + data.id + " , 姓名：" + data.name); },"json"); 
                             }); 
// ajax--post 请求 
$("#postBtn").click(function(){ $.post("http://localhost:8080/16_json_ajax_i18n/ajaxServlet","action=jQueryPost",function (data) { $("#msg").html(" post 编号：" + data.id + " , 姓名：" + data.name);
},"json"); 
                              });
```

- **$.getJSON 方法** 

  url 请求的 url 地址 

  data 发送给服务器的数据 

  callback 成功的回调函数

![image-20211112135741481](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211112135741481.png)



- **表单序列化 serialize()** 

  serialize()可以把表单中所有表单项的内容都获取到，并以name=value&name=value 的形式进行拼接。

  ![image-20211112135849970](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211112135849970.png)



### 7. **i18n** **国际化**（了解内容）

- **什么是** **i18n** **国际化？** 

  - 国际化（Internationalization）指的是同一个网站可以支持多种不同的语言，以方便不同国家，不同语种的用户访问。 

  - 关于国际化我们想到的最简单的方案就是为不同的国家创建不同的网站，比如苹果公司，他的英文官网是：http://www.apple.com 而中国官网是 http://www.apple.com/cn 

  - 苹果公司这种方案并不适合全部公司，而我们希望相同的一个网站，而不同人访问的时候可以根据用户所在的区域显示 不同的语言文字，而网站的布局样式等不发生改变。 

  - 于是就有了我们说的国际化，国际化总的来说就是同一个网站不同国家的人来访问可以显示出不同的语言。但实际上这种需求并不强烈，一般真的有国际化需求的公司，主流采用的依然是苹果公司的那种方案，为不同的国家创建不同的页面。所以国际化的内容我们了解一下即可。 

  - 国际化的英文 Internationalization，但是由于拼写过长，老外想了一个简单的写法叫做 I18N，代表的是 Internationalization 这个单词，以 I 开头，以 N 结尾，而中间是 18 个字母，所以简写为 I18N。以后我们说 I18N 和国际化是一个意思。

- **国际化相关要素介绍**

  ![image-20211112233538666](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211112233538666.png)



- **通过请求头国际化页面**

  ![image-20211112233839432](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211112233839432.png)

  ![image-20211112233849006](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211112233849006.png)

- **通过显示的选择语言类型进行国际化**

  ![image-20211112233908599](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211112233908599.png)

  ![image-20211112233940703](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211112233940703.png)

  ![image-20211112233952832](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211112233952832.png)

- **JSTL** **标签库实现国际化**

  ![image-20211112234314572](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211112234314572.png)

  ![image-20211112234322986](E:\Java_Notes\notebook\JavaWeb\JavaWeb_Notes.assets\image-20211112234322986.png)

  


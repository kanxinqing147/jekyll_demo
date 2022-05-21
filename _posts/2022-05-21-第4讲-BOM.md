---
layout: post
title: 第四部分 BOM & DOM
tags: Web
---

# BOM & DOM #

## 第四讲 BOM & DOM ##

### 4 BOM & DOM ###
	
	BOM & DOM 可以做一些网页的简单效果。
<!--more-->

** 4.1 BOM（浏览器对象模型） **

	* 1 什么是BOM。
		* BOM：Browser Object Model。浏览器对象模型。
			* 浏览器：可以解析html文件，代表一个窗口的对象，窗口叫 window，也叫 父对象，即所有东西都在window对象中运行，包括地址栏、文档。
			
	* 2 浏览器对象（5个，重点是Window）
		* Window	：窗口对象。打开浏览器就是一个窗口对象。				（重点）对象和方法常用
		* Navigator	：浏览器对象。和浏览器版本（火狐、谷歌、IE等）相关的。	（了解）
		* Screen	：屏幕对象。和浏览器屏幕相关的。						（不用记）
		* History	：历史记录对象。和浏览器历史记录相关的。				（有2个方法，了解）
		* Location	：位置对象。和浏览器地址栏相关的。						（有1个属性，了解）
			
	* 3 BOM中5个对象之间的关系
		* window对象是最外层的对象，包含Navigator、Screen、History、Location对象
		
		* 查看《W3School全套教程.CHM》→ Browser Scripting → JavaScript → 完整的JavaScript对象参考手册（包含实例》 → DOM对象
		
		* window对象：地址栏属于窗口对象、历史记录也属于窗口对象、屏幕也属于窗口对象。window对象是JavaScript层级中的顶层对象，是最外层的一个对象。
		* window对象的属性
			* history	：对History对象的引用
			* Screen	：对Screen对象的引用
			* Navigator	：对Navigator对象的引用

** 4.2 BOM对象之Naviagtor、History、Location对象 **

	* 1 Naviagtor对象
		* 方法不用记，简单了解属性即可。
		
		* 属性都是和浏览器版本相关的
			* userAgent	：返回客户机发送服务器的user-agent头部的值。http头部信息。
			
	* 2 History对象
		* 方法
			* back()	：去上一页。
			* forward()	：去下一页。浏览器历史记录可记录上一页和下一页的URL
			* go()		：可以传入值。如果传入1，等于forward()；如果传入-1，代表back()
		* 说明
			* 浏览器本身也提供一个上一页和下一页的功能，在地址栏左侧 ← →	
			* History对象的三个方法和此功能相同。
			
	* 3 Location对象
		* 了解几个属性
		
		* 属性
			* href	：当前网页地址的链接。返回完整的URL。
				* 作用：用来获取和设置当前网页的地址。设置网页地址的话，就可以完成网页的跳转功能。
			* port	：设置或获取当前URL的端口号。
			* host	：设置或返回主机名和当前URL的端口号。
			* protocol	：设置或返回当前URL的协议。
			
	* 4 Naviagtor、History和Location对象举例
		* 在按钮上绑定事件
			<body>
				<!-- 在按钮上绑定事件 -->
				<input type="button" value="按钮" onclick="run()"/>
				//按钮就是事件源，可以在事件源上绑定一些事件

				<input type="button" value="下一页" onclick="run2()"/>

				<input type="button" value="地址栏跳转" onclick="run3()"/>
			</body>
			<script type="text/javascript">
				//点击按钮，执行run()方法
				funciton run(){
					//alert("hehe");
					//获取查看Navigator的属性
					alert(window.navigator.userAgent);
				}

				//History对象
				function run2(){
					//去下一页
					window.history.forward();

					//去下一页的另一个方式
					window.history.go(1);
				}

				//
				funciton run3(){
					//获取当前网页的URL
					//alert(window.location.href);	//如果地址栏中有中文，会对中文进行编码

					//设置当前网页的地址为百度
					window.location.href="http://www.baidu.com";
				}
			</script>

	* 强调一点：
		* window可以省略。
		
** 4.2 BOM对象之window对象 **

	* 1 window对象的方法
		* （1）alert()	：弹出提示框。显示带有一段消息和一个确认按钮的警告框。
		
		* （2）confirm("显示的内容")	：弹出询问框。显示带有一段消息以及确认按钮和取消按钮的对话框。
			* 询问框上有2个按钮，一个是确定，一个是取消。点击"确定"，默认返回true；点击"取消"，默认返回false。
			* 举例
				<body>
					<input type="button" value="删除" onclick="del()" />
				</body>
				<script type="text/javascript">
					funciton del(){
						if(window.confirm("确定删除吗？")){
							alert("删除成功！");
						}else{
							alert("咋还取消了呢！！");
						}
					}
				</script>
		* （3）setInterval("函数名称",毫秒数)	：每隔多少毫秒执行一次（执行n次）。默认返回id值。
		* （3）setTimeout("函数名称",毫秒数)	：到多少毫秒后执行一次（只执行一次）。默认返回id值。
		* （4）clearInterval("唯一的id值")	：清除定时器
		* （4）clearTimeout("唯一的id值")	：
			* 举例
				<body>
					<input type="button" value="定时器" onclick="run()" />

					<input type="button" value="清除定时器" onclick="clear2()" />
				</body>
				<script type="text/javascript">
					var timeId;
					//完成定时器的操作
					function run(){
						// 每隔3秒钟执行一次show()方法
						timeId = window.setInterval("show()",3000);
		
						//执行性1次
						//window.setTimeout("show()",3000);
					}
	
					//清除定时器
					function clear2(){
						window.clearInterval(timeId);
					}

					function show(){
						alert("haha");
					}
				</script>

			* 应用场景
				* 有了定时器就可以做一些和定时器相关的操作，比如每隔1秒刷新页面。
		* （5）open(URL,features,replace)	：弹出一个新的窗口。用于打开一个新的浏览器窗口或者查找一个已命名的窗口。
			<body>
				<input type="button" value="弹出新窗口" onclick="tan()" />
			</body>
			<script>
				function tan(){
					window.open("http://www.baidu.com","aa","width=400","height=200");
				}
			</script>

			作业：
				详见： window.html 参考案例
				详解见：《作业3：弹出新窗口.bmp》
	
	* 2 图片随机移动案例
		* 图片在页面每隔几秒钟移动一个位置
		
		* 加载事件：页面一加载完成，立即执行事件。onload="run()"。一般作用在<body>标签上。
		
		* window对象还包括document对象。document对象提供了getElementById("id的值");方法。该方法获取到元素（标签）对象。

			步骤1：onload加载事件	页面一加载完成，执行方法。
			步骤2：document对象：代表文档的对象。通过getElementById(id值)获取元素对象。
			步骤3：通过img.style.xxx = 赋值。
			步骤4：通过Math对象获取随机数。
			步骤5：window.setTimeout()。
	
			----------

			<head>
				<style type="text/css">
					img{
						position:absolute;
						/*top:100px;
						left:100px;*/
					}
				</style>
			</head>

			<body onload="run()">
				<img alt="" id="imgId" style="top:100px;left:100px" src="peppa pig.jpg"> <br />

				<input id="userId" type="text" name="username" value="haha" />
			</body>

			<script type="text/javascript">
				//加载事件
				function run(){
					//alert("haha");

					//使用document对象来获取input文本框的对象
					//var input = window.document.getElementById("userId");	//input是引用类型
					//alert(input.value);	//拿到input对象的value属性值
					//input.value = "张三";	//重新赋值

					//先获取img标签的对象
					var img = document.getElementById("imgId");

					//设置距离页面上端的距离
					img.style.top = Math.random()*300 + "px";
					//设置距离页面左端的距离
					img.style.left = Math.random()*500 +"px";

					//定时器
					window.setTimeout("run()",1000);
				}
			</script>

-------------------------------------------------------------

### 作业解答 ###

	360浏览器，不是标准，模拟的是IE的内核，在此基础上自己扩展一些功能，后来又换成谷歌内核。总之，永远都是在模仿。
	猎豹、世界之窗等之类的浏览器，统统卸载掉。

	IE、谷歌、火狐这3个浏览器是世界公认的，最权威的，尤其是谷歌和火狐。H5标准出来之后，浏览器的兼容性就出现很大的问题。

** 作业1： 99乘法表**
	<html>
	<head>
		<title>99乘法表</title>
	</head>
	<body>

	</body>
		<script type="text/script">

			/*
				* 外层有一个大循环（循环行） var i = 1 从1到9
				* 每循环一行，小的循环（循环列，条件：var j <= i)
				* 每循环一行后，要输出一个换行
			*/
			
			// 99乘法表
			// 向页面输出表格
			document.write("<table border='1'  width='50%' cellpadding='10'>");
			// 循环行
			for(var i = 1;i <= 9;i++){
				// 编写行
				document.write("<tr>");
				// 循环列
				for(var j = 1;j <=i; j++){
					// 拼接字符串，1 * 1 = 1
					document.write("<td>" + j + "*" + i + "=" + i*j + "</td>");
				}
				//换行
				//document.write("<br />");
				document.write("</tr>");	//表格自动换行
			}
			
			// table的结束标签
			document.write("</table>");
		</script>
	</html>

	目的：锻炼这种html和js结合在一起的编程方式

** 作业2：去掉字符串两边的空格 **
	<html>
	<head>
		<title>去掉字符串两边的空格</title>
	</head>
	<body>

	</body>
		<script type="text/javascript">
			// 定义去掉字符串两边空格的方法
			function myTrim(str){
				// 定义两个变量，一个从0开始，一个从末尾开始
				var strat = 0;
				var end = str.length - 1;

				// 判断指定位置的字符是" "
				while(strat <= end && str.chaAt(strat) == " "){
					// 让start自加
					strat++;
				}

				// 从后向前判断指定位置的字符
				while(start <= end && str.charAt(end) == " "){
					// 从后向前
					end--;
				}

				// 截取字符串
				return str.substring(start,end + 1);
			}
			// 测试方法是否正确
			var str = "    abc    ";
			alert("-" + str + "-");

			var str2 = myTrim(str);
			alert("-" + str2 + "-");
		</script>
	</html>

** 作业3：弹出新窗口案例 **
	parent.html
	<html>
	<head>
		<title></title>
	</head>
	<body>
		编号：<input type="text" name="userNum" id="numId" /> <br />
		姓名：<input type="text" name="userName" id="nameId" /> <br />

		<input type="button" value="选择" onclick="create()" />
	</body>
		<script type="text/javascript">
			// 弹出新窗口
			function create(){
				window.open("child.html","child","width=400,height=200");
			}
		</script>
	</html>

	----------
	child.html
	<html>
	<head>
		<title>选择数据</title>
		<style type="text/css" >
			tr{
				text-aligin:center;
			}
		</style>
	</head>
	<body>
		<table border="1" width="100%" cellpadding="10">
			<tr>
				<th>操作</th>
				<th>编号</th>
				<th>姓名</th>
			</tr>
			<tr>
				<td>
					<input type="button" value="选择" onclick="check('001','张三')" />
				</td>
				<td>001</td>
				<td>张三</td>
			</tr>
			<tr>
				<td>
					<input type="button" value="选择" onclick="check('002','李四')" />
				</td>
				<td>002</td>
				<td>李四</td>
			</tr>
			<tr>
				<td>
					<input type="button" value="选择" onclick="check('003','王五')" />
				</td>
				<td>003</td>
				<td>王五</td>
			</tr>
		</table>
	</body>
		<script type="text/javascript">
			// 获取选择的数据
			function check(num,name){
				// 如果已经接受到值
				// 进行赋值

				// window ：代表当前窗口child窗口
				// 属性	：通过opener可以获取创建该窗口的window对象

				// 获取parentWin窗口的引用
				var parentWin = window.opener;

				// 可以使用parentWin对象来获取document文档
				parentWin.document.getElementById("numId").value = num;
				parentWin.document.getElementById("nameId").value = name;

				// 关闭当前的窗口
				window.close();
			}
		</script>
	</html>

-------------------------------------------------------------

** 4.3 DOM 文档对象模型 **

	DOM必然涉及到解析的知识，即用DOM方式来解析HTML，还可以用来解析XML。

	* 1 DOM简介
		* （1）DOM：Document Object Model	文档对象模型
			* 文档：标记性的文档（HTML、XML）。浏览器“大白板”
			* 对象：有对象就会有其方法或属性。就可以方便的操作。
			* 模型：抽象的概念。把共有的特性封装起来，形成一个模型。

		* （2）DOM的作用
			* 会把所有的文档内容全部（、文本元素、属性）封装成对象，封装成对象的目的是方便我们操作，因为对象提供了方法和属性。

		* （3）DOM要操作标记型文档必须先进行解析（解析器）
			* 涉及一个概念：解析器。
			* 解析器都已经给我们提供了。如果想操作html，浏览器就充当了解析器的角色，因为浏览器就可以解析html代码，一解析就把html元素封装成对象。浏览器对XML就不是解析了，因为XML提供了类，sun公司提供了java的类，类中就有解析器的概念，可以使用类来解析xml文件。
		
	* 2 DOM使用什么样的方式来解析HTML代码
		* 使用DOM方式解析HTML。怎么样来解析的，要知道解析的过程。
			* 详见《01-DOM解析HTML的方式.bmp》
												|			  ——————————
												|			  |document|  （document节点
												|			  ——————————	是所有树的根节点）
												|				  |
												|				——————
												|				|html|
		---- 最普通的HTML代码 ----				|				——————
		<html>									|			↙			↘
			<head>								|	——————				————————
				<title>HTML DOM</title>			|	|head|				| body |
			</head>								|	——————				————————
			<body>								|	   |				↙     ↘
				<h1>DOM的结构</h1>				|	———————		  ——————		 ——————
				<p><a href="href">链接</a></p>	|	|title|		  | h1 |		 |  p |
			</body>								|	———————		  ——————		 ——————
		</html>									|	   |			 |			    |  
												|  ——————————	——————————— 	 ———————   —————— 
												|  |HTML DOM|	|DOM的结构|  	 | a标签|——|href|
												|  ——————————	———————————  	 ———————   —————— 
												|（把标签内容也封装成对象）		  	|    
												|								 ————————  
												|								 | 链接 |  
												|								 ————————  
												|								（属性也是对象）
												|
												|1. DOM也会把标签的文本内容封装成对象，
												|所以，文本也是一个节点。
												|2. DOM也将标签的属性封装成对象，属性也是一个节点。
												|
												|* document	：代表整个文档对象
												|* element	：代表元素（标签）对象
												|* text		：代表文本内容	（没有）
												|* attribute：代表属性对象	（没有）
												|
												|* Node		：代表节点对象。是以上对象的父类。

		* 用浏览器打开html文件，打开html之后，在浏览器的内存中解析html，解析后形成一个树状结构，

		* DOM解析的方式：先把整个标记型文档一次性的全部加载进内存中，形成一个树状结构。
		* DOM解析方式：树状结构。   （考点）

		* 树状结构有好处：
			* 节点之间有关系，兄弟节点、父子节点、祖孙节点之间都有关系。节点中提供访问兄弟、父子、祖孙节点的方法，例如获取父节点的方法、获取兄弟节点等方法。
			* 还可以添加一个节点。创建一个节点，找个位置添加上即可。
			
	* 3 DOM的三个级别和DHTML介绍
		* （1）DOM的三个级别就是DOM发展的过程
			* 最开始DOM 1级别，支持解析html、xml。随着技术的发展，h4到h5，xml也是一直发展的，DOM也要随之发展，就有了DOM的三个级别。
			* DOM 1，是最基础的一个级别，支持一些简单的解析，随着html和xml功能的增加，DOM1支持不了了，就升级到DOM2，对一些新的技术做了一些支持。

			* DOM level 1：将html封装成对象。
			* DOM level 2：在level 1的基础上添加新功能，例如，对事件和css样式的支持。
			* DOM level 3：支持xml 1.0的一些特性。
				* 注意：
					* 1 现在学的基本上都是1级别的。
					* 2 如果想深入学习，今后还需要去了解2、3级别的新特性，因为要知道有些方法是在2、3级别上提供的。

		* （2） DHTML
			* DHTML不是一门语言。是几种语言合在一起，形成的一套体系。
				* HTML				：使用标签封装数据（最基本的一步）。因为，所有东西都得用html标签封装起来，才能操作标签。
				* CSS				：设置网页的样式。
				* JavaScript（BOM）	：提供程序的控制语句。for if等语句。
				* DOM				：提供了一些解析的对象。对象提供了api，才能去完成对html的操作。
				
	* 4 BOM和HTML DOM关系图
		* 详见《BOM 和HTML DOM关系图.png》

		* Farme		：框架。
		* document	：浏览器主要的"大白板"中的内容。
		
	* 5 document对象和api	
		* 代表整个文档对象，提供了一些方法和属性。
		
		* （1）document对象的集合
			* 可以使用集合的方式，获取一些内容。例如 forms[]获取文档中所有的from对象的引用，再通过下标值，得到指定的form。
			
		* （2）document对象的方法  （考点）
			* getElementById("id的值")	：获取指定id值的元素对象。
				* id值要唯一。如果不唯一的话，默认获取的是先加载的第一对象。
				
			* getElementsByName("name名称")	：获取name名称相同的元素对象。
				* 返回的是类似一个集合，但是不是数组，底层封装成类似集合的一个对象，和数组很相似。也可以通过下标[]得到该元素，或者循环遍历。其实是没有一个真实的对象。叫connation：ElementConnection，NodeList集合，是一个节点对象列表。
				
			* getElementsByTagName("标签名称")	：获取通过标签名称的元素对象集合。
			
			* wirte("文本内容")	：把文本内容输出到客户端（浏览器）。
			* writeln("文本内容")：但是在页面上不换行，因为浏览器解析成空格，n个空格在浏览器上解析成1个空格。
		
		* （3）举例
			<html>
				<head>
					<title>document</title>
				</head>
				<body>
					<input type="text" name="username" id="nameId" value="张三" /> <br />

					<input type="text" value="李四" /> <br />
					<input type="text" value="王五" /> <br />
				</body>
					<script type="text/javascript">
						// 获取一个对象
						var input = window.document.getElementById("nameId");
						alert(input.value);

						// 
						var inputs = document.getElementsByName("username");	//得到类似于集合的对象
						alert(inputs[1].value);	//通过下标值访问
						for(var i = 0; i< inputs.length; i++){
							alert(inputs[i].value);
						}

						var inputs2 = document.getElementsByTagName("input");
						for(var i = 0; i < inputs2.length; i++){
							alert(inputs2[i].value);
						}

					</script>
			</html>

		* 强调
			* getElementById("id的值")、getElementsByName("name名称")、getElementsByTagName("标签名称")三个方法是程序的入口。3个方法必须熟记、掌握。
			* 若想操作一个文档，一般情况，需要获取元素的对象，有了元素对象才可以进行后续的操作。
			
	* 6 动态添加子节点
		* 因为浏览器已经将html文件解析成树状结构了，只需要在树状结构上添加一个节点就OK。
		
		* 在节点末尾添加一个新节点

		* 思路详见《02-添加子节点.bmp》
		
		* 举例
			<body>
				<h4>无序列表</h4>
				<ul>
					<li>北京</li>
					<li>上海</li>
					<li>广州</li>
				</ul>
					<br />

					<input type="button" value="添加" onclick="run()" />
				
			</body>
				<script type="text/javascript">
					// 点击添加按钮，在ul的列表下添加<li>深圳</li>
					// 分析过程详见《02-添加子节点.bmp》
					// 创建元素方法详见《网页制作完全手册.chm》
					// 添加节点方法详见《NODE接口的特性和方法.png》
					
					// 生成子节点
					function run(){
						// 创建元素对象
						var li = document.createElement("li");
						// 创建文本
						var text = document.createTextNode("深圳");
						// 把文本添加到li下面
						li.appendChild(text);
						// 把li添加到ul的下面
						// 获取ul的节点
						var uls = document.getElementsByTagName("ul");	//uls是类似集合节点
						var ul = uls[0];	//得到一个元素
						ul.appendChild(li);
						
					}
				</script>
		* 总结
			* 创建元素对象	：document.createElement()
			* 创建文本对象	：document.createTextNode()
			* 添加子节点		：appendChild()
		
	* 7 Element（元素）对象
		* （1）和操作属性相关的方法。
			* setAttribute("属性名称","属性值")	:设置或修改属性的值。
			* getAttribute("属性名称")		:获取属性的值。
			* removeAttribute("属性名称")	:删除属性。
			
		* （2）获取子节点（记住）
			* Element.getElementsByTagName("元素名称")	：获取元素下面的所有子节点。
		* 举例
			<html>
				<head>
					<title></title>
				</head>
				<body>
					<input type="text" id="nameId" value="张三">

					<ul id="ulId">
						<li>北京</li>
						<li>上海</li>
						<li>广州</li>
					</ul>
				</body>
					<script type="text/javascript">
						// 代表的是元素Element
						var input = document.getElementById("nameId");
	
						// 获取元素对象的属性
						alert(input.getAttribute("value")); //与window.document.getElementById("nameId").value获取的值是一样的，但是底层实现不一样。

						// 设置属性的值
						input.setAttribute("value","李四");
						alert(input.getAttribute("value"));

						// 删除属性（属性删除后，获取的值是null）
						input.removeAttribute("value");
						alert(input.getAttribute("value"));


						// 获取ul下所有子节点
						var ul = document.getElementById("ulId");
			
						// 两种方式
						// 方式1（IE9及以上、谷歌、火狐浏览器中 获取的子节点数不准确）
						var lis = ul.childNodes;
						alert(lis.length);

						// 方式2（常用）
						// 通过getElementByTagName来获取子节点
						var lis2 = ul.getElementsByTagName("li");
						alert(lis2.length);
						
					</script>
			</html>

	* 8 Node节点对象
		* Document、Element、Text、Attribute对象都属于Node节点对象。即Node对象的方法，在上述4种对象中都可以使用。
		
		* （1）Node对象的三个属性   （考点）
			* nodeName	：属性名称
			* nodeType	：属性类型
			* nodeValue	：属性值
				* 可以通过以上三个属性判断获取的对象是那种对象，因为这3个属性的值都是固定的。
				—————————————————————————————————————————————————————
				|			|   元素对象		| 属性对象	|  文本对象	|
				—————————————————————————————————————————————————————
				| nodeName	| 大写的标签名称	| 属性名称	|   #text	|
				—————————————————————————————————————————————————————
				| nodeType	|      1		|    2		|     3		|
				—————————————————————————————————————————————————————
				| nodeValue	|     null		| 属性值		| 文本的内容 |
				—————————————————————————————————————————————————————
				* 举例
					<body>
						<input type="text" id="nameId" value="张三" /> <br />

						<span id="spanId">我是文本内容</span>
					</body>
						<scripte type="text/javascript" >
							// 先获取元素对象
							var input = document.getElementById("nameId");
							alert(input.nodeName);	// INPUT
							alert(input.nodeType);	// 1
							alert(input.nodeValue);	// null

							// 获取属性对象
							var value = input.getAttributeNode("value");
							alert(value.nodeName);	// value
							alert(value.nodeType);	// 2
							alert(value.nodeValue);	// 张三

							// 获取文本
							var span = document.getElementById("spanId");
							var text = span.firstChild;
							alert(text.nodeName);	// #text
							alert(text.nodeType);	// 3
							alert(text.nodeValue);	// 我是文本内容
						</script>

		* （2）Node其它的属性
			* 节点与节点之间的关系详见《03-节点与节点之间的关系图.bmp》
			
			* 父节点：parentNode
				* parentNode属性返回的节点永远是一个元素节点，因为只有元素节点才有可能包含子节点。
				* document节点没有父节点。
			* 子节点
				* childNodes	：获取指定节点的所有子节点集合。
				* firstChild	：获取指定节点的第一个子节点。
				* lastChild		：获取指定节点的最后一个子节点。
			* 同辈节点
				* nextSibling	：返回一个给定节点的下一个兄弟节点
				* previousSibling：返回一个给定节点的上一个兄弟节点
			
			* 注意：
				  IE6-8								IE9-10、Chrome、FireFox
				firstChild		第一个节点		firstElementChild		第一个节点
				lastChild		最后一个节点		lastElementChild		最后一个节点
				nextSibling		下一同级节点		nextElementSibling		下一同级节点
				previousSibling	上一同级节点		previousElementSibling	上一同级节点
			* 举例
				<body>
					<ul id="ulId">
						<li>北京</li>
						<li>上海</li>
						<li>广州</li>
					</ul>
				</body>
					<script type="text/javascript">
						var ul = document.getElementById("ulId");

						// DOM一级别时，提供的方式，但是火狐、谷歌都包含 换行符 ，并且高版本的IE也包含 换行符了。
						var bj = ul.firstChild;	// 获取到的是 换行 的文本，而不是第一 li 元素
						alert(bj.nodeName);		// #text

						// 在DOM二级别就将firstChild扩展成了firstElementChild（第一个元素的子节点）
						var bj2 = ul.firstElementChild;	// 第一个元素的子节点
						alert(bj2.nodeName);	// LI
					</script>

	* 9 Node节点对象的方法
		* （1）检测子节点和属性的方法
			* hasChildNodes()	:查看是否存在子节点
			* hasAttributes()	:查看是否存在属性
			
			* 举例
				<body>
					<ul id="ulId">
						<li>北京</li>
						<li>上海</li>
						<li>广州</li>
					</ul>
				</body>
					<script type="text/javascript">
						// 先判断ul是否包含子节点
						var ul = document.getElementById("ulId");
						alert(ul.hasChildNodes());

						// 判断是否包含属性
						alert(ul.hasAttributes());
					</script>

** 4.4 操作DOM节点树 **	（考点）

	* 1 插入节点
		* appendChild()			：默认向末尾添加子节点
		* insertBefore(new,old)	：在指定的节点之前添加子节点。new：创建的新节点；old：在哪个节点之前添加
			* 注意：没有insertAfter()方法

		* 举例
			<body>
				<h4>无序列表</h4>
				<ul>
					<li>北京</li>
					<li id="shId">上海</li>
					<li>广州</li>
				</ul>
				<br />

				<input type="button" value="添加" onclick="run()" />
				
			</body>
				<script type="text/javascript">
					// 生成子节点
					function run(){
						// 创建元素对象
						var li = document.createElement("li");
						// 创建文本
						var text = document.createTextNode("深圳");
						// 把文本添加到li下面
						li.appendChild(text);
						// 把li添加到ul的下面
						
						//------------方法1--------------
						/* // 获取ul的节点
						var uls = document.getElementsByTagName("ul");	//uls是类似集合节点
						var ul = uls[0];	//得到一个元素

						// 获取上海的节点
						var sh = document.getElementById("shId");
						ul.insertBefore(li,sh); */
						
						//------------方法2--------------
						var sh = document.getElementById("shId");
						// 根据shId获取其父节点
						var ul = sh.parentNode;
						
						ul.insertBefore(li,sh);
					}
				</script>
	* 2 删除节点
		* removeChild(node)	：删除节点。
			* 注意：要使用父节点调用该方法。
		* 举例
			* --------------------
			<body>
				<ul id="ulId">
					<li>北京</li>
					<li onclick="run()">上海</li>
					<li>广州</li>
				</ul>
			</body>
				<script type="text/javascript">
					// 需求：点击“上海”，把上海节点删除
					function run(){
						// 点击弹出警告框
						alert("哈哈");
					}
				</script>

			* --------------------
			<body>
				<ul id="ulId">
					<li>北京</li>
					<li id="shId">上海</li>
					<li>广州</li>
				</ul>
			</body>
				<script type="text/javascript">
					// 需求：点击“上海”，把上海节点删除
					document.getElementById("shId").onclick = function(){	// 匿名函数
						/*
						// alert("呵呵");

						// 获取上海节点
						var sh = document.getElementById("shId");
						// 通过上海节点，获取父节点
						var ul = sh.parentNode;
						// 调用删除节点的方法
						ul.removeChild(sh);
						*/

						// 该方法中有一个关键字this：代表当前对象。因为当前操作的是li，所以，this代表当前的li对象
						this.parentNode.removeChild(this);
					};
				</script>

	* 3 替换节点
		* replaceChild(new,old)	：替换节点。
			* 注意：1 使用父节点调用该方法。
				    2 替换是不是交换
		* 举例
			<body>
				<ul id="ulId1">
					<li>北京</li>
					<li id="shId">上海</li>
					<li>广州</li>
				</ul>

				<ul id="ulId2">
					<li>东城区</li>
					<li id="pdId">浦东区</li>
					<li>黄埔区</li>
				</ul>
			</body>
				<script type="text/javascript">
					// 需求：点击"上海"节点，使用"浦东区"节点替换掉"上海"节点
					document.getElementById("shId").onclick = function(){
						// 获取"浦东区"节点
						var pdq = document.getElementById("pdId");

						// this代表上海
						this.parentNode.replaceChild(pdq,this);
					};
				</script>

	* 4 复制（克隆）节点
		* cloneNode(boolean)	：复制节点。
			* 注意：
				若该节点中还有子节点，如果参数设置为true，则复制子节点；如果参数设置为false，则不复制子节点。
				默认是false，不复制子节点。
		* 举例
			<body>
				<h3>复制节点</h3>
				<button id="btnId" onclick="clone2()">我是按钮</button>

				<div id="divId"></div>
			</body>
				<script type="text/javascript">
					// 需求：复制button按钮的节点，添加到div标签的中间
					function clone2(){
						// 获取按钮的节点
						var btn = document.getElementById("btnId");
						// 复制一个新的节点
						var newBtn = btn.cloneNode(true);
						// 获取div节点对象
						var div = document.getElementbyId("divId");
						// 新节点添加到div下面作为子节点
						div.appendChild(newBtn);
					}

				</script>

** 4.5 innerHTML属性 **

	* 1 innerHTML说明
		* 该属性不是W3C提供的官方标准，但是，几乎所有的浏览器都支持这个属性。
		* 作用：获取和设置标签的文本内容。

		* 举例1
			<body>
				<span id="spanId">我是span区域</span> <br />
			</body>
				<script type="text/javascript">
					// 如果不使用innerHTML属性，获取文本内容。nodeValue：如果是文本对象，则获取的就是文本的内容。

					// 使用innerHTML属性来获取文本内容
					// 获取span标签对象
					var span = document.getElementById("spanId");

					// 获取span标签内容
					//alert(span.innerHTML);

					// 设置span标签内容
					span.innerHTML = "<font color='red'>span新内容</font>";
				</script>

		* 举例2：获取/失去焦点
			* onfocus	：获取焦点。效果详见《新浪邮箱注册之获得焦点.png》
			* onblur	：失去焦点。效果详见《新浪邮箱注册之失去焦点.png》
			
			<body>
				<h4>获取和失去焦点的事件</h4>
				姓名：<input type="text" name="username" id="nameId" onfocus="run1()" onblur="run2()"/> <span id="uspan"></span> <br />
				密码：<input type="password" name="password" id="pwdId" /><span id="uspan"> <br />
			</body>
				<script type="text/javascript">
					function run1(){
						// 操作uspan，动态设置提示内容
						var uspan = document.getElementById("uspan");
						uspan.innerHTML = "不能输入特殊字符";
					}

					function run2(){
						// 异步请求（AJAX的技术：Asynchronous JavaScript And XML（异步JavaScript和XML））：页面不动整个，只有局部给服务器发送一个请求，请求后台，返回后台的内容
						// 用户名输入完毕后，一失去焦点，就应该异步请求去后台对用户名做校验
						var uspan = document.getElementById("uspan");
						uspan.innerHTML = "用户名已存在";
					}
				</script>

** 4.6 应用案例 **

	* 1 全选/全不选/反选 的前台效果
		* 应用场景：
			* 邮箱、网盘中有全选/全不选，选中之后删除
		* 应用案例
			<html>
				<head>
					<title></title>
				</head>
				<body>
					<h3>全选练习</h3>

					<input type="checkbox" id="boxId" onclick="selOrNo()" />全选/全不选<br />

					<input type="checkbox" name="love" />篮球<br />
					<input type="checkbox" name="love" />足球<br />
					<input type="checkbox" name="love" />乒乓球<br />
					<input type="checkbox" name="love" />羽毛球<br />

					<input type="button" value="全选" onclick="selAll()" />
					<input type="button" value="全不选" onclick="selNo()" />
					<input type="button" value="反选" onclick="selOth()"/>
				</body>
					<script type="text/javascript">
						/*
							全选的功能
							1.使用checked属性来控制
							2.让4个复选框都具有checked属性
							3.获取4个复选框
							4.设置每一个复选框checked属性
						*/
						// 全选
						function selAll(){
							// 获取4个复选框
							var inputs = document.getElementsByName("love");
							// 循环遍历。目的：获取每一个input标签对象，设置对象的checked属性
							for(var i = 0; i < inputs.length;i++){
								// 每循环一次，获取一个input标签对象
								var input = inputs[i];
								// 方式1：设置属性。没有加实际的属性
								input.checked = true;	// 对象的属性
	
								// 方式2：在每个一个input标签上加上了checked="checked"属性。F12 → HTML → 查看html代码
								input.setAttribute("checked","checked");	// 特性

								/*
								 两种方式的区别
								方式2，是真正的在html标签上加入了checked属性，称作：特性。操作的是html真正的标签，添加了属性。
								方式1，叫做对象的属性。在内存中存在input对象，input.checked代表对象的一个属性。操作的是内存中的一个对象。
								开发中一般使用方式1较多。
							}
						}

						// 全不选
						function selNo(){
							// 获取4个复选框
							var inputs = document.getElementsByName("love");
							// 循环遍历
							for(var i = 0;i < inputs.length; i++){
								// 设置checked = false
								var input = inputs[i];
								// 设置checked = false
								input.checked = false;

								// 不能使用方式2，因为只要标签上出现了checke属性，不管属性值是true还是false，默认就是被选中的。
								// input.setAttribute("checked","false"); ×
								// 若想是用方式2，需要删除checked属性
								input.removeAttribute("checked");
							}
						}

						// 反选
						function selOth(){
							// 先获取4个复选框
							var inputs = document.getElementsByName("love");
							// 循环遍历。目的：获取每一个input标签对象，设置对象的checked属性
							for(var i = 0; i < inputs.length;i++){
								// 每循环一次，获取一个input标签对象
								var input = inputs[i];

								// 方式1
								if(input.checked == true){
									// 设置属性
									input.checked = false;
								}else{
									input.checked = true;
								}

								// 方式2：上述if~else功能的简写形式
								input.checked = !input.checked;
							}
						}

						// 顶部"全选/全不选"
						function selOrNo(){
							// 
							var input = document.getElementById("boxId");

							// 进行判断。如果input.checked == true,调用全选的方法
							if(input.checked == true){
								// 调用全选方法
								selAll();
							}else{
								selNo();
							}
						}
					</script>

					/* 有一个小bug，通过计数来实现"全选/全不选"前的复选框的选择。事件委托、事件冒泡的高级特性。
			</html>
 
	* 2 列表项的左右选择 的案例 （js+DOM）
		* 
		* 案例代码
			<html>
				<head>
					<title></title>
					<style type="text/css">
						* {margin:0; padding:0;}
						
						div.centent{
							float:left:
							text-align:center;
							margin:10px;
						}

						span {
							display:block;
							margin:2px 2px;
							padding:4px 10px;
							background:#898989;
							cursor:pointer;
							font-size:12px;
							color:white;
						}
					</style>
				</head>
				<body>
					<div class="centent">
						<select multiple="multiple" id="select1" style="width:100px;height:160px;">
							<option value="1">选项1</option>
							<option value="2">选项2</option>
							<option value="3">选项3</option>
							<option value="4">选项4</option>
							<option value="5">选项5</option>
							<option value="6">选项6</option>
							<option value="7">选项7</option>
						</select>
						<div>
							<span id="add" >选中添加到右边&gt;&gt;</span>
							<span id="add_all" >全部添加到右边&gt;&gt;</span>
						</div>
					</div>

					<div class="centent">
						<select multiple="multiple" id="select2" style="width:100px;height:160px;">
							<option value="8">选项8</option>
						</select>
						<div>
							<span id="remove">&lt;&lt;选中删除到左边</span>
							<span id="remove_all">&lt;&lt;全部删除到左边</span>
						</div>
					</div>
				</body>
				<script type="text/javascript">
					/* 
						选择左边条目添加到右边。详见《04-分析下拉列表左右选择.bmp》
					*/
					
					// -----------------------------------------------------------------------
					// 从左边向右添加
					document.getElementById("add").onclick = function(){	//在"add"上绑定匿名函数
						// 1.判断哪几个被选中

						// 获取select2
						var select2 = document.getElementById("select2");

						// 先获取select1
						var select1 = document.getElementById("select");

						// 再获取select1下的所有子节点
						var options = select1.getElementsByTagName("option");

						// 循环遍历。目的：拿到每一个节点，判断是否被选中
						for(var i = 0;i < options.length;i++){
							// 获取每一个option
							var option = option[i];
							// 进行判断selected是否被选中,如果已经选中,直接添加到select2中
							if(option.selected = true){
								// 向select2中添加选中的option
								select2.appendChild(option);

								// 选择多个option时，options长度在变化，详见《05-解释问题.bmp》
								i--;
							}
						}
					};

					// 全部添加到右边
					document.getElementById("add_all").onclick = function(){
						// 获取select2
						var select2 = document.getElementById("select2");

						// 先获取select1，通过select1获取其下的所有option对象
						var select1 = document.getElementById("select1");

						// 获取select1下所有的option对象，循环变脸，把每一个添加到selecet2中
						var options = select1.getElementsByTagName("option");

						// 循环遍历
						for(var i = 0; i < option.length;i++){
							var option = option[i];

							// 直接加入到select2
							select2.appendChile(option);

							i--;
						}
					};

					//------------------------------------------------------
					// 从右向左添加
					document.getElementById("remove").onclick = function(){
						// 获取select2
						var select2 = document.getElementById("select2");

						// 先获取select1
						var select1 = document.getElementById("select");

						// 再获取select2下的所有子节点
						var options = select2.getElementsByTagName("option");

						// 循环遍历。目的：拿到每一个节点，判断是否被选中
						for(var i = 0;i < options.length;i++){
							// 获取每一个option
							var option = option[i];
							// 进行判断selected是否被选中,如果已经选中,直接添加到select2中
							if(option.selected = true){
								// 向select1中添加选中的option
								select1.appendChild(option);

								// 选择多个option时，options长度在变化，详见《05-解释问题.bmp》
								i--;
							}
						}
					};

					document.getElementById("remove_all").onclick = function(){
						// 获取select2
						var select2 = document.getElementById("select2");

						// 先获取select1，通过select1获取其下的所有option对象
						var select1 = document.getElementById("select1");

						// 获取select2下所有的option对象，循环变脸，把每一个添加到selecet1中
						var options = select2.getElementsByTagName("option");

						// 循环遍历
						for(var i = 0; i < option.length;i++){
							var option = option[i];

							// 直接加入到select2
							select1.appendChile(option);

							i--;
						}
					};

					//------------------------------------------------------
					// 双击从左向右添加。逻辑和单击是一样的，只不过得绑定双击事件
					// 绑定在父select节点上，不绑定在子option上。因为option是select的子节点，在父节点上绑定事件后，子节点上也会具有父节点的事件————事件冒泡。事件的高级特性

					docuemnt.getElementById("select1").ondblclick = function(){
						// 获取select2
						var select2 = document.getElementById("select2");

						// 先获取select1
						var select1 = document.getElementById("select");

						// 再获取select1下的所有子节点
						var options = select1.getElementsByTagName("option");

						// 循环遍历。目的：拿到每一个节点，判断是否被选中
						for(var i = 0;i < options.length;i++){
							// 获取每一个option
							var option = option[i];
							// 进行判断selected是否被选中,如果已经选中,直接添加到select2中
							if(option.selected = true){
								// 向select2中添加选中的option
								select2.appendChild(option);

								// 选择多个option时，options长度在变化，详见《05-解释问题.bmp》
								i--;
							}
						}
					};

					// 双击从右向左添加
					document.getElementById("select2").ondbclick = function(){
						// 获取select2
						var select2 = document.getElementById("select2");

						// 先获取select1
						var select1 = document.getElementById("select");

						// 再获取select2下的所有子节点
						var options = select2.getElementsByTagName("option");

						// 循环遍历。目的：拿到每一个节点，判断是否被选中
						for(var i = 0;i < options.length;i++){
							// 获取每一个option
							var option = option[i];
							// 进行判断selected是否被选中,如果已经选中,直接添加到select2中
							if(option.selected = true){
								// 向select1中添加选中的option
								select1.appendChild(option);

								// 选择多个option时，options长度在变化，详见《05-解释问题.bmp》
								i--;
							}
						}
					};
				</script>
			</html>

	* 3 下拉列表的"省市联动"案例  （考点）
		* 北京 选择各个区，还有三级联动。
		* 在没有数据库时，保存数据只能使用数组，比较麻烦。如果使用数据，将数据的关系保存到数据库中，通过查询把数据显示在页面上。现在只能用二维数据来实现操作。

		* 案例代码
			<html>
				<head>
					<title></title>
				</head>
				<body>
					<select id="select1" onchange="show(this.value)"> //this代表网页操作的option对象
						<option value="none">---请选择---</option>
						<option value="北京">北京</option>
						<option value="河北">河北</option>
						<option value="河南">河北</option>
						<option value="山东">山东</option>
						<option value="山西">山西</option>
					</select>

					<select id="select2">

					</select>
				</body>
					<script type="text/javascript">
						var arr = [];
						arr[0] = new Array("北京","海淀区","昌平区","朝阳区","东城区","西城区","丰台区","通州区","怀柔区");
						arr[1] = new Array("河北","石家庄","秦皇岛","衡水","邯郸","邢台","保定","廊坊","唐山");
						arr[2] = new Array("河南","郑州","南阳","安阳","焦作","洛阳","濮阳","新乡");
						arr[3] = new Array("山东","济南","青岛","烟台","威海","日照","泰安","菏泽","济宁");

						/*
							思路：如果选择了北京，需要获取除北京以外，后面所有的元素数据，把这些元素添加到select2中去。
							1.如何去顶选择了哪个省份？
								使用onchange事件
								onchange：选择事件。一般情况和select标签一起使用。this.value：代表页面选择的option
									如果选择的内容发生了变化，才会触发该事件。
							2.如果获取了选择的值，再获取二维数组中，除了下标0位置之后的所有元素
								
						*/
				
						function show(val){
							// alert("哈哈");	//测试无参的show()方法
							// alert(val);		//测试有参的show(this.value)方法

							// 获取select2
							var select2 = document.getElementById("select2");
	
							// 每选择一次，将select2子节点删除清空一次
							// 获取所有的子节点
							var options = select2.getElementByTagName("option");
							for(var x = 0;x < options.length; x++){
								var op = options[x];
								select2.removeChild(op);
								x++;
							}

							// 循环遍历
							for(var i = 0;i < arr.length; i++){
								// 每循环一次，拿到的是二维数组的一个数组
								var inarr = arr[i];
								// 获取每个数组的0位置的元素
								var inStr = inarr[0];
								//alert(inStr);	// 验证拿到的数据是否正确
								// 作对比，如果匹配成功，获取后面的所有元素
								if(val == inStr){
									// 获取从1位置开始的所有元素
									for(var j = 1; j < inarr.length;j++){
										// 获取数组中所有的元素（除了0位置）
										var value = inarr[j];
										// alert(value);	// 验证是否拿到内容
										// 把文本的内容，添加到select2中
										
										// 创建标签对象
										var option = document.createElement("option");
										// 创建文本对象
										var text = document.createTextNode(value);
										// 把文本添加到标签对象下面
										option.appendChild(text);
										// 把标签添加到select2中
										select2.appendChild(option);
									}
								}
							}
						}
					</script>
			</html>
	 
** 4.7 常用事件总结 **

	* 1 鼠标点击事件
		* onclick		：单击事件。应用最多的一个事件
		* ondblclick	：双击事件。
		* mousedown		：鼠标按下事件。（很少用,了解）
		* mouseup		：鼠标松开事件。（很少用,了解）
			* 注意：没有右键的事件。
			
	* 2 加载与卸载事件
		* onload	：加载事件。
			* HTML文件加载完成后，才会触发的事件。经常做一些预处理的操作，页面一加载完成，弹出小广告。
		* unload	：卸载事件。（不常用，了解）。
			* 在关闭浏览器时，触发的事件。关闭浏览器弹出一小广告，比较讨厌的。很多浏览器都不支持该事件了，IE还是支持的。
			
	* 3 聚焦与离焦事件（经常使用的，做效果的时候用）
		* onfocus	：获取焦点的事件。
		* onblur	：失去焦点事件。
		
	* 4 鼠标移动事件
		* onmouseover	：鼠标进入某个区域，停留在区域上，触发事件。
		* mousemove		：（用的不多）
		* mouseout		：（用的不多）
		
	* 5 键盘事件
		* onkepress		：监听键盘，按下某个键，没有松开，触发的事件。
		
	* 6 选择与改变事件
		* onchange		：改变事件。
		* onselect		：
		
	* 7 提交与重置事件
		* onreset	：
		* onsubmit	：控制表单的提交，对表单做校验。
			* （1）必须和表单标签结合在一起使用。
			* （2）作用在form标签上。<form onsubmit="return run()">
			* （3）onsubmit值的写法（固定）：return run()。return 函数名()
			* （4）run()方法需要实现，必须要有返回值。如果返回true，表单就可以提交；如果返回false，表单不能提交。
				* 注意：onblur、onfocus事件是不能阻止onsubmit提交的。
		* 举例
			<body>
				<form action="success.html" method="post" onsubmit="return fun()"> // 报错是因为，MyEclipse默认校验没通过。
				// window → Preferences → MyEclipse → Validation → JavaScript validator for JS files取消该选项后面的两复选框√ → Apply → OK → 重新打开html文件即可
				<table border="1" cellpadding="10" width="50%>
					<tr>
						<td>
							用户名：
						</td>
						<td>
							<input type="text" name="username" id="nameId" onfocus="showName()" onblur="checkName()" />
							<span id="uspan"></span>
						</td>
					</tr>
					<tr>
						<td>
							密&nbsp&nbsp码：
						</td>
						<td>
							<input type="password" id="pwdId" name="password" />
						</td>
					</tr>
					<tr>
						<td>
							确认密码：
						</td>
						<td>
							<input type="password" id="repwdId" name="repassword" />
						</td>
					</tr>
					<tr>
						<td>
							邮&nbsp&nbsp箱：
						</td>
						<td>
							<input type="text" id="emailId" name="email" />
						</td>
					</tr>
					<tr>
						<td colspan="2">
							<input type="submit" value="注册" />
						</td>
					</tr>
				</table>
			</body>
				<script type="text/javascript">
					// 对表单进行校验。只完成不能为空的校验。
						/* 
							表单校验需根据用户需求的规则，根据具体的业务定规则。
							例如：
								用户名：不能输入特殊字符、不能输入中文、还有长度限制
								密  码：数字、字母（大小写）的组合
								邮  箱：@
						*/
					function run(){
						// 校验用户名，不能为空，为空的话不能提交
						var username = document.getElementById("nameId").value;
			
						// 用户名为空，给用户提示
						if(username.trim() == ""){	// 提供了去掉字符串前后的多余空格的方法
							alert("用户名不能为空");	// 也可使用span标签进行提示
							return false;
						}

						/*
							以上是前台做的校验，后台程序还要做一次校验，因为前台毕竟是不安全的，可以绕行，抓包将数据修改后，绕过去。
							前台校验的目的，交互性比较好，提升用户的体验。
						*/

						// 密码不能为空
						var pwd = document.getElementById("pwdId").value;
						if(pwd.trim() == "" || pwd.length < 6){
							alert("密码不能为空或密码长度至少6位");
							return false;
						}

						// 确认密码和密码一致
						var repwd = document.getElementById("repwdId").value;
						if(repwd != pwd){
							alert("两次输入密码不一致");
							return false;
						}
						
						// 邮箱规则	XXX@163.com,一般情况使用正则表达式来判断
						// /^([a-zA-Z0-9_\.\-])+\@(([a-zA-Z0-9\-])+\.)+([a-zA-Z0-9]{2,4})+$/
						var email = document.getEmementById("emailId").value;
						// 完成校验
						if(!/^([a-zA-Z0-9_\.\-])+\@(([a-zA-Z0-9\-])+\.)+([a-zA-Z0-9]{2,4})+$/.text(email)){
							alert("邮箱格式不正确");
							return false;
						}
					}
					
					function showName(){
						var span = document.getElementById("uspan");
						uspan.innerHTML = "请输入用户名";
					}

					// 判断用户名是否为空
					function checkName(){
						var input = document.getElementById("nameId").value;
						if(name == ""){
							var uspan = document.getElementById("uspan");
							uspan.innerHTML = "用户名不能为空";
						}
					}
				</script>

** 4.9 js提交表单 **

	* 举例
		<body>
			<form name="from1" action="success.html" method="post" > 
			<table border="1" cellpadding="10" width="50%>
				<tr>
					<td>
						用户名：
					</td>
					<td>
						<input type="text" name="username"  onfocus="showName()" onblur="checkName()" />
						<span id="uspan"></span>
					</td>
				</tr>
				<tr>
					<td>
						密&nbsp&nbsp码：
					</td>
					<td>
						<input type="password" id="pwdId" name="password" />
					</td>
				</tr>
				<tr>
					<td>
						确认密码：
					</td>
					<td>
						<input type="password" id="repwdId" name="repassword" />
					</td>
				</tr>
				<tr>
					<td>
						邮&nbsp&nbsp箱：
					</td>
					<td>
						<input type="text" id="emailId" name="email" />
					</td>
				</tr>
				<tr>
					<td colspan="2">
						<!-- <input type="submit" value="注册" /> -->
						<input type="button" value="注册2" onclick="mysubmit()" />	//button必须绑定事件才能提交.通过button手动提交，尤其是有多个按钮提交时
					</td>
				</tr>
			</table>
		</body>
			<script type="text/javascript">
				// 通过js提交表单
				function mysubmit(){
					var from1 = document.from1;
					// 提交表单。如果使用这种方式提交表单的话，就不能使用onsubmit事件了
					/*
					// 设置提交路径
					from1.action="";	//设置提交的路径

					// 指定提交方式
					form1.method="get";
					*/
					from1.submit();
				}

				function showName(){
					// 获取用户输入的内容
					var span = document.getElementById("uspan");
					/* 《W3School 全套教程》中，Document对象中有集合。froms[]
					   如果一个页面上有多个form表单的话，可以使用.forms,得到所有的form的引用
						document.form1;	//得到form表单对象的引用
						document.form1.username;//得到的是input文本框对象
					*/
					// var input = document.form1.username;
					//var username = input.value;
					uspan.innerHTML = "请输入用户名";
				}

				// 判断用户名是否为空
				function checkName(){
					// 获取用户名文本框的引用
					var input = document.form1.username;
					// 获取用户输入的值
					var username = input.value;

					if(username == ""){
						var uspan = document.getElementById("uspan");
						uspan.innerHTML = "用户名不能为空";
					}
				}
			</script>

	* name的属性是必须的有的，因为需要提交到后台，如果没有name后台拿不到数据。
	* 使用name，可以不用getElementById()的方法。
 
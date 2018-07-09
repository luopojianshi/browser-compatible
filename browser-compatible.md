#IE 浏览器兼容问题

##一、html 的 hack
	html 的 hack 由注释 <!--  --> 演变而来，在高级浏览器中注释不会被加载，把 IE 浏览器的兼容代码写在注释中，IE 浏览器会识别。
注:
#####	①  用于写兼容的注释，标签内首尾都要加 ! 感叹号
#####	②  单词都写在一对中括号中
#####	③  IE 和版本号之间要加空格
#####	④  不加比较单词，表示只兼容这一个版本
	比较单词:
		lt  = less than         	小于
		lte = less than or equal	小于等于
		gt  = less than         	大于
		gte = less than or equal	大于等于

	例子:
		<!--[if IE 6]>
			<p>只有 IE6 认识我</p>
		<![endif]-->
		<!--[if gte IE 9]>
			<h1>大于等于 IE9 的浏览器能看到</h1>
		<![endif]-->
		<!--[if lte IE 8]>
			<h1 class="red">您的浏览器版本过低，IE8及以下版本不支持新样式，请更换浏览器</h1>
		<![endif]-->


##二、css 的 hack

设置 css 的 hack 要注意的是 css 样式的层叠性，给同一个元素设置的兼容写法，必须写在后面，否则会被层叠覆盖掉。

###1、属性的 hack
#####	①  只兼容 IE6 的 hack
		hack符: -或_，当做前缀写在属性前面，中间不能加空格
		在属性名前面加短横-或者下划线_（原理：高级浏览器及其他浏览器会认为这个前缀符号是一个 unknown property name），未知的属性，不会报错，不予加载。
		 background: red;	// 高级浏览器识别
		_background: red;	// 仅 IE6 识别
#####	②  兼容 IE6、7 的 hack
		hack 符： ` ~ ! @ # $ % ^ & * ( ) + = [ ] | < > , . 中的任一字符，作为前缀写在属性前面
		  background: red;	// 高级浏览器识别
		! background: red;	// 仅 IE6、7 识别
#####	③  只兼容 IE8 的 hack
		hack符：\0/，必须写在属性值与分号之间，中间不能加空格
		background: red;		// 高级浏览器识别
		background: pink\0/;	// 仅 IE8 识别
#####	④  兼容 IE8、9、10 的 hack
		hack符：\0，必须写在属性值与分号之间，中间不能加空格
		background: red;	// 高级浏览器识别
		background: pink\0;	// IE8、9 识别
#####	⑤  兼容 IE6、7、8、9、10
		hack符：\9，必须写在属性值与分号之间，中间不能加空格

###2、选择器的 hack

	给选择器添加 hack，这个选择器中的样式都是 IE 兼容模式，其他高级浏览器不识别，同理，给同一个选择器设置的兼容模式要写在高级浏览器可识别的常规样式后面，否则会被层叠

#####	①  IE6 及以下版本的 hack
		hack符：* html，* 和 html 之间有空格，再加一个空格，后面写选择器
		<!--常规写法-->
			.box {
				width: 200px;
				height: 200px;
				border-radius: 50%;
				background: yellowgreen;	
			}
		<!--兼容写法-->
			* html .box {
				with: 100px;
				height: 100px;
				background: skyblue;
			}
#####	②  IE7 及以下版本的 hack
		hack符：,  英文的逗号，写在选择器后面，不加空格
		.box, {
			background: #999;
			border: 1px solid red;
		}
#####	③  兼容 IE6 以外的其他版本的 hack
		hack符：html>body，写在选择器前面，与选择器之间有一个空格隔开
		html>body .box {
			background: yellow;
		}
#####	④  兼容 IE6、7 以外的版本的 hack
		hack符：html>/**/ 或 html~/**/ ，写在选择器前面，与选择器之间有一个空格隔开


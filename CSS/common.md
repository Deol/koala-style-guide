# 1. 基础规范

## 1.1 代码风格

### 1.1.1 文件
[建议]：使用无bom的utf-8格式  
原因：bom可以理解成作为文件头的一种声明编码格式的字段。这里不建议使用，是因为有可能有些编辑器不认识这个字段导致不必要的麻烦。

### 1.1.2 缩进
[强制]：使用四个空格为单位的缩进。  

```css
.selector {
□□□□margin: 0;
}
```

### 1.1.3 空格
[强制]：选择器跟 { 之间必须有空格

```css
.selector□{
    margin: 0;
}
```

[强制]：属性名与之后的 : 之间必须无空格，: 和之后的属性值必须有空格

```css
.selector {
    margin:□0;
}
```

[强制]：列表属性值写在单行的时候，必须有空格

```css
.selector {
    font-family: Arial,□sans-serif;
}
```

### 1.1.4 行长度
[强制]：单行的长度不宜超过120字符。  
注：这里有一个例外，如果像url这种不可分割的属性值过长，就让他过长吧。  
[建议]：对于很长的单行属性，可以在逗号处合理的换行，并保持整齐。

```css
background-image: -webkit-gradient(
    linear,
    left bottom,
    left top,
    color-stop(0.04, rgb(88,94,124)),
    color-stop(0.52, rgb(115,123,162))
);
```

### 1.1.5 选择器
[强制]：当一个规则的选择器有多个的时候，选择器合并一行，并用逗号隔开

```css
.m-list li,.m-list h3 {width: 100px;padding: 10px;border: 1px solid #ddd;}
```

[强制]：'>','+','~' 这些选择器的左右都需要一个空格隔开。

```css
main > naiv {
    padding: 10px;
}
label + input {
    margin-left: 5px;
}
```

### 1.1.6 属性
[强制]：单行写完一个选择器定义。（便于选择器的寻找和阅读，也便于插入新选择器和编辑，便于模块等的识别。去除多余空格，使代码紧凑减少换行。）  
注：这里如果使用的是类似mcss的预处理器，由于编译之后会自动合并成一行，所以在写mcss类的代码时，可以换行。

```css
.m-list li,.m-list h3{width:100px;padding:10px;border:1px solid #ddd;}
```

[强制]：属性定义结束必须使用分号作为结尾  

```css
.selector {
    margin: 0;
}
```

## 1.2 通用

### 1.2.1 选择器
[强制]：如果没有必要，不能给类选择器前面加类型选择器进行限定

```css
/* good */
#error,
.danger-message {
    font-color: #c00;
}
/* bad */
dialog#error,p.danger-message {
    font-color: #c00;
}
```

[建议]：选择器的嵌套尽量不要超过五级，位置靠后的条件应该尽可能精确

```css
/* good */
#username input {}
.comment .avatar {}
/* bad */
.page .header .login #username input {}
.comment div * {}
```

### 1.2.2 属性缩写
[建议]：在属性能缩写的情况下，尽量缩写属性

```css
/* good */
.post {
    font: 12px/1.5 arial, sans-serif;
}
/* bad */
.post {
    font-family: arial, sans-serif;
    font-size: 12px;
    line-height: 1.5;
}
```

### 1.2.3 属性顺序
[建议]：先显示定位布局类属性，后盒模型等自身属性，最后是文本类及修饰类属性。  

显示属性 | 自身属性 | 文本属性和其他修饰
---|---|---
display | width | font
visibility | height | text-align
positon | margin| text-decoration
float | padding| vertical-align
clear | border| white-space
list-style | overflow| color
top | min-width| background

```css
.m-box{position:relative;width:600px;margin:0 auto 10px;text-align:center;color:#000;}
```

## 1.3 值与单位

### 1.3.1 使用单引号
[强制]：省略url引用中的引号，其他需要引号的地方使用单引号。

```css
.m-box:after{content:'.';}
```

### 1.3.2 url
[强制]：url函数中的路径不加引号

```css
body {
    background: url(bg.png);
}
```

[建议]：url的协议头可以省略(这样会自动匹配协议，兼容性更高)

```css
body {
    background: url(//baidu.com/img/bg.png) no-repeat 0 0;
}
```

### 1.3.3 数值
[强制]：当数值为0开头的小数时，省略前面的0

```css
/* good */
panel {
    opacity: .8
}
/* bad */
panel {
    opacity: 0.8
}
```

### 1.3.4 长度
[强制]：当属性的值为0且单位为长度的时候，后面的px等可以省略。

```css
/* good */body {
    padding: 0 5px;
}
/* bad */body {
    padding: 0px 5px;
}
```

### 1.3.5 颜色
[强制]：RGB颜色必须使用十六进制形式#rrggbb。如果有alpha，则需要在每个逗号后面加一个空格。

```css
/* good */
.success {
    box-shadow: 0 0 2px rgba(0, 128, 0, .3);
    border-color: #008000;
}
/* bad */
.success {
    box-shadow: 0 0 2px rgba(0,128,0,.3);
    border-color: rgb(0, 128, 0);
}
```

[强制]：颜色可以缩写的时候必须缩写。
[强制]：颜色不允许命名色值。

```css
/* good */
.success {
    color: #90ee90;
}
/* bad */
.success {
    color: lightgreen;
}
```

## 1.4 命名分类

### 1.4.1 布局
- 布局（grid）（.g-）：将页面分割为几个大块，通常有头部、主体、主栏、侧栏、尾部等

```css
.g-sd{float:left;width:300px;}
```

语义 | 命名 | 简写
---  | ---  | ---
文档 | doc  | doc
头部 | head |	hd
主体 |	body|	bd
尾部 |	foot|	ft
主栏 |	main|	mn
主栏子容器|	mainc|	mnc
主导航 | mainnav | mainnav
侧栏|	side|	sd
侧栏子容器|	sidec|	sdc
盒容器|	wrap/box|	wrap/box

### 1.4.2 模块与原件
- 模块（module）（.m-）：通常是一个语义化的可以重复使用的较大的整体！比如导航、登录、注册、各种列表、评论、搜索等！  
- 元件（unit）（.u-）：通常是一个不可再分的较为小巧的个体，通常被重复用于各种模块中！比如按钮、输入框、loading、图标等！

```css
/* 模块 */
.m-logo{width:200px;height:50px;}
/* 元件 */
.u-btn{height:20px;border:1px solid #333;}
```

语义 |	命名 |	简写
---  | ---  | ---
导航 |	nav	| nav
子导航|	subnav|	snav
面包屑|	crumb|	crm
菜单|	menu|	menu
选项卡|	tab	|tab
标题区|	head/title|	hd/tt
内容区|	body/content|	bd/ct
列表|	list|	lst
表格|	table|	tb
表单|	form|	fm
热点|	hot|	hot
排行|	top|	top
登录|	login|	log
标志|	logo|	logo
广告|	advertise|	ad
搜索|	search|	sch
幻灯|	slide|	sld
提示|	tips|	tips
帮助|	help|	help
新闻|	news|	news
下载|	download|	dld
注册|	regist|	reg
投票|	vote|	vote
版权|	copyright|	cprt
结果|	result|	rst
标题|	title|	tt
按钮|	button|	btn
输入|	input|	ipt

### 1.4.3 功能
- 功能（function）（.f-）：为方便一些常用样式的使用，我们将这些使用率较高的样式剥离出来，按需使用，通常这些选择器具有固定样式表现，比如清除浮动等！不可滥用！(在当前的几个项目中，这个f-用的很少，都写在u或者m里面了)  
- 注：在这里的 .f-xxx 适用于重用度比较高的功能样式，也不能只要有功能类的样式都放在这里。

语义|	命名|	简写
---  | ---  | ---
浮动清除|	clearboth|	cb
向左浮动|	floatleft|	fl
向右浮动|	floatright|	fr
内联块级|	inlineblock|	ib
文本居中|	textaligncenter|	tac
文本居右|	textalignright|	tar
文本居左|	textalignleft|	tal
垂直居中|	verticalalignmiddle|	vam
溢出隐藏|	overflowhidden|	oh
完全消失|	displaynone|	dn
字体大小|	fontsize|	fs
字体粗细|	fontweight|	fw

```css
/* 功能 */
.f-tac{text-align:center;}
```

### 1.4.4 状态
- 状态（.z-）：为状态类样式加入前缀，统一标识，方便识别，她只能组合使用或作为后代出现（.u-ipt.z-dis{}，.m-list li.z-sel{}），具体详见命名规则的扩展相关项。
- 注：如果只存在两种状态，可以把其中一种状态设置为默认状态。状态不能单独使用，需要有适当的前缀使它的语义明确。

语义	|命名|	简写
---  | ---  | ---
选中|	selected|	sel
当前|	current|	crt
显示|	show|	show
隐藏|	hide|	hide
打开|	open	|open
关闭|	close|	close
出错|	error|	err
不可用|	disabled|	dis

```css
/* 状态 */
.m-list li.z-sel{background:#f4f4f4;}
```

### 1.4.5 统一处理
- 重置（reset）和默认（base）（tags）：消除默认样式和浏览器差异，并设置部分标签的初始样式，以减少后面的重复劳动！你可以根据你的网站需求设置！

```css
/* 统一调用背景图 */
.m-logo a,.m-nav a,.m-nav em{background:url(images/sprite.png) no-repeat 9999px 9999px;}
/* 统一清除浮动 */
.g-bdc:after,.m-dimg ul:after,.u-tab:after{display:block;visibility:hidden;clear:both;height:0;overflow:hidden;content:'.';}
```

### 1.4.6 皮肤
- 皮肤（skin）（.s-）：如果你需要把皮肤型的样式抽离出来，通常为文字色、背景色（图）、边框色等，非换肤型网站通常只提取文字色！非换肤型网站不可滥用此类！

语义|	命名|	简写
---  | ---  | ---
字体颜色|	fontcolor|	fc
背景|	background|	bg
背景颜色|	backgroundcolor|	bgc
背景图片|	backgroundimage|	bgi
背景定位|	backgroundposition|	bgp
边框颜色|	bordercolor|	bdc

```css
/* 皮肤 */
.s-fc,a.s-fc:hover{color:#fff;}
```

### 1.4.7 重置与默认
- 重置（reset）和默认（base）（tags）：消除默认样式和浏览器差异，并设置部分标签的初始样式，以减少后面的重复劳动！你可以根据你的网站需求设置！

```css
/* 重置 */
div,p,ul,ol,li{margin:0;padding:0;}
/* 默认 */
strong,em{font-style:normal;font-weight:bold;}
```

## 1.5 命名规则

### 1.5.1 使用单个字母+"-"为前缀
- 布局（grid）（.g-）；模块（module）（.m-）；元件（unit）（.u-）；功能（function）（.f-）；皮肤（skin）（.s-）；状态（.z-）。  
- 对以上的解释详情参见：分类方法中的“CSS内部的分类及其顺序”。  
- 注：在你样式中的选择器总是要以上面前五类开头，然后在里面使用后代选择器。
如果这五类不能满足你的需求，你可以另外定义一个或多个大类，但必须符合单个字母+"-"为前缀的命名规则，即 .x- 的格式。  
特殊：.j-将被专用于JS获取节点，请勿使用.j-定义样式。

### 1.5.2 后代选择器命名
- 约定不以单个字母+"-"为前缀且长度大于等于2的类选择器为后代选择器，如：.item为m-list模块里的每一个项，.text为m-list模块里的文本部分：.m-list .item{}.m-list .text{}。
- 一个语义化的标签也可以是后代选择器，比如：.m-list li{}。
- 不允许单个字母的类选择器出现，原因详见下面的“模块和元件的后代选择器的扩展类”.    
- 通过使用后代选择器的方法，你不需要考虑他的命名是否已被使用，因为他只在当前模块或元件中生效，同样的样式名可以在不同的模块或元件中重复使用，互不干扰；在多人协作或者分模块协作的时候效果尤为明显！
后代选择器不需要完整表现结构树层级，尽量能短则短。
- 注：后代选择器不要在页面布局中使用，因为污染的可能性较大；

```css
/* 这里的.itm和.cnt只在.m-list中有效 */
.m-list{margin:0;padding:0;}
.m-list .itm{margin:1px;padding:1px;}
.m-list .cnt{margin-left:100px;}
/* 这里的.cnt和.num只在.m-page中有效 */
.m-page{height:20px;}
.m-page .cnt{text-align:center;}
.m-page .num{border:1px solid #ddd;}
```

### 1.5.3 命名应简约而不失语义

```css
/* 反对：表现化的或没有语义的命名 */
.m-abc .green2{}
.g-left2{}
/* 推荐：使用有语义的简短的命名 */
.m-list .wrap2{}
.g-side2{}
```

### 1.5.4 相同语义的不同类命名
- 方法：直接加数字或字母区分即可（如：.m-list、.m-list2、.m-list3等，都是列表模块，但是是完全不一样的模块）。  
其他举例：.f-fw0、.f-fw1、.s-fc0、.s-fc1、.m-logo2、.m-logo3、u-btn、u-btn2等等。  
- 注：这里的区分不建议直接加数字区分，这样语义化的效果比较差。可以为了跟拓展类区分，可以使用驼峰，例如：.m-list,.m-listTop,m-listBottom等。

### 1.5.5 模块和元件的扩展类的命名方法
- 当A、B、C、...它们类型相同且外形相似区别不大，那么就以它们中出现率最高的做成基类，其他做成基类的扩展。  
- 方法：+“-”+数字或字母（如：.m-list的扩展类为.m-list-1、.m-list-2等）。  
补充：基类自身可以独立使用（如：class="m-list"即可），扩展类必须基于基类使用（如：class="m-list m-list-2"）。  
- 如果你的扩展类是表示不同状态，那么你可以这样命名：u-btn-dis，u-btn-hov，m-box-sel，m-box-hov等等，然后像这样使用：class="u-btn u-btn-dis"。  
- 如果你的网站可以不兼容IE6等浏览器，那么你标识状态的方法也可以采取独立状态分类（.z-）方法：.u-btn.z-dis，.m-box.z-sel，然后像这样使用：class="u-btn z-dis"。  
- 注：这里关于类的扩展，也可以考虑把基类以外的状态用 .z-xxx 来做，需要考虑实际情况。并且，这里的 .z-xxx 还是需要加上足够表达语义的前缀的。

### 1.5.6 模块和元件的后代选择器的扩展类
- 有时候模块内会有些类似的东西，如果你没有把它们做成元件和扩展，那么也可以使用后代选择器和扩展。  
- 后代选择器：.m-login .btn{}。  
- 后代选择器扩展：.m-login .btn-1{}，.m-login .btn-dis{}。  
- 同样也可以采取独立状态分类（.z-）方法：.m-login  .btn.z-dis{}，然后像这样使用：class="btn z-dis"。
- 注：此方法用于类选择器，直接使用标签做为选择器的则不需要使用此命名方法。
- 注：为防止后代选择器的扩展类和大类命名规范冲突，后代选择器不允许使用单个字母。比如：.m-list .a{}是不允许的，因为当这个.a需要扩展的时候就会变成.a-bb，这样就和大类的命名规范冲突。

### 1.5.7 分组选择器有时可以代替扩展方法
- 有时候虽然两个同类型的模块很相似，但是你希望他们之间不要有依赖关系，也就是说你不希望使用扩展的方法，那么你可以通过合并选择器来设置共性的样式。  
- 使用本方法的前提是：相同类型、功能和外观都相似，写在同一片代码区域方便维护。

```css
/* 两个元件共性的样式 */
.u-tip1,.u-tip2{}
.u-tip1 .itm,.u-tip2 .itm{}
/* 在分别是两个元件各自的样式 */
/* tip1 */
.u-tip1{}
.u-tip1 .itm{}
/* tip2 */
.u-tip2{}
.u-tip2 .itm{}
```

### 1.5.7 防止污染和被污染
- 当模块或元件之间互相嵌套，且使用了相同的标签选择器或其他后代选择器，那么里面的选择器就会被外面相同的选择器所影响。  
- 所以，如果你的模块或元件可能嵌套或被嵌套于其他模块或元件，那么要慎用标签选择器，必要时采用类选择器，并注意命名方式，可以采用.m-layer .layerxxx、.m-list2 .list2xxx的形式来降低后代选择器的污染性  

## 1.6 兼容性

### 1.6.1 属性前缀
[强制]：带私有属性前缀的由长到短排列，并按照冒号对齐
```css
.box {
    -webkit-box-sizing: border-box;
       -moz-box-sizing: border-box;
            box-sizing: border-box;
}
```

- 注：在预处理器下，这么写。如果在纯css的环境下，建议写成一行。

### 1.6.2 hack
[建议]：能不使用hack就不使用hack

```css
.box {
    _display: inline; /* fix double margin */
    float: left;
    margin-left: 20px;
}
.container {
    overflow: hidden;
    *zoom: 1; /* triggering hasLayout */
}
```

## 1.7 注释
注释格式：/* 注释文字 \*/  
- 对选择器的注释统一写在被注释对象的上一行，对属性及值的注释写于分号后。  
- 注释内容两端需空格，已确保即使在编码错误的情况下也可以正确解析样式。  
- 在必要的情况下，可以使用块状注释，块状注释保持统一的缩进对齐。  
原则上每个系列的样式都需要有一个注释，言简意赅的表明名称、用途、注意事项等。

```css
/* 块状注释文字
 * 块状注释文字
 * 块状注释文字
 */
.m-list{width:500px;}
.m-list li{height:20px;line-height:20px;/* 这里是对line-height的一个注释 */overflow:hidden;}
.m-list li a{color:#333;}
/* 单行注释文字 */
.m-list li em{color:#666;}
```

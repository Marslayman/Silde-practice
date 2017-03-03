## Use only CSS & HTML to create a single page restaurant exhibition page

>This is just a practice for learning CSS and HTML, so the whole page is not responsible and write with no any javascript in the page.

### What I learned in this practice

- **how to extract required elements from the original design file**
- **how to write the basic frame of the page in HTML**
- **css knowledge learned in this practice**

---

### How to extract required elements from the original design file

In this practice ,the PSD file I used as the original file was downloaded from the template website **[Pixlhint](http://pixelhint.com/)** 

Below are some summaries I learned from this practice about extracting from original design file.

- **Give a general look to the design file**

	> When get the design file ,the first thing should be openning it in a gallery view to have a general look about the whole page.

	> To determine which part should be common part and which part should be individual part in the page ,so that can determine the file structure when start to write the page code.

- **Do not put every element to a picture** 
	
	> When start to get material from the design file ,should always think about it ,what do I need to cut as a picture and what I can use CSS to get the same result.

	>it is better to use CSS if the material is easy to get rather than put it as a picture

### How to write the basic frame of the page in HTML

In the basic HTML page ,I use HTML5 tags to structure the page frame, semantization is part of the HTML5 standard ,semantization tags such as `<header>` ,`<nav>` ,`<artile>` ,`<section>`, `<footer>` and so on.

When add selector to tags in the page, we should consider which tag we should add a selector ,not just used for CSS but also need to consider the usage when we need to use javascript in the page. The selector name should be **WYSIWYG**, such as `class="header-nav-list"` or `class="nav-list-item"`.

### CSS knowlege learned in this practice

Completed this page ,below are some knowledge checkpoints I learned.

- **Reset the style for default element**

	>Below are some mostly used reset css style 

	<pre>
	html, body, div, span, object, iframe, blockquote,p, pre, a, h4,abbr, address, cite, code, del, dfn, em, img, ins, kbd, q, s, samp, small, strike, strong, sub, sup, tt, var, b, u, i, center, dl, dt, dd, ol, ul, li, fieldset, form, label, legend, table, caption, tbody, tfoot, thead, tr, th, td, article, aside, canvas, details, embed, figure, figcaption, footer, header, hgroup, menu, nav, output, ruby, section, summary, time, mark, audio, video {
	margin: 0;
	padding: 0;
	border: 0;
	font-size: 100%;
	font: inherit;
	vertical-align: baseline;
	outline: none;
	box-sizing: border-box;
	}
	</pre>
	<pre>
	/* html { height: 101%; }   //强制出现滚动条 */
	body {
		font-size: 62.5%;
		line-height: 1;
		font-family: Arial, Tahoma, sans-serif;
	}
	article, aside, details, figcaption, figure, footer, header, hgroup, menu, nav, section {
		display: block;
	}
	ol, ul {
		list-style: none;
	}
	blockquote, q {
		quotes: none;
	}
	blockquote:before, blockquote:after, q:before, q:after {
		content: '';
		content: none;
	}
	strong {
		font-weight: bold;
	}
	table {
		border-collapse: collapse;
		border-spacing: 0;
	}
	img {
		border: 0;
		max-width: 100%;
	}
	a{
		text-decoration: none;
	}
	p {
		font-size: 1.2em;
		line-height: 1.0em;
		color: #333;
	}
	</pre>
	
	> **clearfix** style is used to clear the float ,make sure the father container's height not be 0 when father container's height is not defined.
	> 
	> This **clearfix** selector should be added to father container's sytle sheet.
	> 
 	> The comment part in below code block for float clear seems not work in the browser.

	<pre>
	/* .clearfix:before, .container:after,.clearfix:after {
	content: "";
	display: table;
	}
	.clearfix:after {
		clear: both;
	} */
	.clearfix:after {
		content: ".";
		display: block;
		clear: both;
		visibility: hidden;
		line-height: 0;
		height: 0;
	}
	
	html[xmlns] .clearfix {
		display: block;
	}
	
	\* html .clearfix {
		height: 1%;
	}
	/* IE 6/7 */
	.clearfix {
		zoom: 1;
	}
	</pre>
- **Use transform to achieve vertical center layout**
	> In order to get the vertical center layout ,we need `position:absulute;` attribute.
	> 
	> For element which has certain `width` and `height` ,we can use `margin` attribute to get what we want 
	>  
	> For element with uncertain `width` and `height` ,we can use `tranform` and `translate` attributes to get what we want

	<pre>
	/* Full screen vertical center layout ,we need to set html and body tag first */
    html,body{
    width:100%;
    height:100%;
	}
	/ * When know the certain width and height,use margin attribute * /
    {
	position:absolute;
	top:50%;
	left:50%;
	margin-left:-width/2;
	margin-top:-height/2;
	}
	/ * use tranform attribute to get vertical center layout when the width and height are not certain * /
	.index-banner-text{
	position:absolute
	top: 50%;
	left: 50%;
	text-align: center;
	color: #FFF;
	\-webkit-transform: translate(-50%, -50%);
	        transform: translate(-50%, -50%);
	overflow: hidden;
	}
	</pre>

- **display inline-block get 4px space**

	>Set `Font-size` attirbute to 0px in father container in CSS to get rid of the 4px space for inline-block child element

	<pre>
	.feature-panel-btn-group{
		float: right;
		margin-top: 23px;
		font-size: 0px; /*清除子元素的inline-block的4px间距*/
	}
	.feature-panel-btn{
		display: inline-block;
		width: 8px;
		height: 8px;
		margin-right: 10px;
		background-color: #dedede;
		border-radius: 50%;
		background-color: 
	}
	</pre>

- **The usage of `overflow` attribute**

	> Use overflow attribute adding to father container to achieve picture horizental list with float

	<pre>
	/ * 保证浮动能排成两列，container 的overflow保证为hidden * /
	.menu>.container{
		overflow: hidden;
	}
	.menu-list{
		width: 1160px;
		margin-top: 78px;
	}
	.menu-list >.menu-list-item{
		float: left;
		width: 520px;
		height: 96px;
		margin-right: 60px;
	}
	</pre>

- **User `border` attribute to achieve triangle**

	<pre>
	.menu-tip-flag:after{
		content: "";
		width: 0px;
		height: 0px;
		position: absolute;
		left: 0;
		bottom: 0;
		border-left: solid 78px #f34949;
		border-right: solid 78px #F34949;
		border-bottom: solid 10px #fff;
	}
	</pre>
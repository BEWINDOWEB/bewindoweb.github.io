# CSS：两个inline-block的a标签之间有空隙
`【系统环境】windows 8`  
`【操作内容】phpstorm / css`  
`【解决方案验证次数】3次`  
## <i class="fa fa-question-circle"></i> 出现问题
编写CSS时发现inline-block显示的a标签之间有空隙
![](assets/001/20180619-5d58bbab.png)  
【HTML】
```html
<div class="dishes-sort">
    <a class="dishes-sort-item dsi-select">最多点击</a>
    <a class="dishes-sort-item dsi-select">最新</a>
    <a class="dishes-sort-item dsi-select">名称</a>
</div>
```
```css
.dishes-sort-item{
	width:auto;
	height:30px;
	line-height:30px;
	background: #fff;
	color:#f2f2f2;
	font-size:14px;
	max-width: 190px;
	text-align:center;
	display:inline-block;
	padding:0 20px;
	cursor:pointer;
}
```
## <i class="fa fa-bullseye"></i> 根本原因
a标签间距的默认样式问题
## <i class="fa fa-check-circle"></i> 解决方法
根据[《CSS 怎么清除多个a标签之间的默认空白空隙/间距？》](http://www.ylefu.com/post/353.html)的四种解决方法，采用float（第三种）得到了解决（其他的没尝试）。   
【方法1】父元素设置font-size:0
```html
<div class="demo demo1">
    <a href="#">底部链接1</a>
    <a href="#">底部链接2</a>
</div>
.demo1{
    font-size: 0;
}
.demo1 a{
    font-size: 14px;/*这里一定要设置，不然文本内容将不显示*/
}
```
【方法2】a标签内容写在一行
```html
<div class="demo">
    <a href="#">底部链接1</a><a href="#">底部链接2</a>
</div>
```
【方法3】float浮动（本文采用）
```html
.dishes-sort-item{
	width:auto;
	height:30px;
	line-height:30px;
	background: #fff;
	color:#f2f2f2;
	font-size:14px;
	max-width: 190px;
	text-align:center;
	display:inline-block;
	padding:0 20px;
	cursor:pointer;
	float:left;
}
```
![](assets/001/20180619-4f50dc7f.png)  
【方法4】设置letter-spacing
```html
<div class="demo demo3">
    <a href="#">底部链接1</a>
    <a href="#">底部链接2</a>
</div>
.demo3{
    letter-spacing: -999px;
}
.demo3 a{
    letter-spacing: 0;
}
```

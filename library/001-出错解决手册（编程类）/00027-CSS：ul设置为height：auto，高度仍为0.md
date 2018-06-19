# CSS：ul设置为height：auto，高度仍为0
`【系统环境】windows 8`  
`【操作内容】phpstorm / css`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
div、ul、li嵌套使用时，ul设置了height:auto，li有层高但是是float的，ul的高度仍然为0。  
【HTML】
```html
<div class="dishes-show-table">
        <ul>
            <li>
                <a><img width="60" height="60" src=""></a>
                <a>土豆</a>
                <span>1个</span>
            </li>
            <li>
                <a><img width="60" height="60" src=""></a>
                <a>土豆</a>
                <span>1个</span>
            </li>
            <li>
                <a><img width="60" height="60" src=""></a>
                <a>土豆</a>
                <span>1个</span>
            </li>
        </ul>
</div>
```
【CSS】
```css
.dishes-show-table{
	float:left;
	margin:20px auto;
	width:100%;
	height:auto;
	text-align:center;
}
.dishes-show-table ul{
	list-style:none;
	width:600px;
	height:auto;
	padding:0;
	text-align:center;
	margin:0 auto;
	border-left: 1px solid #eee;
	border-top: 1px solid #eee;
}


.dishes-show-table li{
	border-right: 1px solid #eee;
	border-bottom: 1px solid #eee;
	box-sizing:border-box;
	width:50%;
	height:70px;
	cursor:default;
	float:left;
}
.dishes-show-table img{
	box-sizing:border-box;
	height:60px;
	cursor:default;
	float:left;
}

.dishes-show-table li a{
	display:block;
	float:left;
	font-size:14px;
	line-height:60px;
	padding:5px;

}

.dishes-show-table li span{
	display:block;
	float:right;
	line-height:60px;
	font-size:14px;
	padding:5px;
}
```
## <i class="fa fa-bullseye"></i> 根本原因
据说和float有关系。
## <i class="fa fa-check-circle"></i> 解决方法
参考的[《div ul li 嵌套后解决高度自适应方法》](https://blog.csdn.net/feicongcong/article/details/70670132)，在ul的后面加上：
```css
overflow:hidden;
clear:both;
```
奇迹般地有高度了。

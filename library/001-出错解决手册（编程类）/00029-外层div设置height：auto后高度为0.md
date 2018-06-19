# 外层div设置height:auto后高度为0
`【系统环境】windows 8`  
`【操作内容】phpstorm / css`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
外层div设置height：auto后高度为0，例如：   
【HTML】
```html
<div class="outer">
        <div class="inner" ></div>
</div>
```
【CSS】
```css
.outer{
	width:800px;
	height:auto;
}
.inner{
	width:180px;
	height:180px;
	background-color:#f8f8f8;
	float:left;
}
```
就算内层div有高度，外层div高度仍然为0。
## <i class="fa fa-bullseye"></i> 根本原因
未知
## <i class="fa fa-check-circle"></i> 解决方法
在外层div加入overflow:hidden即可恢复，例如：
```
.outer{
	width:800px;
	height:auto;
	overflow:hidden;
}
```

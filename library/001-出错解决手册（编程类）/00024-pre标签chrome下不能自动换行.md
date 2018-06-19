# pre标签chrome下不能自动换行
`【系统环境】windows 8`  
`【操作内容】css的pre标签`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
用CSS的pre标签时，虽然能识别换行，但是在chrome浏览器下文字会超出pre的外框。
## <i class="fa fa-bullseye"></i> 根本原因
不同浏览器需要不同地去设置。
## <i class="fa fa-check-circle"></i> 解决方法
根据[《又能用pre,又能用自动换行》](https://zhidao.baidu.com/question/140406137.html)的百度知道，一个30赞0踩的回答果然是有效的：
```css
pre{
    white-space: pre-wrap;       
    white-space: -moz-pre-wrap;  
    white-space: -pre-wrap;      
    white-space: -o-pre-wrap;    
    word-wrap: break-word;       
}
```

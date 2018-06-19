# phpstorm报JS书写错误：definenation are not supported
`【系统环境】windows 8`  
`【操作内容】phpstorm`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
phpstorm报书写错误：xxx definenation are not supported by current JavaScrpit version
## <i class="fa fa-bullseye"></i> 根本原因
系统默认JS版本没有那么高
## <i class="fa fa-check-circle"></i> 解决方法
打开phpstorm，`文件`→`设置`→`语言和框架`→`JavaScript`→`JavaScript language version`，选择`ECMAScript6`。
![](assets/001/20180619-10b7ece4.png)  

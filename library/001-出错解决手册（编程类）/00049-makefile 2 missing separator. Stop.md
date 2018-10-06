# make的时候出错 makefile:2: *** missing separator. Stop.
`【系统环境】ubuntu14`  
`【操作内容】shell(dash)`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
编写完makefile，执行make的时候报错：
```
makefile:2: *** missing separator. Stop.
```
## <i class="fa fa-bullseye"></i> 根本原因
makefile开头必须是`TAB键`而不能用`空格`
## <i class="fa fa-check-circle"></i> 解决方法
把所有开头的 **空格** 替换为 **TAB**

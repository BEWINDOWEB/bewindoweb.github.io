# maven编译出错：No compiler is provided in this environment.
`【系统环境】windows 10`  
`【操作内容】maven`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
在使用命令行maven编译的时候：
```
mvn clean compile
```
提示出错：  
[ERROR] No compiler is provided in this environment. Perhaps you are running on a JRE rather than a JDK?
## <i class="fa fa-bullseye"></i> 根本原因
JDK路径没有被正确配置
## <i class="fa fa-check-circle"></i> 解决方法
我的解决方法是：换用管理员模式的CMD，就OK了。  
网上的解决方法是：修改IDE的Execution Environments为JDK。

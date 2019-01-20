# No compiler is provided in this environment
`【系统环境】windows 10`  
`【操作内容】maven 3.5`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
CMD下执行mvn clean compile编译项目报错：
```
No compiler is provided in this environment, perhaps you are running on a JRE rather than a JDK.
```
## <i class="fa fa-bullseye"></i> 根本原因
没有权限打开tools.jar
## <i class="fa fa-check-circle"></i> 解决方法
用管理员模式打开CMD，再执行mvn clean compile。

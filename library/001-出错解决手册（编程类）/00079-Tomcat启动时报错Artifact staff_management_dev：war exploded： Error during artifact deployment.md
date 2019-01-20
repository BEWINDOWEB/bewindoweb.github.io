# Tomcat启动时报错Artifact staff_management_dev:war exploded: Error during artifact deployment
`【系统环境】windows 10`  
`【操作内容】SpringMVC4 /  Hibernate5.2 / Redis 3.2 / IntelliJ IDEA 2018.1 / Java1.8`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
Tomcat启动时报错：
```
Artifact staff_management_dev:war exploded: Error during artifact deployment. See server log for details.
```
## <i class="fa fa-bullseye"></i> 根本原因
查看C:\Users\admin\.IntelliJIdea2018.1\system\tomcat\Unnamed_staff_management_dev\logs\catalina.2018-10-18.log后发现，
我之前通过IDEA的重构工具错误地把两个类命名为一样的名字，造成bean注入的时候发现定义重复了。
## <i class="fa fa-check-circle"></i> 解决方法
重新命名不同的名字。

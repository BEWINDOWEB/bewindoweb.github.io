# NoSuchMethodError: javax.persistence.Table.indexes()[Ljavax/persistence/Index
`【系统环境】windows 10`  
`【操作内容】SpringMVC4 / Hibernate 5 / IntelliJ IDEA 2018.1 / Java1.8`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
用Junit单元测试没报错，用Tomcat网络环境测试service功能时报错：
```
org.apache.catalina.core.StandardWrapperValve.invoke Servlet.service() for servlet [springDispatcherServlet] in context with path [/staff_management_dev] threw exception [Handler processing failed; nested exception is java.lang.ExceptionInInitializerError] with root cause
java.lang.NoSuchMethodError: javax.persistence.Table.indexes()[Ljavax/persistence/Index;
```
## <i class="fa fa-bullseye"></i> 根本原因
hibernate-jpa-2.0版本没有Table.indexes方法，而当Pom.xml修改成2.1了之后，同时引入了两个jar包，在Tomcat的时候2.0的jar包被优先选择，导致仍然找不到。  
更深层的原因是spring-jpa产生了冲突，需要提高spring-jpa的版本。
## <i class="fa fa-check-circle"></i> 解决方法
打开左侧的LIB，选中2.0：
![](assets/001/20181214-0c1757a6.png)  
右键Open Library Settings：
![](assets/001/20181214-24ef8ab3.png)  
删除掉2.0，重启Tomcat。

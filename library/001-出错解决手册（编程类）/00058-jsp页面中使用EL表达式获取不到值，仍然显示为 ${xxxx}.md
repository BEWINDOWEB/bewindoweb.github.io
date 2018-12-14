# jsp页面中使用EL表达式获取不到值，仍然显示为 ${xxxx}
`【系统环境】windows 10`  
`【操作内容】SpringMVC4 / Hibernate 5 / IntelliJ IDEA 2018.1 / Java1.8`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
测试jsp的显示时：
```
hibernate的确获取到了数据，但是jsp页面中使用EL表达式获取不到值，仍然显示为 ${xxxx}
```
## <i class="fa fa-bullseye"></i> 根本原因
当web.xml写：
```
<!DOCTYPE web-app PUBLIC
        "-//Sun Microsystems, Inc.//DTD Web Application 2.3//EN"
        "http://java.sun.com/dtd/web-app_2_3.dtd" >
<web-app>
   ...........
</web-app>
```
的时候，说明使用的是servlet 2.3 / jsp1.2 ，不支持EL表达式。
## <i class="fa fa-check-circle"></i> 解决方法
把上面的代码修改为:
```
<!-- 删掉前面的 -->
<web-app version="2.5"
    xmlns="http://java.sun.com/xml/ns/javaee"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://java.sun.com/xml/ns/javaee
    http://java.sun.com/xml/ns/javaee/web-app_2_5.xsd">
   ...........
</web-app>
```
这样就能使用servlet2.4 / jsp 2.0

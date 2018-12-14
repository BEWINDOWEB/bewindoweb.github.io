# 通配符的匹配很全面, 但无法找到元素 'tx:annotation-driven' 的声明
`【系统环境】windows 10`  
`【操作内容】SpringMVC4 / IntelliJ IDEA 2018.1 / Java1.8`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
开启注解事务管理器时：
```
<!-- 开启注解事务管理器 -->
<tx:annotation-driven transaction-manager="txManager"/>
```
报错：   
通配符的匹配很全面, 但无法找到元素 'tx:annotation-driven' 的声明。
## <i class="fa fa-bullseye"></i> 根本原因
xsi:schemaLocation声明的xsd文件路径有错。
## <i class="fa fa-check-circle"></i> 解决方法
打开左侧的External Libraries，找到tx的包，并依此找到jar  →  META-INF →  spring.schemas：
![](assets/001/20181214-94ef7f8c.png)  
发现路径是：
```
http\://www.springframework.org/schema/tx/spring-tx-4.3.xsd=org/springframework/transaction/config/spring-tx-4.3.xsd
```
所以把原来的改为：
```
<!-- http://www.springframework.org/schema/spring-tx-4.3.xsd -->
http://www.springframework.org/schema/tx/spring-tx-4.3.xsd
```

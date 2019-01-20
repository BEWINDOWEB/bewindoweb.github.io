# Spring-security 报错：NoClassDefFoundError
`【系统环境】windows 10`  
`【操作内容】SpringMVC4 /  Hibernate5.2 / Redis 3.2 / IntelliJ IDEA 2018.1 / Java1.8`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
Spring security在项目启动时报错：
```
03-Sep-2018 20:01:48.789 严重 [RMI TCP Connection(3)-127.0.0.1] org.apache.catalina.core.StandardContext.listenerStart Exception sending context initialized event to listener instance of class [org.springframework.web.context.ContextLoaderListener]
java.lang.NoClassDefFoundError: org/springframework/security/web/access/WebInvocationPrivilegeEvaluator
at java.lang.Class.getDeclaredMethods0(Native Method)
```
按照网上的方法改为了spring-security-core 4.2.0，然而依然报错：
```
java.lang.NoClassDefFoundError: org/springframework/security/authentication/AuthenticationManager
at java.lang.Class.getDeclaredMethods0(Native Method)
```
## <i class="fa fa-bullseye"></i> 根本原因
版本问题，导致找不到方法。
## <i class="fa fa-check-circle"></i> 解决方法
修改maven配置文件pom.xml，使用4.2.3版本：
```
<dependency>
    <groupId>org.springframework.security</groupId>
    <artifactId>spring-security-core</artifactId>
    <version>4.2.3.RELEASE</version>
</dependency>
<dependency>
    <groupId>org.springframework.security</groupId>
    <artifactId>spring-security-crypto</artifactId>
    <version>4.2.3.RELEASE</version>
</dependency>
<dependency>
    <groupId>org.springframework.security</groupId>
    <artifactId>spring-security-ldap</artifactId>
    <version>4.2.3.RELEASE</version>
</dependency>
<dependency>
    <groupId>org.springframework.security</groupId>
    <artifactId>spring-security-config</artifactId>
    <version>4.2.3.RELEASE</version>
</dependency>
<dependency>
    <groupId>org.springframework.security</groupId>
    <artifactId>spring-security-web</artifactId>
    <version>4.2.3.RELEASE</version>
</dependency>
<dependency>
    <groupId>org.springframework.security</groupId>
    <artifactId>spring-security-cas</artifactId>
    <version>4.2.3.RELEASE</version>
</dependency>
```

# 提交ajax的post请求提示：HTTP 415
`【系统环境】windows 10`  
`【操作内容】SpringMVC4 /  IntelliJ IDEA 2018.1 / Java1.8`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
提交ajax的post请求提示：HTTP 415
## <i class="fa fa-bullseye"></i> 根本原因
没有添加json处理组件
## <i class="fa fa-check-circle"></i> 解决方法
用Maven添加jackson:
```
<!-- json -->
<dependency>
    <groupId>org.codehaus.jackson</groupId>
    <artifactId>jackson-mapper-asl</artifactId>
    <version>1.9.8</version>
</dependency>
<dependency>
    <groupId>com.fasterxml.jackson.core</groupId>
    <artifactId>jackson-annotations</artifactId>
    <version>2.9.3</version>
</dependency>
<dependency>
    <groupId>com.fasterxml.jackson.core</groupId>
    <artifactId>jackson-databind</artifactId>
    <version>2.9.3</version>
</dependency>
<dependency>
    <groupId>com.fasterxml.jackson.core</groupId>
    <artifactId>jackson-core</artifactId>
    <version>2.9.3</version>
</dependency>
```

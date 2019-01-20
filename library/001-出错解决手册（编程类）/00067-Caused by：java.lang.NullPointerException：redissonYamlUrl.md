# Caused by: java.lang.NullPointerException: redissonYamlUrl
`【系统环境】windows 10`  
`【操作内容】SpringMVC4 /  Hibernate5 / Redis 3.2 / IntelliJ IDEA 2018.1 / Java1.8`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
配置好redis运行后提示：
```
Caused by: java.lang.NullPointerException: redissonYamlUrl
```
## <i class="fa fa-bullseye"></i> 根本原因
没有找到redisson.yaml文件，文件路径有问题
## <i class="fa fa-check-circle"></i> 解决方法
把redisson.yaml文件放到src/resources目录下，用classpath:redisson.yaml作为路径。

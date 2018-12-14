# 通配符的匹配很全面，但无法找到元素contextannotation-config
`【系统环境】windows 10`  
`【操作内容】springMVC 4/ IntelliJ IDEA 2018.1 / Java1.8`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
测试springMVC框架配置文件时报错：
```
通配符的匹配很全面，但无法找到元素“context: annotation-config”的声明springds.xml<context: annotation-config/>
```
## <i class="fa fa-bullseye"></i> 根本原因
springds.xml中，xsi:schemaLocation的设置有问题
## <i class="fa fa-check-circle"></i> 解决方法
把springds.xml的xsi:schemaLocation的：
```
http://www.springframework.org/schema/beans/spring-context.xsd
```
改为：
```
http://www.springframework.org/schema/context/spring-context.xsd
```

# Hibernate查询报错：Table 'smdtest.smd_user' doesn't exist
`【系统环境】windows 10`  
`【操作内容】SpringMVC4 /  Hibernate5.2 / Redis 3.2 / IntelliJ IDEA 2018.1 / Java1.8`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
在执行查询语句的时候，提示类没有被映射：
```
javax.persistence.PersistenceException: org.hibernate.exception.SQLGrammarException: could not extract ResultSet
Table 'smdtest.smd_user' doesn't exist
```
## <i class="fa fa-bullseye"></i> 根本原因
我将之前的数据库从smdtest更换为了smd，然而配置文件却没有更改。
## <i class="fa fa-check-circle"></i> 解决方法
更改applicationContext.xml中的数据库路径smdtest为smd：
```
<!-- 数据源配置，充当hibernate.cfg.xml的基本连接部分-->
<bean id="smdDataSource" class="org.springframework.jdbc.datasource.DriverManagerDataSource">
    <property name="url" value="jdbc:mysql://localhost:3306/smd" />
</bean>
```

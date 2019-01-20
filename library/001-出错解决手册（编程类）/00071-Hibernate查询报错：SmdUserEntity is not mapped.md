# Hibernate查询报错：SmdUserEntity is not mapped
`【系统环境】debian 8.2`  
`【操作内容】shell(dash)`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
在执行查询语句的时候，提示类没有被映射：
```
Caused by: org.hibernate.hql.internal.ast.QuerySyntaxException: SmdUserEntity is not mapped
java.lang.IllegalArgumentException: org.hibernate.hql.internal.ast.QuerySyntaxException: SmdUserEntity is not mapped [select id from SmdUserEntity where workEmail = ? ]
```
## <i class="fa fa-bullseye"></i> 根本原因
在更新数据库之后，没有去更新applicationContext.xml文件中的配置项。
## <i class="fa fa-check-circle"></i> 解决方法
增加applicationContext.xml中的：
```
<property name="annotatedClasses">
            <list>
                <value>com.smd.model.EmployeeEntity</value>
            </list>
</property>
```

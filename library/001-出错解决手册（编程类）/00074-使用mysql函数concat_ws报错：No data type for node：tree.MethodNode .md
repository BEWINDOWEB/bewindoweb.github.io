# 使用mysql函数concat_ws报错：No data type for node:tree.MethodNode
`【系统环境】windows 10`  
`【操作内容】SpringMVC4 /  Hibernate5.2 / Redis 3.2 / IntelliJ IDEA 2018.1 / Java1.8`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
在使用mysql函数concat_ws时候，hql报错：
```
Caused by: org.hibernate.QueryException: No data type for node: org.hibernate.hql.internal.ast.tree.MethodNode
```
## <i class="fa fa-bullseye"></i> 根本原因
hql只支持基本的mysql函数。
## <i class="fa fa-check-circle"></i> 解决方法
自定义CustomMySQLDialect.java类，注册需要的函数，语法如下：
```
public class CustomMySQLDialect extends MySQLDialect {

    public CustomMySQLDialect(){
        super();
        registerFunction("pyOrder",new SQLFunctionTemplate(StandardBasicTypes.STRING,"convert(?1 using gbk)"));
        //collate gbk_chinese_ci
        //3.5+后取消掉了 Hibernate.STRING  可以使用 StringType.INSTANCE
        //它没有注册concat_ws函数
        registerFunction("concat_ws",new StandardSQLFunction("concat_ws", StandardBasicTypes.STRING));
        registerFunction("gc",new SQLFunctionTemplate(StandardBasicTypes.STRING,"group_concat(distinct ?1 separator ?2)"));
        registerFunction("coalesce",new StandardSQLFunction("coalesce", StandardBasicTypes.STRING));
        registerFunction("countMuti",new SQLFunctionTemplate(StandardBasicTypes.STRING,"count(distinct ?1, ?2)"));
        registerFunction("countSingle",new SQLFunctionTemplate(StandardBasicTypes.STRING,"count(distinct ?1)"));
    }
}
```
然后在applicationContext.xml中去配置它：
```
<bean id="sessionFactory" class="org.springframework.orm.hibernate5.LocalSessionFactoryBean">
    <property name="dataSource" ref="smdDataSource"/>
    <property name="hibernateProperties">
        <props>
            <prop key = "hibernate.dialect">com.smd.utils.CustomMySQLDialect</prop> <!-- org.hibernate.dialect.MySQLDialect -->
            ……
```

# Hibernate插入报错： [Batch update returned unexpected row count from update [0]; actual row count: 0; expected: 1]
`【系统环境】windows 10`  
`【操作内容】SpringMVC4 /  Hibernate5.2 / Redis 3.2 / IntelliJ IDEA 2018.1 / Java1.8`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
在执行插入操作的时候报错：
```
 [Batch update returned unexpected row count from update [0]; actual row count: 0; expected: 1]
```
## <i class="fa fa-bullseye"></i> 根本原因
默认的策略ID必须是绑定的，然而需求是id为null根据数据库来自增，所以需要更改ID策略。
## <i class="fa fa-check-circle"></i> 解决方法
在model类的getId方法上增加注解@GeneratedValue（注意必须重启Tomcat才会生效）：
```
@Id
@GeneratedValue(strategy = GenerationType.IDENTITY)
@Column(name = "id", nullable = false)
public Integer getId() {
    return id;
}
```

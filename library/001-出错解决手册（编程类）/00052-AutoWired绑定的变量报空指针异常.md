# AutoWired绑定的变量报空指针异常
`【系统环境】windows 10`  
`【操作内容】SpringMVC`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
当时使用注解`@Autowired`自动注入变量的时候，报了空指针异常。
## <i class="fa fa-bullseye"></i> 根本原因
某一个部分使用了`new`而不是全都使用`@Autowired`导致注入失败。
## <i class="fa fa-check-circle"></i> 解决方法
修改所有的controller、service、dao的注入都为`@Autowired`，不要使用new！不要使用new！不要使用new！  
同时检查是否有`@Service`、`@Component`注解在类的前面。

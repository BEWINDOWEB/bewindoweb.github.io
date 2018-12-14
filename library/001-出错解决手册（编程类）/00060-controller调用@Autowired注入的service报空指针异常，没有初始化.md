# controller调用@Autowired注入的service报空指针异常，没有初始化
`【系统环境】windows 10`  
`【操作内容】SpringMVC4 / Hibernate 5 / IntelliJ IDEA 2018.1 / Java1.8`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
service层使用@Autowired注入时：
```
@Autowired
private EmployeeEntityDao employeeEntityDao;
```
controller调用service报空指针异常，没有初始化。
## <i class="fa fa-bullseye"></i> 根本原因
要注入都得注入，调用service的也要@Autowired。
## <i class="fa fa-check-circle"></i> 解决方法
修改service：
```
@Autowired
EmployeeEntityService service;// = new EmployeeEntityServiceImpl();
```

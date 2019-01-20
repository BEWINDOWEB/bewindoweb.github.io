# Could not read document: Unrecognized token 'id': was expecting ('true', 'false' or 'null')
`【系统环境】windows 10`  
`【操作内容】SpringMVC4 /  IntelliJ IDEA 2018.1 / Java1.8`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
提交post表单提示：
```
org.springframework.http.converter.HttpMessageNotReadableException: Could not read document: Unrecognized token 'id': was expecting ('true', 'false' or 'null')
```
## <i class="fa fa-bullseye"></i> 根本原因
不能处理json数据，要进行序列化
## <i class="fa fa-check-circle"></i> 解决方法
前端进行序列化。
```
var dataJson = {"id":id, "workid":workid, "sex":sex, "hobby":hobby};
………………
data:JSON.stringify(dataJson),
………………
```

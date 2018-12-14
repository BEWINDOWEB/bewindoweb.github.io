# 首页不访问controller，直接访问的没有数据的index.jsp
`【系统环境】windows 10`  
`【操作内容】SpringMVC4 / IntelliJ IDEA 2018.1 / Java1.8`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
其他的controller能正常访问，首页却似乎没有访问controller，直接访问的没有数据的index.jsp。
## <i class="fa fa-bullseye"></i> 根本原因
没有添加首页配置。
## <i class="fa fa-check-circle"></i> 解决方法
web.xml中添加：
```
<welcome-file-list>
    <welcome-file>index</welcome-file>
</welcome-file-list>
```

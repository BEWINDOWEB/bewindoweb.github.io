# 转换到model时报错：java.lang.Integer cannot be cast to java.lang.Byte
`【系统环境】windows 10`  
`【操作内容】SpringMVC4 /  Hibernate5.2 / Redis 3.2 / IntelliJ IDEA 2018.1 / Java1.8`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
转换为model时报错：
```
java.lang.ClassCastException: java.lang.Integer cannot be cast to java.lang.Byte
```
## <i class="fa fa-bullseye"></i> 根本原因
似乎必须使用规定的包装类，类之间不能自动转换。
## <i class="fa fa-check-circle"></i> 解决方法
手动编写转换方法：
```
public static Long toLong(Object num){
    return num == null ? null : Long.valueOf(num.toString());
}
```

# 编写basedao的时候报错：java.lang.Class cannot be cast to java.lang.reflect.ParameterizedType
`【系统环境 windows 10`  
`【操作内容】 SpringMVC4 /  Hibernate5.2 / Redis 3.2 / IntelliJ IDEA 2018.1 / Java1.8`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
编写dao的基类实现BasedaoImpl.java的构造函数：
```
private Class<T> entityClazz;
private String entityName;
BaseDaoImpl(){
ParameterizedType pt = (ParameterizedType) this.getClass().getGenericSuperclass();// upserclass是BaseDaoImpl<T>
entityClazz = (Class) pt.getActualTypeArguments()[0];// 这样就把T取出来了
entityName = entityClazz.getSimpleName();//就可以使用了
}
```
报错：
```
java.lang.Class cannot be cast to java.lang.reflect.ParameterizedType
```
## <i class="fa fa-bullseye"></i> 根本原因
未知。debug发现getGenericSuperclass总是直接取到Object，而不是具体的T类。
## <i class="fa fa-check-circle"></i> 解决方法
将BaseDaoImpl改为抽象类：
```
public abstract class BaseDaoImpl<T> implements IBaseDao<T>
```
然后执行就会取到具体的类了，网上说是什么这样就不会引起歧义。

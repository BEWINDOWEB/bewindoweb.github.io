# redis作为hibernate二级缓存出错提示：SharedSessionContractImplementor;Ljava/lang/Object;Ljava/lang/Object;)V
`【系统环境】windows 10`  
`【操作内容】SpringMVC4 /  Hibernate5.2 / Redis 3.2 / IntelliJ IDEA 2018.1 / Java1.8`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
redis作为hibernate二级缓存出错提示：
```
java.lang.AbstractMethodError: org.hibernate.cache.redis.hibernate5.regions.RedisTimestampsRegion.put(Lorg/hibernate/engine/spi/SharedSessionContractImplementor;Ljava/lang/Object;Ljava/lang/Object;)V
at org.hibernate.cache.spi.UpdateTimestampsCache.preInvalidate(UpdateTimestampsCache.java:77)
```
## <i class="fa fa-bullseye"></i> 根本原因
工厂方法变化了，Hibernate5和Hibernate5.2的方法是不一样的。
## <i class="fa fa-check-circle"></i> 解决方法
修改Spring配置文件applicationContext.xml：
```
<!-- <prop key = "hibernate.cache.region.factory_class">org.hibernate.cache.redis.hibernate5.SingletonRedisRegionFactory</prop> -->
<prop key = "hibernate.cache.region.factory_class">org.hibernate.cache.redis.hibernate52.SingletonRedisRegionFactory</prop>
```

# hibernate同时使用问号参和名字数组参插入的数据顺序出现混乱
`【系统环境】windows 10`  
`【操作内容】SpringMVC4 /  Hibernate5.2 / Redis 3.2 / IntelliJ IDEA 2018.1 / Java1.8`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
本来是这样一条语句：
```
id in (:ids) limit ?,?
```
其中，ids = [1,3,4,5,6,7,8,9]，问号为 0,10  
在执行之后结果不对，查看mysql执行日志发现变为了：  
```
id in (0, 10, 1, 3, 4, 5, 6, 7) limit 8,9
```
仔细查看debug日志，发现转换过程是：
```
→ in (ids_0, ids_1, ids_2, ids_3, ids_4, ids_5, ids_6, ids_7) limit ?,?
→ in (?, ?, ?, ?, ?, ?, ?, ?) limit ?,?
→ in (0, 10, 1, 3, 4, 5, 6, 7) limit 8,9
```
最开始还有名字，后来全部变为没名字了，然后再换参数，就出现错误。
## <i class="fa fa-bullseye"></i> 根本原因
hql转sql过程中出现顺序异常。
## <i class="fa fa-check-circle"></i> 解决方法
暂时的解决方法是，一旦有数组的名字参，全都使用名字参：
```
id in (:ids) limit :pageNo,:pageSize
```

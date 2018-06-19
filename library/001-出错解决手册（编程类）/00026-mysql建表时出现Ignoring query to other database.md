# mysql建表时出现Ignoring query to other database
`【系统环境】debian`  
`【操作内容】mysql`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
登录Mysql后不管什么命令都会出现：
```
mysql> show tables;
Ignoring query to other database
```
## <i class="fa fa-bullseye"></i> 根本原因
登录的时候没有写-u：
```
mysql -root -p
```
## <i class="fa fa-check-circle"></i> 解决方法
退出重新登录mysql，正确写即可：
```
mysql -uroot -p
```

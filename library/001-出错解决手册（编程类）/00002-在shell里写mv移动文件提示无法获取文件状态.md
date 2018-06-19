# 在shell里写mv移动文件提示无法获取文件状态
`【系统环境】debian 8.2`  
`【操作内容】shell(dash)`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
在写shell脚本时提示：
```bash
mv: 无法获取"/home/mysqlbacky/bakmysql/*.sql" 的文件状态(stat): 没有那个文件或目录
```
移动文件的操作也没有成功。
## <i class="fa fa-bullseye"></i> 根本原因
并不是mv不能移动带通配符的文件，而是mv的文件名不正确，shell脚本把通配符当字符串处理了。
## <i class="fa fa-check-circle"></i> 解决方法
将引号去掉。
比如：
```bash
mv "${datapath}/*.sql"  "${datapath}old/"
```
应该改为：
```bash
mv ${datapath}/*.sql  ${datapath}old/
```
## <i class="fa fa-star"></i> 更多技巧
另外，为了当文件找不到（文件还没生成或者已经被移走了）mv会提示同样的错误，说无法获取文件状态。这是正常的情况，如果不想被提示，可以将错误信息输出到黑洞里去：
```bash
mv ${datapath}/*.sql  ${datapath}old/ 2>/dev/null
```

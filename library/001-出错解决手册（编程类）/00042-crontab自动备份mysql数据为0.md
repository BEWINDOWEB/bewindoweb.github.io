# crontab自动备份mysql数据为0
`【系统环境】debian 8.2`  
`【操作内容】mysql 5.6 / crontab`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
使用脚本
```bash
mdpath=$(which msyqldump) 	#mysqldump path
${mdpath} --opt -u${user} -p${password} -h${hostname} ${databasename} --skip-lock-tables > $File
```
备份mysql时，发现直接运行是可以的，但是用crontab不行，输出的文件内容为空，0字节。
## <i class="fa fa-bullseye"></i> 根本原因
直接运行可以，crontab不行，90%都是因为命令的路径有问题。
我把`which mysqldump`的结果输出，直接输出是对的，而crontab运行输出是空字符串。
## <i class="fa fa-check-circle"></i> 解决方法
暂时只有妥协，设置为字符串：
```bash
mdpath="/opt/mysql/server-5.6/bin/mysqldump" 	#mysqldump path
```

# windows安装mysql5.6版本时，服务mysql56无法启动的问题
`【系统环境】windows 8`  
`【操作内容】安装mysql5.6`  
`【解决方案验证次数】2次`  
## <i class="fa fa-question-circle"></i> 出现问题
windows 8下安装mysql 5.6的最后阶段，安装程序不能提起mysql56的服务，因此重复进行提起、等待操作，安装不能往下继续进行。
## <i class="fa fa-bullseye"></i> 根本原因
mysql读取windows下my.ini配置文件出错，Linux下的换行和windows下不！一！样！读取的时候就出错了，因此无法提起mysql56服务。
## <i class="fa fa-check-circle"></i> 解决方法
【第1步】把`C:\ProgramData\MySQL\MySQL Server 5.6`下的`my.ini`备份成`my.ini.back`
![](assets/001/20180619-ffa93ce0.png)  
【第2步】记事本打开`my.ini`，另存为，果然发现编码格式是`UTF-8`
![](assets/001/20180619-98d36651.png)  
【第3步】把格式改成`ANSI`，存储回`C:\ProgramData\MySQL\MySQL Server 5.6`下
![](assets/001/20180619-612e8052.png)  
【第4步】重新初始化一次（我也不知道这一步是否起了作用）
```sh
C:\Program Files\MySQL\MySQL Server 5.6\bin>mysqld --initialized
2017-04-04 21:05:46 0 [warning] TIMESTAMP with implicit DEFAULT value is deprecated. Please use --explicit_defaults_....
```
【第5步】启动服务，发现好了！
```sh
C:\Program Files\MySQL\MySQL Server 5.6\bin>net start mysql56
MySQL56 服务正在启动...
MySQL56 服务已经启动成功。
```

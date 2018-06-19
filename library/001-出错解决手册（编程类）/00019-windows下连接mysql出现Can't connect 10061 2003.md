# windows下连接mysql出现Can't connect 10061 2003
`【系统环境】windows 8`  
`【操作内容】mysql 5.6 bench`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
打开mysql 5.6的bench管理界面，连接数据库，提示错误日志：
```
2018-02-23 14:49:23 - Starting server...
2018-02-23 14:49:28 - Server start done.
2018-02-23 14:49:29 - Checking server status...
2018-02-23 14:49:29 - Trying to connect to MySQL...
2018-02-23 14:49:29 - Can't connect to MySQL server on '127.0.0.1' (10061) (2003)
2018-02-23 14:49:29 - Assuming server is not running
2018-02-23 14:49:29 - Checking server status...
2018-02-23 14:49:29 - Trying to connect to MySQL...
2018-02-23 14:49:29 - Can't connect to MySQL server on '127.0.0.1' (10061) (2003)
2018-02-23 14:49:29 - Assuming server is not running
2018-02-23 14:49:45 - Checking server status...
2018-02-23 14:49:45 - Trying to connect to MySQL...
2018-02-23 14:49:45 - Can't connect to MySQL server on '127.0.0.1' (10061) (2003)
2018-02-23 14:49:45 - Assuming server is not running
```
无法连接数据库
## <i class="fa fa-bullseye"></i> 根本原因
mysql的服务没有启动
## <i class="fa fa-check-circle"></i> 解决方法
【第一步】win+R 打开控制台  
【第二步】打开服务器管理
```
services.msc
```
【第三步】找到MYSQL服务，一般为MYSQL56，如果没有看到mysql服务，请参考这篇文章[《安装了mysql但是没有mysql56的服务》](?file=001-出错解决手册（编程类）/00018-安装了mysql但是没有mysql56的服务)  
【第四步】右键启动MYSQL服务
![](assets/001/20180619-c4438051.png)  

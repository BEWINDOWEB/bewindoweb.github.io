# 安装了mysql但是没有mysql56的服务
`【系统环境】windows 8`  
`【操作内容】mysql 5.6的服务`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
明明安装了mysql，却没有mysql56服务
## <i class="fa fa-bullseye"></i> 根本原因
最近安装了phpadmin或者LAMP或者之类的，把mysql服务删除了。
## <i class="fa fa-check-circle"></i> 解决方法
【第一步】以管理员模式运行CMD命令shell（否则会没有权限）  
【第二步】进入mysql安装的bin目录
```
E:
cd E:/mysql5.6/bin
```
【第三步】安装mysql服务，我这里是mysql5.6版本
```
mysqld.exe -install
```
【第四步】win+R，输入services.msc，刷新一下就能看到mysql服务了。

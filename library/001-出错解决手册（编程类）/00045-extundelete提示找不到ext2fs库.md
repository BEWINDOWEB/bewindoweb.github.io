# extundelete配置时提示找不到ext2fs库
`【系统环境】ubuntu 14.04 / vmware 14 pro`  
`【操作内容】extundelete v0.2.4`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
使用linux下的误删文件恢复工具extundelete，在安装前的`./configure`阶段提示错误：
```
Configuring extundelete 0.2.4
configure: error: Can't find ext2fs library
```
## <i class="fa fa-bullseye"></i> 根本原因
没有安装ext2fs库
## <i class="fa fa-check-circle"></i> 解决方法
```
sudo apt-get install e2fslibs-dev e2fslibs-dev
```

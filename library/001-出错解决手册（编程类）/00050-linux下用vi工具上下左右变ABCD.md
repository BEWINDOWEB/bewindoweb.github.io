# linux下用vi工具上下左右变ABCD
`【系统环境】debian 8.2`  
`【操作内容】shell(dash)`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
新安装debian 8.2，按`i`进入编辑模式后，按`上下左右`键出现的却是`^A^B^C^D`。
## <i class="fa fa-bullseye"></i> 根本原因
vi的默认风格就是这样的，要想支持上下左右，需要安装vim
## <i class="fa fa-check-circle"></i> 解决方法
安装vim:
```bash
sudo apt-get install vim
```
然后再使用vi或者vim命令就不会有问题啦。

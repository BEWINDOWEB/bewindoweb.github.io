# Ubuntu不能自动适应Vmware窗口大小
`【系统环境】windows 10`  
`【操作内容】vmware workstation 14`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
ubuntu不能自动适应vmware窗口大小。

## <i class="fa fa-bullseye"></i> 根本原因
没有安装vmtool

## <i class="fa fa-check-circle"></i> 解决方法
```
sudo apt-get install open-vm-tools
sudo apt-get install open-vm*
reboot
```
`查看` → `自动调整大小` → `自动适应客户机`

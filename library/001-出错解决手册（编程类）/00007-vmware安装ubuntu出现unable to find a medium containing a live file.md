# vmware安装ubuntu出现unable to find a medium containing a live file system
`【系统环境】windows 8`  
`【操作内容】vmware 10 / ubuntu 16.04 LTS`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
安装ubuntu的时候还没有开始就说遇到了错误，需要重启。  
重启后ubuntu提示unable to find a medium containing a live file system：
![](assets/001/20180619-8012618c.png)  
## <i class="fa fa-bullseye"></i> 根本原因
硬盘分配的内存不够，本来查了下官网准备重新下载，然而发现了这个：
![](assets/001/20180619-ba013fac.png)  
所以是vmware默认的1GB内存、20GB硬盘不够用才出现的问题。
## <i class="fa fa-check-circle"></i> 解决方法
【第1步】删除之前有问题的ubuntu  
【第2步】重新安装ubuntu，内存选择4GB，硬盘选择50GB。

# vmware：无法打开虚拟机，似乎正在被使用
`【系统环境】windows 8`  
`【操作内容】vmware 10.0.2 build-1744117`  
`【解决方案验证次数】2次`  
## <i class="fa fa-question-circle"></i> 出现问题
windows 8下打开vmware虚拟机时出现`无法打开虚拟机：x:xxx.vmx。该虚拟机似乎正在被使用`。
## <i class="fa fa-bullseye"></i> 根本原因
虚拟机运行过程中曾经被强行中止（比如掉电、任务管理器结束任务），造成部分文件被破坏。
## <i class="fa fa-check-circle"></i> 解决方法
【第1步】找到此虚拟机的安装文件夹（比如：`E:\VMware虚拟机\共享虚拟机\windows XP`）  
【第2步】将名字以`.lck`结尾的文件夹全部重命名，重命名的名字随意（比如`Windows XP Professional.vmdk.lck`变为`windowsfnal.vmdk.lck`）  
【第3步】F5刷新，再次打开虚拟机即可使用，并且虚拟机内文件不会丢失！

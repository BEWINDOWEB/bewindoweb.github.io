# 搬瓦工重置密码出错banwagonhost:992800002 VPS is currently running
`【系统环境】centos 6 bbr`  
`【操作内容】搬瓦工`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
想用ssh连接搬瓦工的VPS，通过kiwiVM面板重置搬瓦工root密码时，尽管已经关机了，仍然提示错误：
```
Failed to reset root password
Additional information: 992800002 VPS is currently running.
Please stop the VPS before attempting to modify root password.
```
## <i class="fa fa-bullseye"></i> 根本原因
未知
## <i class="fa fa-check-circle"></i> 解决方法
没有好的解决办法，有一个替代的重置密码方法：  
【第一步】点击左侧菜单的`shell-basic`  
【第二步】输入命令：  
```bash
echo "root:yourpassword" | chpasswd
```
完成后，`yourpassword`就是你的新密码了。注意连接的时候端口可能不是通常的22，你可以从kiwiVM面板首页看到VPS开放的端口。

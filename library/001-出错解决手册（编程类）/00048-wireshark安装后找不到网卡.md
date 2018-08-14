# wireshark安装后找不到网卡
`【系统环境】windows 8`  
`【操作内容】wireshark 2.6.2`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
wireshark安装完成后找不到网卡。
## <i class="fa fa-bullseye"></i> 根本原因
winPcap没有安装好。
**在安装过程中，wireshark提示winPcap已经被安装过了，是否强制安装，我就选择了取消，但其实应该重新强制再装一遍。**
## <i class="fa fa-check-circle"></i> 解决方法
【第一步】卸载wireshark  
【第二步】重装wireshark，在安装过程中如果提示winPcap被安装过，仍然点`确定`强制重新安装winPcap。

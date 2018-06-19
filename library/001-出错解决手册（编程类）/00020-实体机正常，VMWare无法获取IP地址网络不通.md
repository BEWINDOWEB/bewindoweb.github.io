# 实体机正常，VMWare无法获取IP地址网络不通
`【系统环境】windows 8`  
`【操作内容】vmware / windows xp sp3`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
实体机网络通畅，VMWare装的windows XP SP3出现：无法获取IP地址。
## <i class="fa fa-bullseye"></i> 根本原因
前几天用360加速球，把VMWare的DHCP服务给清理掉了
## <i class="fa fa-check-circle"></i> 解决方法
【第一步】打开服务
```
Win+R，services.msc
```
【第二步】把VMWare的所有服务开启
![](assets/001/20180619-c0495950.png)  
## <i class="fa fa-book"></i> 参考资料
[《VMware Workstation虚拟机不能联网的解决办法》](https://jingyan.baidu.com/article/066074d668155bc3c21cb0ca.html)

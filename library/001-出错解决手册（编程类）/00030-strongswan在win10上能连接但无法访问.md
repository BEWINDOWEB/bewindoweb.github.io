# strongswan在win10上能连接但无法访问
`【系统环境】windows 10`  
`【操作内容】配置strongswan连接`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
搭建好的strongswan在win10上能够连接，但是无法访问一些网页
## <i class="fa fa-bullseye"></i> 根本原因
win10 ikev2有bug，默认不勾选“远程网络上使用默认网关”，需要自己手动添加路由表。
## <i class="fa fa-check-circle"></i> 解决方法
【第1步】在`控制面板 > 网络和Internet > 网络链接`中，找到相应的连接，打开其`属性`页
![](assets/001/20180619-4bf8135a.png)  
【第2步】在`网络`标签页中的`ipv4`的`属性`中，点`高级`，打开`高级TCP/IP设置`页面
![](assets/001/20180619-bc3aee21.png)  
【第3步】在`IP设置`标签页中，勾选在`远程网络上使用默认网关`  
![](assets/001/20180619-1c6d4f44.png)  

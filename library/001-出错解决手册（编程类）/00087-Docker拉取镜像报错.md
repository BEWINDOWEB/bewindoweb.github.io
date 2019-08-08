# Docker拉取镜像报错
`【系统环境】windows 10`  
`【操作内容】ubuntu16 docker-ce 18`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
docker 拉取镜像报错：
```
ERROR: Get https://registry-1.docker.io/v2/: dial tcp: lookup registry-1.docker.io on [::1]:53: read udp [::1]:47313->[::1]:53: read: connection refused
```

## <i class="fa fa-bullseye"></i> 根本原因
没有找到IP，连接被拒绝

## <i class="fa fa-check-circle"></i> 解决方法
```
# 修改dns
vi /etc/network/interfaces
末尾添加：dns-nameservers 8.8.8.8

# 重启网络服务
systemctl restart networking.service
```

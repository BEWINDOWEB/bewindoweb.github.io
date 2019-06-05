# docker-cli命令


## 控制相关
| 序号 | 操作 | 命令 | 备注 |
| ---- | ---- | ---- | ---- |
| 1 | 停用全部运行中的容器 | docker stop $(docker ps -q) | - |
| 2 | 删除全部容器 | docker rm $(docker ps -aq) | - |
| 3 | 启动服务 | systemctl start docker | - |
| 4 | 启动服务 | service docker start | - |
| 5 | 重启守护进程 | systemctl daemon-reload | - |
| 6 | 查看docker容器 | docker ps | - |
| 7 | 查看所有docker容器 | docker ps -a | - |
| 8 | 停止所有container | docker stop $(docker ps -a -q) | - |
| 9 | 删除所有container | docker rm $(docker ps -a -q) | - |
| 10 | 清理停掉的Container资源 | docker system prune | - |
| 11 | 强力清理停掉的Container资源 | docker system prune -a | - |
| 12 | 查看docker镜像 | docker images | - |
| 13 | 删除docker镜像 | docker rmi [镜像ID] | - |
| 14 | 删除tag为none的镜像 | docker rmi $(docker images &#124; grep "^<none>" &#124; awk "{print $3}") | - |
| 15 | 导出镜像到文件 | docker save [镜像ID] > [文件路径]  | 例如：docker save c38 > /root/image.tar  |
| 16 | 导入文件镜像 | docker load < [文件路径]  | 例如 docker load < /root/image.tar  |
| 17 | 导入文件镜像 | docker load -i [文件路径]  | 例如 docker load -i /root/image.tar  |
| 18 | 给导入的镜像增加repository和tag | docker tag [镜像id] [名字]:[版本]  | 例如 docker tag b03 redis:3.2 |
| 19 | 进入容器内部 | docker exec -it [容器ID] /bin/bash  | - |

## 运维相关
| 序号 | 操作 | 命令 | 备注 |
| ---- | ---- | ---- | ---- |
| 1 | 查看容器运行日志 | docker logs [容器ID] | - |
| 2 | 监控所有容器占用系统资源 | docker stats | - |
| 3 | 查看docker占用磁盘资源详情 | docker system df -v | - |
| 4 | 查看容器日志占用 | du -sh /var/lib/docker/containers/* | - |
| 5 | 查看容器日志占用 | ls -lh $(find /var/lib/docker/containers/ -name *-json.log) | - |
| 6 | 清理容器日志 | truncate -s 0 /var/lib/docker/containers/[容器ID]/*-json.log | - |
| 7 | 清除无用数据卷 | docker volume rm $(docker volume ls -qf dangling=true) | - |

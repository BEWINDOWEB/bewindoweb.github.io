# Crontab定时任务设置

## Debian
> 测试通过：
> * debian 8.9

#### 修改系统的Crontab
```bash
vi /etc/crontab
```
#### Crontab重启  
```bash
/etc/init.d/cron restart
```
#### 打开Crontab日志功能
```bash
# 用vi打开日志配置文件
vi /etc/rsyslog.conf
# 将下面语句最前面的注释符号去掉
cron.*       /var/log/cron.log
# 重启日志服务
/etc/init.d/rsyslog restart
# 提示：[ ok ] Restarting rsyslog (via systemctl): rsyslog.service.
```

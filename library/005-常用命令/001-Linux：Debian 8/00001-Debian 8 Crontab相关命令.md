# Debian 8 Crontab相关命令

## 修改系统的Crontab
```bash
vi /etc/crontab
```

## Crontab重启  

```bash
/etc/init.d/cron restart
```

## 打开Crontab日志功能

【第一步】
```bash
vi /etc/rsyslog.conf
```
【第二步】将下面语句最前面的#注释符号去掉
```bash
cron.*       /var/log/cron.log
```
【第三步】重启日志服务
```bash
/etc/init.d/rsyslog restart
```
成功则会提示 *提示：[ ok ] Restarting rsyslog (via systemctl): rsyslog.service.*

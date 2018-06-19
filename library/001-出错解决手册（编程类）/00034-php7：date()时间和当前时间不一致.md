# php7：date()时间和当前时间不一致
`【系统环境】debian 8`  
`【操作内容】php7.0`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
php中语句date("Y-m-d")出来的时间比当前恰好少一天
## <i class="fa fa-bullseye"></i> 根本原因
php的日期地区设置有问题
## <i class="fa fa-check-circle"></i> 解决方法
【第1步】查看php.ini的位置和当前时区的设置
编写一个test.php
```php
<?php
  phpinfo();
  echo (date("Y-m-d H:i:s \n"));
?>
```
然后运行：
```
php test.php |grep timezone
php test.php |grep php.ini
```
就会提示你的当前时区是什么、php.ini在什么位置  
【第2步】修改php.ini
```
[Date]
; Defines the default timezone used by the date functions
date.timezone = PRC
```
时区默认是注释的`UTC`,改为`PRC`或者`Asia/Shanghai`或者`Asia/Chongqing`  
【第3步】重启php-fpm
```
//1、杀掉php-fpm进程
/bin/ps -ef | grep 'php-fpm' | grep -v grep | cut -c 9-15 | xargs kill -9
//2、启动php-fpm
/usr/sbin/php-fpm7.0
```
【第4步】查看是否设置正确了
```
php test.php
```
看最后一条语句输出的时间是否正确。

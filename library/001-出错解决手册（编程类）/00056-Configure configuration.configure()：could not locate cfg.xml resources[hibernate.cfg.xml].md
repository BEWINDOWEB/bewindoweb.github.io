# Configure configuration.configure()：could not locate cfg.xml resources[hibernate.cfg.xml]
`【系统环境】windows 10`  
`【操作内容】Hibernate 5/ IntelliJ IDEA 2018.1`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
测试Hibernate时报错：
```
Configure configuration.configure()：could not locate cfg.xml resources[hibernate.cfg.xml]
```
## <i class="fa fa-bullseye"></i> 根本原因
配置文件路径有错导致找不到
## <i class="fa fa-check-circle"></i> 解决方法
将配置文件放在resources下面。
![](assets/001/20181214-7c3d2b67.png)  

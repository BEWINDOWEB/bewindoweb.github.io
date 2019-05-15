# @Slf4j注解正确log仍然报错
`【系统环境】windows 10`  
`【操作内容】idea 2018`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
@slf4j注解能够正确识别，但是log的语句仍然报错
## <i class="fa fa-bullseye"></i> 根本原因
idea没有安装lombok的插件
## <i class="fa fa-check-circle"></i> 解决方法
1、file->settings->plugins  
2、输入lombok→search in repositories  
3、在线安装lombok插件  
4、根据提示重启idea
![](assets/001/20190513-cb69aecb.png)  

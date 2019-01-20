# 测试msyql连接时报错：找不到mysql驱动
`【系统环境】windows 10`  
`【操作内容】mysql 5.6/ IntelliJ IDEA 2018.1`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
测试msyql连接时报错：  
找不到mysql驱动  
![](assets/001/20181214-8af8449b.png)
## <i class="fa fa-bullseye"></i> 根本原因
maven添加的jar包没被使用
## <i class="fa fa-check-circle"></i> 解决方法
maven搜索mysql的包，把正确的配置加进去：
![](assets/001/20181214-67c8fdbc.png)  
并且点击一下”MySQL“，在弹出的页面取消勾选默认的驱动：
![](assets/001/20181214-16576638.png)  
增加jar包的驱动：
![](assets/001/20181214-d84424e5.png)  
![](assets/001/20181214-b342194f.png)  
![](assets/001/20181214-ea26c9b5.png)  

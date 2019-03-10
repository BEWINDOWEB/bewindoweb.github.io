# 安装cool edit后提示没有找到混合器程序[sndvol32 \\r]
`【系统环境】windows 10`  
`【操作内容】cool edit 2.1`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
安装cool edit后点击【选项】→【录制调音台】，提示错误：`没有找到混合器程序[sndvol32 \r]`
## <i class="fa fa-bullseye"></i> 根本原因
`sndvol32`已经变为了`sndvol`
## <i class="fa fa-check-circle"></i> 解决方法
### 打开注册表
`win+R`，`regedit`
### 导航到路径
`HKEY_CURRENT_USER\SOFTWARE\Syntrillium\CEPro2\Tools`
### 更改取值
将`sndvol32 /r`改为`sndvol /r`

# Xftp拖拽提示无法从外部拖放Xftp
`【系统环境】windows 10`  
`【操作内容】xftp4`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
xftp拖拽时提示“无法从外部拖放Xftp，若要拖放需要在套中重新启动机器”：
![](assets/001/20190530-090e16fc.png)  

## <i class="fa fa-bullseye"></i> 根本原因
拖放DLL没有管理员权限

## <i class="fa fa-check-circle"></i> 解决方法
注册拖放的DLL。

### 1、以管理员身份打开CMD：
【xftp4】
```
# 64位系统
C:\Windows\SysWOW64\regsvr32.exe "C:\Program Files (x86)\Common Files\NetSarang\NsCopyHook.dll"
# 32位系统
C:\Windows\System32\regsvr32.exe "C:\Program Files\Common Files\NetSarang\NsCopyHook.dll"
```

【xftp5】
```
# 64位系统
C:\Windows\SysWOW64\regsvr32.exe "C:\Program Files (x86)\Common Files\NetSarang\nscopyhook2.dll"
# 32位系统
C:\Windows\System32\regsvr32.exe "C:\Program Files\Common Files\NetSarang\nscopyhook2.dll"
```

【xftp6】
```
# 64位系统
C:\Windows\SysWOW64\regsvr32.exe "C:\Program Files (x86)\Common Files\NetSarang\nscopyhook3.dll"
# 32位系统
C:\Windows\System32\regsvr32.exe "C:\Program Files\Common Files\NetSarang\nscopyhook3.dll"
```

### 2、重启计算机
重启Xftp是不行的，需要重启计算机

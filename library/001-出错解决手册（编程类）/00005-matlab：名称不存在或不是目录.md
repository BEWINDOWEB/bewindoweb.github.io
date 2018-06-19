# matlab：名称不存在或不是目录
`【系统环境】windows 8`  
`【操作内容】matlab R2014a`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
打开matlab出现警告：名称不存在或不是目录
## <i class="fa fa-bullseye"></i> 根本原因
之前通过addpath、savepath存入的路径目录已经被删除或者重命名了，造成找不到目录的问题。
## <i class="fa fa-check-circle"></i> 解决方法
【第1步】
```matlab
edit  pathdef.m
```
把找不到的目录路径删除，`ctrl+s`保存。  
【第2步】
```matlab
save path
```
【第3步】
重启matlab。

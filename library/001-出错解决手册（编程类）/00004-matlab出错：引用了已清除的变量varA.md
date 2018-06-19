# matlab出错：引用了已清除的变量varA
`【系统环境】windows 8`  
`【操作内容】matlab R2014a`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
matlab报错：
```matlab
引用了已清除的变量 varA。
```
## <i class="fa fa-bullseye"></i> 根本原因
开头加了一句清除语句，后来改成函数后忘了删除：
```matlab
clear;clc;
```
## <i class="fa fa-check-circle"></i> 解决方法
删除开头的清除语句

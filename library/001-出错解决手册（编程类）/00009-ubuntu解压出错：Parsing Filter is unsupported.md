# ubuntu解压出错：Parsing Filter is unsupported
`【系统环境】ubuntu 16.04 LTS`  
`【操作内容】解压RAR文件`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
ubuntu下使用Archive Manager解压RAR文件出错，提示Parsing Filter is unsupported
## <i class="fa fa-bullseye"></i> 根本原因
没有安装压缩/解压RAR相关的程序
## <i class="fa fa-check-circle"></i> 解决方法
安装rar
```bash
sudo apt install unrar
```

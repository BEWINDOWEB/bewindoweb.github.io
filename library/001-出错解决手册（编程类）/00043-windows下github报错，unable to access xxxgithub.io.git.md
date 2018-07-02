# windows下github报错，unable to access "xxxgithub.io.git":schannel failed to open CA file crt
`【系统环境】windows 8`  
`【操作内容】github desktop v1.2.6`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
提交本地仓库没问题，提交到github上时提示：
```
fatal: unable to access 'http://github.com/BEWINDOWEB/bewindoweb.github.io.git': schannel: failed to open CA file 'C:/Program Files/Git/mingw64/ssl/certs/ca-bundle.crt': No such progress
```
![](assets/001/20180701-302e171d.png)  

## <i class="fa fa-bullseye"></i> 根本原因
昨晚安装了windows下的docker，又觉得用vm建立linux启动docker再来跑容器的过程很不科学，因此放弃在windows下使用docker了，然而卸载的过程中同时也卸载了git，git是github desktop依赖的版本控制软件。

## <i class="fa fa-check-circle"></i> 解决方法
【第一步】下载[git for windows](https://git-scm.com/download/win)，我下载的是2.18.0 64位  
【第二步】安装git，一路`下一步`，全部选择默认的选项。  
【第三步】重启github desktop，再次提交，发现恢复了。

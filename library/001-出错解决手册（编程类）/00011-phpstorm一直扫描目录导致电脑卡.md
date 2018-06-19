# phpstorm一直扫描目录导致电脑卡
`【系统环境】windows 8`  
`【操作内容】phpstorm / gulp`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
在安装和部署完node.js、gulp之后，打开phpstorm会一直扫描目录，提示scanning files to index.....，导致电脑非常卡。
## <i class="fa fa-bullseye"></i> 根本原因
部署gulp的时候，生成的node_modules文件夹非常深，内含1000+个文件夹，导致扫描非常缓慢
![](assets/001/20180619-6515fe83.png)  
## <i class="fa fa-check-circle"></i> 解决方法
打开phpstorm，在node_modules文件夹上`右键`→`标记目录为（mark directory as）`→`排除（excluded）`
![](assets/001/20180619-c2af3b94.png)  

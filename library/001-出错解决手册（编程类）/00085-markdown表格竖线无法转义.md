# markdown表格竖线无法转义
`【系统环境】windows 10`  
`【操作内容】atom markdown`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
表格的竖线无法转义：
```
| 13 | 删除tag为none的镜像 | docker rmi $(docker images \| grep "^<none>" \| awk "{print $3}") | - |
```
![](assets/001/20190605-6eef4f54.png)  

## <i class="fa fa-bullseye"></i> 根本原因
表格竖线就是无法转义

## <i class="fa fa-check-circle"></i> 解决方法
使用[HTML ASCII字符集](https://www.runoob.com/tags/html-ascii.html)，竖线是124，因此用`&#124;`代替竖线即可，
```
| 13 | 删除tag为none的镜像 | docker rmi $(docker images &#124; grep "^<none>" &#124; awk "{print $3}") | - |
```
效果：
![](assets/001/20190605-04b5f721.png)  

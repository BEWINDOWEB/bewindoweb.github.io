# 该扩展程序未列在 Chrome 网上应用店中，并可能是在您不知情的情况下添加的
`【系统环境】windows 8`  
`【操作内容】Chrome 69.0.3497.100`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
安装完YAPI插件后翻墙，chrome检测到不是自己的插件，于是自动禁用了该插件：`该扩展程序未列在 Chrome 网上应用店中，并可能是在您不知情的情况下添加的`
## <i class="fa fa-bullseye"></i> 根本原因
Chrome没有设置白名单
## <i class="fa fa-check-circle"></i> 解决方法
### 下载官方策略  
官网下载（翻墙）：
[Zip file of ADM/ADMX templates and documentation](http://www.chromium.org/administrators/policy-templates)  
![](assets/002/20181126-4c5336d9.png)  
国内下载：
[百度云下载](https://pan.baidu.com/s/1eVgygS6JGOWNgopOF5kBjw )（密码a4yj）  
### 安装策略
1、将下载的文件解压，找到`windows\adm\zh-CN\chrome.adm`  
2、`win+R运行`→`gpedit.msc`，在`计算机配置`→`管理模板`上点右键，`添加/删除模板`：
![](assets/002/20181126-e74f1f71.png)  
3、`添加`，把`adm文件`添加进去：
![](assets/002/20181126-a6eda257.png)  
4、然后去chrome找到被禁用插件的ID，这时候启用按钮是点不了的：
![](assets/002/20181126-cf1a1f0d.png)  
5、打开`管理模板`，发现多了一个`经典管理模板adm`，打开其下的`Google`→`Google Chrome`→`扩展程序`，`配置扩展程序安装白名单`→`已启用`→`显示`，把刚刚的ID输入进去：
![](assets/002/20181126-14d39071.png)  
6、刷新一下chrome扩展程序页面，发现可以启用了：
![](assets/002/20181126-00237221.png)  

# Cannot load the system dictionary for zh-CN
`【系统环境】windows 10`  
`【操作内容】Atom 1.28.0`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
打开时总是提示：Cannot load the system dictionary for zh-CN
![](assets/001/20190317-0732018a.png)  

## <i class="fa fa-bullseye"></i> 根本原因
核心插件spell-check检查语法时使用了zh-CN,但在本地`C:\Users\BEWINDOWEB\AppData\Local\atom\app-1.28.0\resources\app.asar.unpacked\node_modules\spellchecker\vendor\hunspell_dictionaries`没有找到对应的语法字典:
![](assets/001/20190317-d6c37a5d.png)  

## <i class="fa fa-check-circle"></i> 解决方法
禁用中文语法检查，使用默认英文语法检查，因为使用Atom其实并不需要中文语法检查。  
1、打开spell-check插件  
`文件`→`设置`→`扩展`→`搜索spell-check`→`核心扩展`：
![](assets/001/20190317-7760651c.png)  
2、禁用zh-CN  
取消勾选Use Locales，然后LocalePaths填入en-US：
![](assets/001/20190317-1952120c.png)

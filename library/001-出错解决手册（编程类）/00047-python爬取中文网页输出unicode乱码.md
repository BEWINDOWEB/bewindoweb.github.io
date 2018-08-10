# python爬取中文网页输出乱码
`【系统环境】windows 8`  
`【操作内容】python 3`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
用Python爬取中文网页后输出：
```
\x1f\x8b\x08\x00\x00\x00\x00\x00\x00\x03\xbc\xbd\xdd\xae5Ir\
```
并且这种乱码不是简单的Unicode，而是夹杂着+号等符号的乱码。
## <i class="fa fa-bullseye"></i> 根本原因
网页采用了gzip压缩，不是简单的decode、encode能解决的。
## <i class="fa fa-check-circle"></i> 解决方法
使用gzip模块解压缩
```py
import gzip
gzip.decompress(html).decode("utf-8")
```
![](assets/001/20180811-bdd04866.png)  

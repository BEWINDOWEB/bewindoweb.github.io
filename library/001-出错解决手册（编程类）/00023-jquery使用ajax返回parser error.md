# jquery使用ajax返回parser error
`【系统环境】windows 8`  
`【操作内容】jquery 3.0中的ajax`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
使用Jquery的ajax的时候，error function报错。   
代码：
```js
error: erryFunction,  //错误执行方法
function erryFunction(XMLHttpRequest, textStatus, errorThrown) {
                    console.log(XMLHttpRequest.status);
                    console.log(XMLHttpRequest.readyState);
                    console.log(textStatus);
 }
```
错误信息：
```
XMLHttpRequest.status = 200
XMLHttpRequest.readyState = 4
textStatus = parser error
```
## <i class="fa fa-bullseye"></i> 根本原因
这是最常出现的一种错误，200已经请求成功，4已经解析完成，parser error表示解析出错，说明服务器没有返回信息或者格式不正确
## <i class="fa fa-check-circle"></i> 解决方法
服务器端的php写：
```php
echo json_encode($rs);
```

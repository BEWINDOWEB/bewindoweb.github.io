# ant design pro @antv data-set DataSet undefined
`【系统环境】windows 10`  
`【操作内容】webstorm 2018 / ant design pro v2`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
ant design pro 在展示图形数据的时候报错：
```
ReferenceError: DataSet is not defined
@antv/data-set
external "DataSet":1
> 1 | module.exports = DataSet;
```
## <i class="fa fa-bullseye"></i> 根本原因
document.ejs引用了
```
<script src="https://gw.alipayobjects.com/os/antv/pkg/_antv.data-set-0.9.6/dist/data-set.min.js"></script>
```
该网址文件如果无法访问则会报错
## <i class="fa fa-check-circle"></i> 解决方法
将node_modules中的data-set.min.js放到public，然后src这样写：
```
/data-set.min.js
```
就能够正常访问了。  
github issue:https://github.com/ant-design/ant-design-pro/issues/2773 

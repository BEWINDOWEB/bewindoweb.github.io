# matlab出错：在不同结构体之间进行下标赋值
`【系统环境】windows 8`  
`【操作内容】matlab R2014a`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
在赋值结构体的数组时，出现：
```
在不同结构体之间进行下标赋值：
出错test(line 25)
   st.ch(2) = d;
```
## <i class="fa fa-bullseye"></i> 根本原因
matlab结构体的赋值顺序必须相同才算是**相同的结构体**。
## <i class="fa fa-check-circle"></i> 解决方法
将结构体赋值顺序统一：
```matlab
c.ia = 1;
c.ib = [];
c.ic = st;

d.ia = 1;
d.ib = [];
d.ic = st;

root.ch(1) = c;
root.ch(2) = d;
```
ia，ib，ic对应进行赋值，不要调换顺序，就不会报错了。

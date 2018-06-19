# shell提示找不到变量
`【系统环境】debian 8.2`  
`【操作内容】shell(dash)`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
明明定义了变量，shell却提示：
```bash
./test.sh: 2: ./test.sh: cronfile: not found
./test.sh: 3: ./test.sh: basepath: not found
./test.sh: 4: ./test.sh: crontaskname: not found
```
## <i class="fa fa-bullseye"></i> 根本原因
定义变量的时候空格了，这是不正确的写法。
## <i class="fa fa-check-circle"></i> 解决方法
把空格去掉，比如：
```bash
myvar = "hello world!"
```
改为
```bash
myvar="hello world!"
```

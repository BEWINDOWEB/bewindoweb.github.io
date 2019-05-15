# SSH登陆时提示：enter passphrase for key
`【系统环境】windows10`  
`【操作内容】shell`  
`【解决方案验证次数】1次`

## <i class="fa fa-question-circle"></i> 出现问题
SSH登陆时提示：`enter passphrase for key /root/.ssh/id_rsa.pub`，可是无论是否输入密码，都报错无法登录。
## <i class="fa fa-bullseye"></i> 根本原因
本地没有拉起ssh-agent，导致外部机器回送公钥加密的字符串时，本地找不到对应私钥去解密，握手失败
## <i class="fa fa-check-circle"></i> 解决方法
拉起agent，把密钥加上（会默认加C:\Users\XXXXXX\.ssh\id_rsa）执行：
```
eval `ssh-agent`
ssh-add
```
注意：仅对一次session会话有效（一个Terminal）。

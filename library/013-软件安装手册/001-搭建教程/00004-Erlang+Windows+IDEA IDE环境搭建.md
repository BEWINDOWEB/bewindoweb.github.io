# Erlang + Windows + IDEA IDE环境搭建

## 相关信息
`【系统环境】windows 8（64位） / Erlang otp_win64_21.0.1（64位） / IDEA 2018`  
`【安装次数】1次`

## 一、安装Erlang
### 1、去Erlang官网下载对应的Erlang程序
官网地址：http://www.erlang.org/downloads  
下载链接：如果知道版本就会很简单，只需要替换对应版本的部分，例如下载21.3：
* 源码：http://erlang.org/download/otp_src_21.3.tar.gz
* win32：http://erlang.org/download/otp_win32_21.3.exe
* win64：http://erlang.org/download/otp_win64_21.3.exe

官网打开可能会很慢，但下载还算能够接受，可以去CSDN找一些资源下载会快一些。
* EMQ 2.3.11 的编译版本是 Erlang OTP 20.0，想要学习MQTT3.1/3.1.1的可以看2.x版本代码
* EMQ X 3.1-beta.1 Released 的编译版本是Erlang OTP 21.2，想要学习MQTT5.0的可以看3.x的代码

我下载的20.0.1。
### 2、安装Erlang
1）正常安装EXE  
2）配置Path环境变量，例如：`E:\erl10.0.1\bin`  
3）测试是否安装成功：cmd → `erl`：  
![](assets/013/20190313-3b01e564.png)  

## 二、配置IDEA的Erlang插件
1）打开IDEA，文件 → 设置 → 插件，搜索Erlang，界面提示本地们找到，是否搜索库：
![](assets/013/20190313-f647be88.png)  
2）搜索仓库，在线安装Erlang插件
![](assets/013/20190313-9ae70216.png)  
3）重启IDEA
![](assets/013/20190313-ae405eab.png)  

## 三、配置Rebar3
rebar3用来编译Erlang程序。  
1）下载rebar3  
打开IDEA，文件 → 设置 → 其他设置 → Erlang扩展工具 → 点击Download the latest rebar3：
![](assets/013/20190313-b36cd7a3.png)  
选择合适的文件夹，下载后，会自动填充路径：
![](assets/013/20190313-3b03c524.png)  
2）设置rebar3为编译器
设置 → 构建、执行和部署 → 编译器 → Erlang编译器 → 勾选Compile project with rebar、Add debug info：
![](assets/013/20190313-4fb37c6a.png)  

## 四、Erlang Hello World
1）文件 → 新建项目 → Erlang：
![](assets/013/20190313-77d04df6.png)  
2）配置SDK为Erlang安装根目录，会自动识别Erlang：
![](assets/013/20190313-8e61a3a0.png)  
3）建立一个名为hello的Erlang的文件
![](assets/013/20190313-6cf9611b.png)  
![](assets/013/20190313-579c0ec2.png)  
4）将默认生成的代码改为Helloworld：
默认生成代码：
```erl
%% API
-export([]).
```
Helloworld：
```erl
-export([start/0]).

start() ->
  io:fwrite("Hello, world!\n").
```
5) 配置编译
* 右上角选择编译结构
![](assets/013/20190313-e9dc18ad.png)  
* 增加一个Erlang Application
![](assets/013/20190313-b0f534e4.png)  
* 选择工程、选择要使用哪个模块的哪个函数来启动
![](assets/013/20190313-3fe5c12c.png)  

6）启动程序
![](assets/013/20190313-ef71f48f.png)  

## 五、配置文档
默认文档是去网上在线查的，这里改成本地查。  
选择文件 → 项目结构 → SDKs → Erlang 21 → 增加本地的doc文件目录：
![](assets/013/20190313-b4b78d4e.png)  
可以顺便把网上查的删掉。  
ctrl+Q就可以查系统函数了：  
![](assets/013/20190313-f3f83238.png)  

## 六、其他说明
一般用rebar的时候需要使用rebar.config来配置依赖包，程序的入口是`xxx.app.src`  
例如emq2.x：   
![](assets/013/20190313-e4409af7.png)  
1）建立rebar.config
```erl
{escript_incl_extra,[{"priv/templates/*","."}]}.

{erl_opts,
  [
    debug_info,
    {src_dirs,
      [
        "src"
      ]}
  ]
}.

{pre_hooks,[]}.

{cover_enabled, true}.
{sub_dirs,[
  "src"
]}.
```
2)建立hello.app.src（OTP application resource file）  
如果写的是hello.erl，mod则写hello：  
```erl
{application, hello, [
  {description, ""},
  {vsn, "1"},
  {registered, []},
  {applications, [
    kernel,
    stdlib
  ]},
  {mod, {hello, []}},
  {env, []}
]}.
```
![](assets/013/20190313-baf2a053.png)  

3）配置erlang rebar编译
![](assets/013/20190313-49d81ce8.png)  

4）执行rebar编译：
![](assets/013/20190313-b6c57dea.png)  
如果直接执行，会报错，原因是之前设置的rebar3路径被清空了，重新配置一次，这次不用Download了，直接选择。  
设置→其他设置→Erlang扩展工具→Path：  
![](assets/013/20190313-96a8e451.png)  
再编译就能通过了：  
![](assets/013/20190313-424811ab.png)  

5）执行编译后的程序  
找到编译后hello.app、hello.beam的路径：  
![](assets/013/20190313-bd282171.png)  
重新配置一个erlang application，将working directory配置成相应路径：  
![](assets/013/20190313-cc3d5e61.png)  
执行hello2，会产生和之前一样的结果：  
![](assets/013/20190313-b775cfc7.png)  

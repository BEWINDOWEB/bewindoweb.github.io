# C++读文件出错：no matching function for call to std::basic_ifstream
`【系统环境】ubuntu 14.04`  
`【操作内容】C++`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
C++使用ifstream在读文件时：
```cpp
std::string fp= "/home/dasdsa/123.txt";
std::ifstream fin( fp );
```
报错：
```cpp
error: no matching function for call to std::basic_ifstream<char>::open(std::string&)...
```
## <i class="fa fa-bullseye"></i> 根本原因
C++的std::string类无法作为open的参数
```cpp
std::string fp= "/home/dasdsa/123.txt";
```
## <i class="fa fa-check-circle"></i> 解决方法
使用字符数组：
```cpp
char fp[] = "/home/dasdsa/123.txt";
```

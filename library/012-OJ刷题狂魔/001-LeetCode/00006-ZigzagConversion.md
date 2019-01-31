# ZigzagConversion - Z 字形变换
### 题目描述
将一个给定字符串根据给定的行数，以从上往下、从左到右进行 Z 字形排列。  
比如输入字符串为 "LEETCODEISHIRING" 行数为 3 时，排列如下：
```
L   C   I   R
E T O E S I I G
E   D   H   N
```
之后，你的输出需要从左往右逐行读取，产生出一个新的字符串，比如："LCIRETOESIIGEDHN"。  
请你实现这个将字符串进行指定行数变换的函数：string convert(string s, int numRows);

>示例 1:  
输入: s = "LEETCODEISHIRING", numRows = 3  
输出: "LCIRETOESIIGEDHN"  

>示例 2:   
输入: s = "LEETCODEISHIRING", numRows = 4  
输出: "LDREOEIIECIHNTSG"  
解释:
```
L     D     R
E   O E   I I
E C   I H   N
T     S     G
```

### 涉及知识


### 第一次想到的解法
刚开始想直接模拟，后来发现有规律，每一横排相当于先往下走，再往上走，不断循环：  
下走：(numRows - i - 1) \* 2  
上走：i \* 2  
因此可以以行为循环，一次就得到整个字符串。  
注意处理边界问题：  
* 空串： "" , 3
* 单字符串单行： "A" , 1
* 多字符串但是单行： "AB", 1  

所有的边界都可以直接返回s来处理。

```Java
public String convert(String s, int numRows) {
    StringBuffer ans = new StringBuffer();

    if (s.length() <= numRows || numRows == 1)
        return s;

    for (int i = 0; i < numRows; i++){
        int j = i, skipLen = -1;
        boolean state = true;

        while(j < s.length() ){
            if (skipLen != 0){  //如果在边界，直接跳过一次存储
                ans.append(s.charAt(j));
            }
            skipLen = state ? (numRows - i - 1) * 2 : i * 2;
            state = !state;
            j += skipLen;
        }
    }

    return ans.toString();
}
```

### 标准题解

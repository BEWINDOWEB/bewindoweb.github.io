# LongestPalindromicSubstring - 最长回文子串
### 题目描述
给定一个字符串 s，找到 s 中最长的回文子串。你可以假设 s 的最大长度为 1000。
>示例 1：  
输入: "babad"  
输出: "bab"  
注意: "aba" 也是一个有效答案。  

>示例 2：  
输入: "cbbd"    
输出: "bb"  

### 涉及知识
substring：endIndex需要+1，原因就是在计算subLen的时候没有+1。  
JDK8 java.lang.String
```java
public String substring(int beginIndex, int endIndex) {
    if (beginIndex < 0) {
        throw new StringIndexOutOfBoundsException(beginIndex);
    }
    if (endIndex > value.length) {
        throw new StringIndexOutOfBoundsException(endIndex);
    }
    int subLen = endIndex - beginIndex;
    if (subLen < 0) {
        throw new StringIndexOutOfBoundsException(subLen);
    }
    return ((beginIndex == 0) && (endIndex == value.length)) ? this
            : new String(value, beginIndex, subLen);
}
```


### 第一次想到的解法
暴力破解，并且错误了两次：
* 没考虑到边界空串""
* 没考虑到偶数回文 cbba -> bb

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

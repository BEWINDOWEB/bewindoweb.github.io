# LongestSubstringWithoutRepeatingCharacters
### 题目描述
给定一个字符串，请你找出其中不含有重复字符的 最长子串 的长度。

>示例 1:  
输入: "abcabcbb"  
输出: 3  
解释: 因为无重复字符的最长子串是 "abc"，所以其长度为 3。  

>示例 2:  
输入: "bbbbb"  
输出: 1  
解释: 因为无重复字符的最长子串是 "b"，所以其长度为 1。  

>示例 3:  
输入: "pwwkew"  
输出: 3  
解释: 因为无重复字符的最长子串是 "wke"，所以其长度为 3。  

>请注意，你的答案必须是 子串 的长度，"pwke" 是一个子序列，不是子串。  

### 涉及知识


### 第一次想到的解法
用JAVA的集合很容易解决：
```Java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        int p = 0, q = 0;
        int maxlen = 0;
        Set characters = new HashSet();

        while (p < s.length()){
            char c = s.charAt(p);
            if (characters.contains(c)){ //重复了，更新长度
                maxlen = characters.size() > maxlen ? characters.size() : maxlen;
                while (s.charAt(q) != c){//移动指针到重复的位置
                    characters.remove(s.charAt(q));
                    q++;
                }
                q++; // 跳过重复的字符，c已经加入不必移出
                p++; // 指针前进
            } else {
                characters.add(c);
                p++; //前进
            }
        }
        maxlen = characters.size() > maxlen ? characters.size() : maxlen; // 再次更新长度
        return maxlen;
    }
}
```

### 标准题解

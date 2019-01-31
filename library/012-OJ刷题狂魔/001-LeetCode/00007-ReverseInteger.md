# ReverseInteger - 整数反转
### 题目描述
给出一个 32 位的有符号整数，你需要将这个整数中每位上的数字进行反转。

>示例 1:  
输入: 123  
输出: 321  

>示例 2:  
输入: -123  
输出: -321  

>示例 3:  
输入: 120  
输出: 21  
注意:  

假设我们的环境只能存储得下 32 位的有符号整数，则其数值范围为 [−2^31,  2^31 − 1]。  
请根据这个假设，如果反转后整数溢出那么就返回 0。

### 涉及知识


### 第一次想到的解法
第一反应是整数不断地取余整除之类的，符号不变，把数值反转即可，唯一要做的有一件事：
* 求整数长度：`int len = (x + "").length();`

结果WA遇到1534236469，应该溢出输出0，输出的却是溢出值2147483647，才想到考虑边界问题。  

既然有边界比较，那直接所有的操作都基于字符串不就好了吗，反转也不需要取余了，直接反转字符串更简单，最后和边界字符串比较一下：
* 如果合法就转为整数
* 不合法返回0。

这里的重点在于java.lang.String的compareTo方法，jdk8：
```
public int compareTo(String anotherString) {
    int len1 = value.length;
    int len2 = anotherString.value.length;
    int lim = Math.min(len1, len2);
    char v1[] = value;
    char v2[] = anotherString.value;

    int k = 0;
    while (k < lim) {
        char c1 = v1[k];
        char c2 = v2[k];
        if (c1 != c2) {
            return c1 - c2;
        }
        k++;
    }
    return len1 - len2;
}
```
从高位开始比较，如果有差异则返回ASCII的差值（0-9正好是0<1<...<9），如果比较的字符一模一样，则返回长度差值，无论怎样：
* 结果小于0：说明自己可能比被比较的字符串数值小
* 结果大于0：说明自己可能比被比较的字符串数值大

为什么是可能呢？因为如果"321"和"2147483647"比较，会在第一个字符"3">"2"误判"321">"2147483647"，所以当长度不等的时候，可以直接推断谁大谁小，当长度相等的时候，才使用compareTo去比较大小。

```Java
public int reverse(int x) {
        String symbol = x < 0 ? "-" : "";
        String y = x + "";
        StringBuffer z = new StringBuffer();

        y = x < 0 ? y.substring(1) : y;
        for (int i = y.length()-1; i >= 0; i--){
            z.append(y.charAt(i));
        }

        String ans = z.toString();
        String upbound = "2147483646";
        String lowbound = "2147483647";
        if (symbol.equals("-") && s1LessthanS2(ans,lowbound) || symbol.equals("") && s1LessthanS2(ans,upbound)){
            return Integer.parseInt(symbol+ans);
        }
        return 0;
    }

    public boolean s1LessthanS2(String s1, String s2){
        if (s1.length() < s2.length())
            return true;
        if (s2.length() < s1.length())
            return false;
        if (s1.compareTo(s2) <= 0)
            return true;
        return false;
    }
```

### 标准题解

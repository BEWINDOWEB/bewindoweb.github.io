# TwoSum
### 题目描述
给定一个整数数组，并返回他们的数组下标。  
你可以假设每种输入只会对应一个答案。但是，你不能重复利用这个数组中同样的元素。

>示例:  
给定 nums

### 涉及知识


### 第一次想到的解法
暴力破解
```Java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        for (int i = 0; i < nums.length; i++)
            for (int j = i+1; j < nums.length; j++){
                if (nums[i] + nums[j] == target)
                    return new int[]{i,j};
            }
        return null;
    }
}
```

### 标准题解

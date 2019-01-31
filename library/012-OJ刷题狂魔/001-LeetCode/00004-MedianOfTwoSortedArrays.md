# MedianOfTwoSortedArrays - 寻找两个有序数组的中位数
### 题目描述
给定两个大小为 m 和 n 的有序数组 nums1 和 nums2。  
请你找出这两个有序数组的中位数，并且要求算法的时间复杂度为 O(log(m + n))。  
你可以假设 nums1 和 nums2 不会同时为空。  

>示例 1:  
nums1 = [1, 3]  
nums2 = [2]  
则中位数是 2.0

>示例 2:  
nums1 = [1, 2]  
nums2 = [3, 4]  
则中位数是 (2 + 3)/2 = 2.5

### 涉及知识


### 第一次想到的解法
主要是考虑下用完的情况
```Java
class Solution {
    private int p = 0, q = 0;

    public double findMedianSortedArrays(int[] nums1, int[] nums2) {
        int len1 = nums1 == null ? 0 : nums1.length;
        int len2 = nums2 == null ? 0 : nums2.length;
        int allLen = len1 + len2;

        if (allLen % 2 == 0){ //中位数必然是两数之和
            int mid = allLen / 2 - 1;
            while(p + q < mid){
                getNext(nums1,nums2,len1,len2);
            }
            return (getNext(nums1,nums2,len1,len2) + getNext(nums1,nums2,len1,len2))/2.0;
        } else {
            int mid = allLen / 2;
            while(p + q < mid){
                getNext(nums1,nums2,len1,len2);
            }
            return (getNext(nums1,nums2,len1,len2));
        }
    }

    public int getNext(int[] nums1, int[] nums2, int len1, int len2){
        if (nums1 == null || p >= len1) // 如果num1用完了
            return nums2[q++];
        if (nums2 == null || q >= len2) // 如果num2用完了
            return nums1[p++];
        if (nums1[p] <= nums2[q]) //如果nums1更小
            return nums1[p++];
        return nums2[q++]; //nums2更小
    }

}
```

### 标准题解

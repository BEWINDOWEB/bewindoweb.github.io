# TwoSum - 两数相加
### 题目描述
给出两个`非空`的链表用来表示两个非负的整数。其中，它们各自的位数是按照`逆序`的方式存储的，并且它们的每个节点只能存储`一位`数字。  
如果，我们将这两个数相加起来，则会返回一个新的链表来表示它们的和。  
您可以假设除了数字 0 之外，这两个数都不会以 0 开头。  

>示例：
输入：(2 -> 4 -> 3) + (5 -> 6 -> 4)  
输出：7 -> 0 -> 8  
原因：342 + 465 = 807  

### 涉及知识


### 第一次想到的解法
简单的思路，不断加就行了，注意先更新和，再更新进位；先判断链表是否为空，再判断进位是否为0；在最后的时候不能光把当前指针置为null，需要记录它的父节点指针才行。  
一次提交就AC。
```Java
/**
public class ListNode {
    public int val;
    public ListNode next;

    public ListNode(int x) {
        val = x;
    }
}
 */
class Solution {
       public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        if (l1 == null)
            return l2;
        if (l2 == null)
            return l1;
        int c = 0, sum = 0;
        ListNode ans = new ListNode(0);
        ListNode head = ans;
        ListNode p = null;

        while (l1 != null && l2 != null){
            sum = (l1.val + l2.val + c) % 10;
            c = (l1.val + l2.val + c) / 10;
            ans.val = sum;
            ans.next = new ListNode(0);
            p = ans;
            ans = ans.next;
            l1 = l1.next;
            l2 = l2.next;
        }

        if (l1 != null){
            while(l1 != null){
                sum = (l1.val + c) % 10;
                c = (l1.val + c) / 10;
                ans.val = sum;
                ans.next = new ListNode(0);
                p = ans;
                ans = ans.next;
                l1 = l1.next;
            }
        }

        if (l2 != null){
            while(l2 != null){
                sum = (l2.val + c) % 10;
                c = (l2.val + c) / 10;
                ans.val = sum;
                ans.next = new ListNode(0);
                p = ans;
                ans = ans.next;
                l2 = l2.next;
            }
        }

        if (c != 0){
            ans.val = c;
            ans.next = null;
        } else {
            p.next = null;
        }

        return head;
    }
}
```

### 标准题解

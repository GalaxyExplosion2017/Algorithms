## [166 Nth to Last Node in List](http://www.lintcode.com/en/problem/nth-to-last-node-in-list/)

**Description**

Find the nth to last element of a singly linked list. 

The minimum number of nodes in list is n.

**Example**

Given a List  3->2->1->5->null and n = 2, return node  whose value is 1.

**解题思路**

> 创建两个指针，一个快指针fast，一个慢指针slow，都指向head，fast先往后移动n个结点，然后fast和slow都向后移动，直到fast指向null，slow就是相对链表尾的第n个结点，返回slow。

```java
/**
 * Definition for ListNode.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int val) {
 *         this.val = val;
 *         this.next = null;
 *     }
 * }
 */ 
public class Solution {
    /**
     * @param head: The first node of linked list.
     * @param n: An integer.
     * @return: Nth to last node of a singly linked list. 
     */
    ListNode nthToLast(ListNode head, int n) {
        // write your code here
        ListNode fast = head;
        ListNode slow = head;
        while(n-- >0) fast = fast.next;
        while(fast != null)
        {
            fast = fast.next;
            slow = slow.next;
        }
        return slow;
    }
}
```


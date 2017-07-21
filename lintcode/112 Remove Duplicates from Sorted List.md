## [112 Remove Duplicates from Sorted List](http://www.lintcode.com/en/problem/remove-duplicates-from-sorted-list/)

**Description**

Given a sorted linked list, delete all duplicates such that each element appear only *once*.

**Example**

Given `1->1->2`, return `1->2`.
Given `1->1->2->3->3`, return `1->2->3`.

**解题思路**

> 若头结点head不为空，创建一个结点L存储head的初始位置。如果head的下一个结点不为空，判断若head的值val与head的下一个结点的值val相同，则head指向head的下一个结点的下一个结点；若不相等，则head移动到下一个结点(head = head.next)，直到head的下一个结点为空，返回L。

```java
/**
 * Definition for ListNode
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    /**
     * @param ListNode head is the head of the linked list
     * @return: ListNode head of linked list
     */
    public static ListNode deleteDuplicates(ListNode head) { 
        // write your code here
        ListNode L = head;
        while(head!=null && head.next != null)
        {
            if(head.val == head.next.val)
                head.next = head.next.next;
            else
                head = head.next;
        }
        return L;
    }  
}
```


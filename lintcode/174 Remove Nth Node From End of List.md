## [174 Remove Nth Node From End of List](http://www.lintcode.com/en/problem/remove-nth-node-from-end-of-list/)

**Description**

Given a linked list, remove the $$n^{th}$$ node from the end of list and return its head.

** **Notice**

The minimum number of nodes in list is *n*.

**Example**

Given linked list: `1->2->3->4->5->null`, and *n* = `2`.After removing the second node from the end, the linked list becomes `1->2->3->5->null`.

**Intuition**

创建一个头结点dummy指向给定结点head，创建两个指针fast，slow，fast移动到它后n个位置，当fast.next  != null，fast和slow都移动到下一个结点直到fast.next = null，然后slow指向它下一个结点的后继结点，返回链表dummy.next。

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
     * @return: The head of linked list.
     */
    ListNode removeNthFromEnd(ListNode head, int n) {
        // write your code here
        ListNode dummy = new ListNode(0);
        dummy.next = head;
        ListNode fast = dummy;
        ListNode slow = dummy;
        while(n-- >0) fast = fast.next;
        while(fast.next != null)
        {
            fast = fast.next;
            slow = slow.next;
        }
        slow.next = slow.next.next;
        return dummy.next;
    }
}

```


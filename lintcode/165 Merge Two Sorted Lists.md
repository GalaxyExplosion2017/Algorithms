## [165 Merge Two Sorted Lists](http://www.lintcode.com/en/problem/merge-two-sorted-lists/)

**Description**

Merge two sorted (ascending) linked lists and return it as a new sorted list. The new sorted list should be made by splicing together the nodes of the two lists and sorted in ascending order.

**Example**

Given `1->3->8->11->15->null`, `2->null` , return `1->2->3->8->11->15->null`.

**解题思路 1**

> 递归。设计一个方法，比较l1结点的当前值与l2结点的当前值，如果l1.val < l2.val，则l1的下一个结点指向

```java
public class Solution {
    /**
     * @param ListNode l1 is the head of the linked list
     * @param ListNode l2 is the head of the linked list
     * @return: ListNode head of linked list
     */
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        // write your code here
        if(l1 == null) return l2;
        if(l2 == null) return l1;
        if(l1.val < l2.val)
        {
            l1.next = mergeTwoLists(l1.next,l2);
            return l1;
        }else{
            l2.next = mergeTwoLists(l1,l2.next);
            return l2;
        }
    }
}
```

**解题思路 2**

> 先判断l1和l2是否为空，有则返回另一个。然后创建一个新的链表l，头结点为node，遍历l1和l2，比较值将较小的放在node后面，直到其中一个链表遍历完毕，将剩下的另外一个链表放在node后面，最后返回l.next。

```java
public class Solution {
    /**
     * @param ListNode l1 is the head of the linked list
     * @param ListNode l2 is the head of the linked list
     * @return: ListNode head of linked list
     */
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        // write your code here
        if(l1 == null) return l2;
        if(l2 == null) return l1;
        ListNode l = new ListNode(0);
        ListNode node = l;
        while(l1 != null && l2 != null)
        {
            if(l1.val < l2.val)
            {
                node.next = l1;
                l1 = l1.next;
            }else{
                node.next = l2;
                l2 = l2.next;
            }
            node = node.next;
        }
        if(l1 != null) node.next = l1;
        if(l2 != null) node.next = l2;
        return l.next;
    }
}
```


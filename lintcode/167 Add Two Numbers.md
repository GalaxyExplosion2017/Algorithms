## [167 Add Two Numbers](http://www.lintcode.com/en/problem/add-two-numbers/)

**Description**

You have two numbers represented by a linked list, where each node contains a single digit. The digits are stored in `reverse` order, such that the 1's digit is at the head of the list. Write a function that adds the two numbers and returns the sum as a linked list.

**Example**

Given `7->1->6 + 5->9->2`. That is, `617 + 295`.Return `2->1->9`. That is `912`.Given `3->1->5` and `5->9->2`, return `8->0->8`.

**解题思路**

> 创建一个头结点head，当前结点node = head，两个遍历l1,l2的结点p1,p2，进位变量carry ，两个结点的和sum，遍历两个链表，当前两个结点的和等于两个结点的值加上进位权值，当前结点指向一个新结点，为两个结点和取模10后的值，然后移到下一个结点位置，进位权值等于前一次和除以10，直到两个链表遍历完毕，若遍历完毕后进位权值carry大于0，则当前结点指向值为carry的新结点，最后返回head.next。

```java
/**
 * Definition for singly-linked list.
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
     * @param l1: the first list
     * @param l2: the second list
     * @return: the sum list of l1 and l2 
     */
    public ListNode addLists(ListNode l1, ListNode l2) {
        // write your code here
        ListNode head = new ListNode(0);
        ListNode node = head;
        ListNode p1 = l1;
        ListNode p2 = l2;
        int carry = 0;
        while(p1 != null || p2 != null)
        {
            int x = (p1 != null) ? p1.val : 0;
            int y = (p2 != null) ? p2.val : 0;
            int sum = carry + x + y;
            carry = sum/10;
            node.next = new ListNode(sum % 10);
            node = node.next;
            if(p1 != null) p1 = p1.next;
            if(p2 != null) p2 = p2.next;
        }
        if(carry > 0) node.next = new ListNode(carry);
        return head.next;
    }
}
```


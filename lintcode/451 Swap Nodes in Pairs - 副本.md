## [451 Swap Nodes in Pairs](http://www.lintcode.com/en/problem/swap-nodes-in-pairs/)

##### Description

Given a linked list, swap every two adjacent nodes and return its head.

##### Example

Given `1->2->3->4`, you should return the list as `2->1->4->3`.

##### Solution

创建一个临时结点指向链表，若链表当前结点和下一个结点不为空，则交换它们位置，当前结点后移两位继续判断，直到它们中有一个为空。

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
public class Solution {
    /*
     * @param head: a ListNode
     * @return: a ListNode
     */
    public ListNode swapPairs(ListNode head) {
        // write your code here
        ListNode dummy = new ListNode(0);
        dummy.next = head;
        ListNode curr = dummy;
        while(curr.next != null && curr.next.next != null){
            ListNode first = curr.next;
            ListNode second = curr.next.next;
            first.next = second.next;
            second.next = first;
            curr.next = second;
            curr = curr.next.next;
        }
        return dummy.next;
    }
};
```

##### Solution 2

递归

```java
public class Solution {
    public ListNode swapPairs(ListNode head) {
        if ((head == null)||(head.next == null))
            return head;
        ListNode n = head.next;
        head.next = swapPairs(head.next.next);
        n.next = head;
        return n;
    }
}
```


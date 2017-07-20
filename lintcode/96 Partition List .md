# # [**96 Partition List** ](http://www.lintcode.com/en/problem/partition-list/)

**Description**

Given a linked list and a value x, partition it such that all nodes less than x come before nodes greater than or equal to x.

You should preserve the original relative order of the nodes in each of the two partitions.

**Example**

Given `1->4->3->2->5->2->null` and x = `3`,
return `1->2->2->4->3->5->null`.

**解题思路**

> 创建四个结点left,right,currLeft,currRight，两个初始值为0，left,right分别用来记录小于给定值的链表的头结点，和大于给定值的链表的头结点，另外两个结点currLeft,currRight用来分别记录两个链表的当前结点，遍历完毕后，然后将小于给定值的链表的当前结点的下一个结点指向大于给定值的链表，最后返回组合后的链表。

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
     * @param x: an integer
     * @return: a ListNode 
     */
    public ListNode partition(ListNode head, int x) {
        // write your code here
        ListNode left = new ListNode(0);
        ListNode right = new ListNode(0);
        ListNode currLeft = left , currRight = right;
        while(head!=null)
        {
            if(head.val<x) 
            {
                currLeft.next = head;
                currLeft = head;
            }else
            {
                currRight.next = head;
                currRight = head;
            }
            head = head.next;
        }
        currRight.next = null;
        currLeft.next = right.next;
        return left.next;
    }
}
```


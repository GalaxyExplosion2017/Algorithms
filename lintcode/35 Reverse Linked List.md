# 35 [Reverse Linked List](http://www.lintcode.com/en/problem/reverse-linked-list/)

**Description：**

Reverse a linked list.

**Example：**

For linked list `1->2->3`, the reversed linked list is `3->2->1`

**解题思路：**

> 逆置链接，将每个元素指向前一个元素即可。先新建一个结点prev->null，然后创建一个索引结点L，将头结点(head->1)赋给L，然后头结点指向下一个结点(head=head->next)，再使L结点(head结点)指向逆置到前一个结点prev->null,变成(L->1)->(prev->null),再把L->1赋给prev,变成(pre/L->1)->null,然后再把后一个结点(head->2)指向前一个结点(pre/L->1)->null,直到遍历完所有结点，都指向前一个结点(while(head!=null))。

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
     * @param head: The head of linked list.
     * @return: The new head of reversed linked list.
     */
    public ListNode reverse(ListNode head) {
        // write your code here
        ListNode prev = null;
        while(head!=null)
        {
            ListNode L=head;
            head=head.next;
            L.next=prev;
            prev=L;
        }
        return prev;
    }
}
```


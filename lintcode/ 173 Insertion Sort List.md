##  [**173 Insertion Sort List**](http://www.lintcode.com/en/problem/insertion-sort-list/)

**Description** 

Sort a linked list using insertion sort.

**Example** 

Given `1->3->2->0->null`, return `0->1->2->3->null`.

**Intuition**

创建一个值为0的结点dummy，创建一个结点node存储当前结点位置，遍历给定的结点head，将值小于node.next的放入node后面，直到遍历完head。

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
     * @return: The head of linked list.
     */
    public ListNode insertionSortList(ListNode head) {
        // write your code here
          ListNode dummy = new ListNode(0);
        // 这个dummy的作用是，把head开头的链表一个个的插入到dummy开头的链表里
        // 所以这里不需要dummy.next = head;
        while(head != null)
        {
            ListNode node = dummy;
            while(node.next != null && node.next.val < head.val)
                node = node.next;
            ListNode temp = head.next;
            head.next = node.next;
            node.next = head;
            head = temp;
        }
        return dummy.next;
    }
}
```


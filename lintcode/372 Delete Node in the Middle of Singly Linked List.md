## [372 Delete Node in the Middle of Singly Linked List](http://www.lintcode.com/en/problem/delete-node-in-the-middle-of-singly-linked-list/)

##### Description

Implement an algorithm to delete a node in the middle of a singly linked list, given only access to that node.

**Example**

Linked list is `1->2->3->4`, and given node `3`, delete the node in place `1->2->4`

##### Solution

将要删除结点的下一个结点的值赋给当前结点，下一个结点的next赋给当前结点

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
     * @param node: the node in the list should be deleted
     * @return: nothing
     */
    public void deleteNode(ListNode node) {
        // write your code here
        if (node == null) return;
        if (node.next != null) {
            node.val = node.next.val;
            node.next = node.next.next;
        }
        return;
    }
}
```


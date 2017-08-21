#### [453 Flatten Binary Tree to Linked List](http://www.lintcode.com/en/problem/flatten-binary-tree-to-linked-list/)

##### Description

Flatten a binary tree to a fake "linked list" in pre-order traversal.

Here we use the *right* pointer in TreeNode as the *next*pointer in ListNode.

##### ** Notice

Don't forget to mark the left child of each node to null. Or you will get Time Limit Exceeded or Memory Limit Exceeded.

##### Example

```
              1
               \
     1          2
    / \          \
   2   5    =>    3
  / \   \          \
 3   4   6          4
                     \
                      5
                       \
                        6
```

##### Solution

二叉树是先序的，因此把铺平成链表，就应该倒着遍历。先定义一个结点pre，每次把最下方的结点指向pre，然后再把当前根结点赋给pre，直到遍历完毕。

```java
/**
 * Definition of TreeNode:
 * public class TreeNode {
 *     public int val;
 *     public TreeNode left, right;
 *     public TreeNode(int val) {
 *         this.val = val;
 *         this.left = this.right = null;
 *     }
 * }
 */


public class Solution {
    /*
     * @param root: a TreeNode, the root of the binary tree
     * @return: 
     */
    private TreeNode pre = null;
    public void flatten(TreeNode root) {
        // write your code here
        if(root == null) return ;
        flatten(root.right);
        flatten(root.left);
        root.right = pre;
        root.left = null;
        pre = root;
    }
};
```


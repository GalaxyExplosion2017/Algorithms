# [85 Insert Node in a Binary Search Tree](http://www.lintcode.com/en/problem/insert-node-in-a-binary-search-tree/)

**Description**

Given a binary search tree and a new tree node, insert the node into the tree. You should keep the tree still be a valid binary search tree.

> #####  Notice
>
> You can assume there is no duplicate values in this tree + node.

**Example**

Given binary search tree as follow, after Insert node 6, the tree should be:

```
  2             2
 / \           / \
1   4   -->   1   4
   /             / \ 
  3             3   6
```

**解题思路 1**

> 递归

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
    /**
     * @param root: The root of the binary search tree.
     * @param node: insert this node into the binary search tree
     * @return: The root of the new binary search tree.
     */
    public TreeNode insertNode(TreeNode root, TreeNode node) {
        // write your code here
        if(root == null) return node;
        if(root.val > node.val)
            root.left = insertNode(root.left,node);
        else
            root.right = insertNode(root.right,node);
        return root;
    }
}
```



**解题思路 2**

> 迭代.建立两个树结点，先用curr找到node在BST的位置，让pre作为curr的根节点；找到node的位置后，curr指向null。此时，用node代替curr与pre连接就可以了。返回root。

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
    /**
     * @param root: The root of the binary search tree.
     * @param node: insert this node into the binary search tree
     * @return: The root of the new binary search tree.
     */
    public TreeNode insertNode(TreeNode root, TreeNode node) {
        // write your code here
        if(root == null) return node;
        TreeNode curr = root;
        TreeNode pre = null;
        while(curr != null)
        {
            pre = curr;
            if(curr.val>node.val) curr = curr.left;
            else curr = curr.right;
        }
        if(pre != null)
        {
            if(pre.val > node.val) pre.left = node;
            else pre.right = node;
        }
        return root;
    }
}
```


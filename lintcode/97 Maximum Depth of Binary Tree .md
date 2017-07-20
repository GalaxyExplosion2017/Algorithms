# [97 Maximum Depth of Binary Tree ](http://www.lintcode.com/en/problem/maximum-depth-of-binary-tree/#)

**Description**

Given a binary tree, find its maximum depth.

The maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.

**Example**

Given a binary tree as follow:

```
  1
 / \ 
2   3
   / \
  4   5

```

The maximum depth is `3`.

**解题思路**

> 递归。若当前结点不为空，遍历二叉树，找到每个结点的子树的深度，依次将深度返回给当前结点的根结点。

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
     * @param root: The root of binary tree.
     * @return: An integer.
     */
    public int maxDepth(TreeNode root) {
        // write your code here
        if(root == null) return 0;
        int ld = maxDepth(root.left);
        int rd = maxDepth(root.right);
        return Math.max(ld,rd)+1;
    }
}
```


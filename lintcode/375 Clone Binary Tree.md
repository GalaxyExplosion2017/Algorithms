## [375 Clone Binary Tree](http://www.lintcode.com/en/problem/clone-binary-tree/)

##### Description

For the given binary tree, return a **deep copy** of it.

**Example **

Given a binary tree:

```
     1
   /  \
  2    3
 / \
4   5
```

return the new binary tree with same structure and same value:

```
     1
   /  \
  2    3
 / \
4   5
```

##### Solution

递归。若给定的结点root不为空，创建一个值为root.val的结点，继续判断给定结点root的左右结点，直到root为空。

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
     * @param root: The root of binary tree
     * @return root of new tree
     */
    public TreeNode cloneTree(TreeNode root) {
        // Write your code here
        if(root == null) return null;
        TreeNode clone_Tree = new TreeNode(root.val);
        clone_Tree.left = cloneTree(root.left);
        clone_Tree.right = cloneTree(root.right);
        return clone_Tree;
    }
}
```


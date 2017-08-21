## [469 Identical Binary Tree](http://www.lintcode.com/en/problem/identical-binary-tree/)

##### Description

Check if two binary trees are identical. Identical means the two binary trees have the same structure and every identical position has the same value.

##### Example

```
    1             1
   / \           / \
  2   2   and   2   2
 /             /
4             4

```

are identical.

```
    1             1
   / \           / \
  2   3   and   2   3
 /               \
4                 4

```

are not identical.

##### Solution

递归，比较两个树根结点的值和左右子树根结点的值

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
     * @param a: the root of binary tree a.
     * @param b: the root of binary tree b.
     * @return: true if they are identical, or false.
     */
    public boolean isIdentical(TreeNode a, TreeNode b) {
        // write your code here
        if(a == null && b == null) return true;
        if(a == null || b == null) return false;
        return (a.val == b.val) && isIdentical(a.left , b.left) && isIdentical(a.right , b.right); 
    }
};
```




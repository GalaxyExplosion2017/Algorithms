# [93 Balanced Binary Tree](http://www.lintcode.com/en/problem/balanced-binary-tree/) 

**Description**

Given a binary tree, determine if it is height-balanced.

For this problem, a height-balanced binary tree is defined as a binary tree in which the depth of the two subtrees of every node never differ by more than 1.

**Example**

Given binary tree A = `{3,9,20,#,#,15,7}`, B = `{3,#,20,15,7}`

```
A)  3            B)    3 
   / \                  \
  9  20                 20
    /  \                / \
   15   7              15  7

```

The binary tree A is a height-balanced binary tree, but B is not.

**解题思路**

> 若根结点存在，遍历左右子树，比较左右子树的深度，若深度差不超过1，则使平衡二叉树

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
     * @return: True if this Binary tree is Balanced, or false.
     */
    public boolean isBalanced(TreeNode root) {
        // write your code here
        return deepth(root)!=-1;
    }
    public int deepth(TreeNode node)
    {
        if(node == null) return 0;
        int left = deepth(node.left);
        int right = deepth(node.right);
        if(left == -1||right == -1||Math.abs(left-right)>1) return -1;
        return Math.max(left,right)+1;
    }
}
```


## [**155 Minimum Depth of Binary Tree**](http://www.lintcode.com/en/problem/minimum-depth-of-binary-tree/#)

**Description**

Given a binary tree, find its minimum depth.

The minimum depth is the number of nodes along the shortest path from the root node down to the nearest leaf node.

**Example**

Given a binary tree as follow:

```
  1
 / \ 
2   3
   / \
  4   5
```

The minimum depth is `2`

**解题思路**

> 如果二叉树是左子树或者是右子树，则只遍历唯一的子树；若两个子树都存在，则取深度最小的子树。

```java
public class Solution {
    /**
     * @param root: The root of binary tree.
     * @return: An integer.
     */
    public int minDepth(TreeNode root) {
        // write your code here
        if(root == null) return 0;
        if(root.left == null) return minDepth(root.right)+1;
        if(root.right == null) return minDepth(root.left)+1;
        return Math.min(minDepth(root.left),minDepth(root.right))+1;
    }
}
```


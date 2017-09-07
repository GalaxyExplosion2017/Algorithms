## [661 Convert BST to Greater Tree](http://www.lintcode.com/en/problem/convert-bst-to-greater-tree/)

##### Description

Given a Binary Search Tree (BST), convert it to a Greater Tree such that every key of the original BST is changed to the original key plus sum of all keys greater than the original key in BST.

#####Example

Given a binary search Tree `{5,2,3}`:

```
              5
            /   \
           2     13

```

Return the root of new tree

```
             18
            /   \
          20     13
```

##### Solution

中序遍历二叉树

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
     * @param root: the root of binary tree
     * @return: the new root
     */
    int tmp = 0;
    public TreeNode convertBST(TreeNode root) {
        // write your code here
        if(root == null) return null;
        convertBST(root.right);
        root.val += tmp;
        tmp = root.val;
        convertBST(root.left);
        return root;
    }
}
```


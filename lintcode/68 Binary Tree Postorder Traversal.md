# [**68 Binary Tree Postorder Traversal**](http://www.lintcode.com/en/problem/binary-tree-postorder-traversal/#)

**Description**

Given a binary tree, return the *postorder* traversal of its nodes' values.

**Example**

Given binary tree `{1,#,2,3}`,

```
   1
    \
     2
    /
   3
 
```

return `[3,2,1]`.

**解题思路 1**

> 递归。编写一个方法，若当前的结点的左右结点存在，继续递归该方法的左右结点，直到叶子结点，然后将当前结点的值加入list中，直到遍历完根结点的所有左右结点，再把根结点的值加入到list中，返回list。

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
     * @return: Postorder in ArrayList which contains node values.
     */
    public ArrayList<Integer> postorderTraversal(TreeNode root) {
        // write your code here
        ArrayList<Integer> list = new ArrayList<Integer>();
        traverse(root,list);
        return list;
        
    }
    public void traverse(TreeNode root,ArrayList<Integer> list)
    {
        if(root==null) return;
        if(root.left!=null) traverse(root.left,list);
        if(root.right!=null) traverse(root.right,list);
        list.add(root.val);
    }
}
```

**解题思路 2**



```java

```


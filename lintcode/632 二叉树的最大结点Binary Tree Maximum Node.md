# 632 二叉树的最大结点		Binary Tree Maximum Node

>先判断根结点是否为空，然后遍历每一个子结点，直到叶子结点的父节点，然后比较每个左右叶子结点的值，其中最大值与父节点比较，再回到上一级父节点进行比较，直到与根结点比较.

```java
public class Solution {
    /**
     * @param root the root of binary tree
     * @return the max ndoe
     */
    public TreeNode maxNode(TreeNode root) 
    {
        // Write your code here
        if(root==null) return root;
        TreeNode left = maxNode(root.left);
        TreeNode right = maxNode(root.right);
        return max(root,max(left,right));
    }
    
    public TreeNode max(TreeNode l,TreeNode r)
    {
       if(l==null) return r;
       if(r==null) return l;
       if(l.val>=r.val) return l;
       return r;
       
    }
}
```


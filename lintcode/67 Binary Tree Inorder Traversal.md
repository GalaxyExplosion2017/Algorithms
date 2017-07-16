# [67 Binary Tree Inorder Traversal](http://www.lintcode.com/en/problem/binary-tree-inorder-traversal/#)

**Description**

Given a binary tree, return the *inorder* traversal of its nodes' values.

**Example**

Given binary tree `{1,#,2,3}`,

```
   1
    \
     2
    /
   3 
```

return `[1,3,2]`.

**解题思路 1**

> 递归。编写一个方法，若当前根结点存在，则判断左结点是否存在，若存在，继续递归直到叶子结点，然后将当前根结点值加入list中，再判断右结点是否存在，若存在同学继续递归直到叶子结点。

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
     * @return: Inorder in ArrayList which contains node values.
     */
    public ArrayList<Integer> inorderTraversal(TreeNode root) {
        // write your code here
        ArrayList<Integer> list = new  ArrayList<Integer>();
        traverse(root,list);
        return list;   
    }
    public void traverse(TreeNode root,ArrayList<Integer> list)
    {
        if(root==null)  return;
        if(root.left!=null) traverse(root.left,list);
        list.add(root.val);
        if(root.right!=null) traverse(root.right,list);
    }
}
```



**解题思路 2**

> 迭代，创建一个临时结点node存储当前遍历的结点，判断根结点的左子树结点是否存在，若存在，遍历左结点，存在则将左结点和当前根结点入栈，直到叶子结点，然后再出栈，判断右结点是否存在，存在则入栈，继续上述判断，直到node==null则出栈，直到左子树遍历完毕，再以同样的方法遍历右子树。

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
     * @return: Inorder in ArrayList which contains node values.
     */
    public ArrayList<Integer> inorderTraversal(TreeNode root) {
        // write your code here
        ArrayList<Integer> list = new  ArrayList<Integer>();
        Stack<TreeNode> stack = new Stack<TreeNode>();
        TreeNode node = root;
        while(!stack.isEmpty()||node!=null)
        {
            while(node!=null)
            {
                stack.add(node);
                node=node.left;
            }
            node=stack.pop();
            list.add(node.val);
            node=node.right;           
        }
        return list;
    }
}
```


# [66 Binary Tree Preorder Traversal](http://www.lintcode.com/en/problem/binary-tree-preorder-traversal/#)

**Description**

Given a binary tree, return the preorder traversal of its nodes' values.

**Example**

Given:

```
    1
   / \
  2   3
 / \
4   5
```

return `[1,2,4,5,3]`.

**解题思路 1** 

> 递归.创建一个遍历根结点左右结点的方法，然后不停的递归这个方法直到叶子结点。

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
     * @return: Preorder in ArrayList which contains node values.
     */
    public ArrayList<Integer> preorderTraversal(TreeNode root) {
        // write your code here
        ArrayList<Integer> list = new ArrayList<Integer>();
        traverse(root,list);
        return list;
    }
    public void traverse(TreeNode root,ArrayList<Integer> list)
    {
        if(root==null) 
            return ;
        list.add(root.val);
        traverse(root.left,list);
        traverse(root.right,list);
    }
}
```

**解题思路 2**

> 迭代。创建一个栈stack，作为辅助存储空间，先将根结点入栈，若栈不为空，则将当前结点出栈，然后先判断是否有右结点，若有则右结点入栈，再判断是否有做结点，若有也入栈，直到遍历到叶子结点，然后将栈内所有元素出栈，直到栈为空。

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
     * @return: Preorder in ArrayList which contains node values.
     */
    public ArrayList<Integer> preorderTraversal(TreeNode root) {
        // write your code here
        ArrayList<Integer> list = new ArrayList<Integer>();
        Stack<TreeNode> stack = new Stack();
        if(root==null)
            return list;
        stack.push(root);
        while(!stack.isEmpty())
        {
            TreeNode node = stack.pop();
            list.add(node.val);
            if(node.right!=null)
                stack.push(node.right);
            if(node.left!=null)
                stack.push(node.left);
        }
        return list;
    }
}
```


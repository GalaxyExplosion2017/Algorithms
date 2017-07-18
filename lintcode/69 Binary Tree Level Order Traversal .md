# [69 Binary Tree Level Order Traversal ](http://www.lintcode.com/en/problem/binary-tree-level-order-traversal/)

**Description**

Given a binary tree, return the *level order* traversal of its nodes' values. (ie, from left to right, level by level).

**Example**

Given binary tree `{3,9,20,#,#,15,7}`,

```
    3
   / \
  9  20
    /  \
   15   7
```

return its level order traversal as:

```
[
  [3],
  [9,20],
  [15,7]
]
```

**解题思路**

> 深度优先遍历。创建一个递归方法，当当前结点不为0时，若list中元素个数等于深度，在list中加入一个匿名链表ArrayList<Integer>，将当前结点的值加入该匿名链表中；若不等于深度，递归遍历当前结点的左结点和右结点，直到当前结点为空。

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
     * @return: Level order a list of lists of integer
     */
    public ArrayList<ArrayList<Integer>> levelOrder(TreeNode root) {
        // write your code here
        ArrayList<ArrayList<Integer>> list = new ArrayList<ArrayList<Integer>>();
        DFS(list,root,0);
        return list;
    }
    public void DFS(ArrayList<ArrayList<Integer>> list,TreeNode node,int deepth)
    {
        if(node==null) return ;
        if(list.size()==deepth)
            list.add(new ArrayList<Integer>());
        list.get(deepth).add(node.val);
        DFS(list,node.left,deepth+1);
        DFS(list,node.right,deepth+1);
    }
}
```


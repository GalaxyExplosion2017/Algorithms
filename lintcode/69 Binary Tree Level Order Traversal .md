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

**解题思路 1**

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

**解题思路 2**

> 广度优先遍历。若当前结点不为空，创建一个队列，将当前结点加入队列中，若队列中有元素，创建一个level列表，将当前队列中的元素出队，作为当前结点，将它的值加入到list中，若当前结点的左右结点存在，则将它的左右结点加入到队列中，重复上述判断，直到队列中无元素，返回list列表。

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
       if(root==null) return list;
       Queue<TreeNode> queue = new LinkedList<TreeNode>();
       queue.add(root);
       while(queue.size()>0)
       {
           ArrayList<Integer> level = new ArrayList<Integer>();
           int size = queue.size();
           for(int i=0;i<size;i++)
           {
                TreeNode node = queue.poll();
                level.add(node.val);
                if(node.left!=null) queue.add(node.left);
                if(node.right!=null) queue.add(node.right);
           }
           list.add(level);
       }
       return list;
    }
}
```


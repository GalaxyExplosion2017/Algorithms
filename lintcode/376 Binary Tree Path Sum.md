## [376 Binary Tree Path Sum](http://www.lintcode.com/en/problem/binary-tree-path-sum/)

##### Description

Given a binary tree, find all paths that sum of the nodes in the path equals to a given number `target`.

A valid path is from root node to any of the leaf nodes.

**Example**

Given a binary tree, and target = `5`:

```
     1
    / \
   2   4
  / \
 2   3
```

return

```
[
  [1, 2, 2],
  [1, 4]
]
```

##### Solution

将二叉树的每条路径上面的结点的值加入当前path中，若路径和正好等于给定的target，则将当前path加入到list中，遍历完一条路径后，则将除了根结点外的其他结点值清空，继续遍历下一条结点，直到遍历完所有路径。

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
     * @param root the root of binary tree
     * @param target an integer
     * @return all valid paths
     */
    public List<List<Integer>> binaryTreePathSum(TreeNode root, int target) {
        // Write your code here
        List<List<Integer>> list = new ArrayList<List<Integer>>();
        if(root == null || target == 0){
            return list;
        } 
        List<Integer> path = new ArrayList<Integer>();
        path.add(root.val);
        dfs(list, path, root, target, root.val);
        return list;
    }
    
    
    public void dfs(List<List<Integer>> list, List<Integer> path, TreeNode root, int target, int sum) {
        // 遇到叶子节点的返回条件
        if (root.left == null && root.right == null) {
            if (sum == target) {
                list.add(new ArrayList<Integer>(path));
            }
            return;
        }
        
        if (root.left != null) {
            path.add(root.left.val);
            dfs(list, path, root.left, target, sum + root.left.val);
            path.remove(path.size() - 1);
        }
        
        if (root.right != null) {
            path.add(root.right.val);
            dfs(list, path, root.right, target, sum + root.right.val);
            path.remove(path.size() - 1);
        }
    }
    
}
```


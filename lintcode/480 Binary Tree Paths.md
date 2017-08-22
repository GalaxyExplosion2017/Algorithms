## [480 Binary Tree Paths](http://www.lintcode.com/en/problem/binary-tree-paths/)

##### Description

Given a binary tree, return all root-to-leaf paths.

##### Example

Given the following binary tree:

```
   1
 /   \
2     3
 \
  5

```

All root-to-leaf paths are:

```
[
  "1->2->5",
  "1->3"
]
```

##### Solution

创建一个String类型的链表paths，遍历根结点的左右子树的路径path，将根结点的值+"->"+左右子树的路径path加入paths中，返回paths

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
     * @param root the root of the binary tree
     * @return all root-to-leaf paths
     */
    
    public List<String> binaryTreePaths(TreeNode root) {
        // Write your code here
        ArrayList<String> paths = new ArrayList<String>();
        if(root == null) return paths;
        if(root.left == null && root.right == null){
            paths.add(root.val+"");
            return paths;
        }
        for(String path : binaryTreePaths(root.left)){
            paths.add(root.val + "->" + path);
        }
        for(String path : binaryTreePaths(root.right)){
            paths.add(root.val + "->" + path);
        }
        return paths;
    }
}
```


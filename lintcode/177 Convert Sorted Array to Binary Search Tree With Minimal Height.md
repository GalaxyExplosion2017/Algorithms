##### [177 Convert Sorted Array to Binary Search Tree With Minimal Height](http://www.lintcode.com/en/problem/convert-sorted-array-to-binary-search-tree-with-minimal-height/#)

**Description**

Given a sorted (increasing order) array, Convert it to create a binary tree with minimal height.

##### **Notice

There may exist multiple valid solutions, return any of them.

**Example**

Given `[1,2,3,4,5,6,7]`, return

```
     4
   /   \
  2     6
 / \    / \
1   3  5   7
```

**Solution**

利用二叉查找树，根结点为数组的中值，数组的左结点为中值左部分的中值，右结点为中值右部分中值...直到数组所有的数构造完二叉树，返回根结点。

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
     * @param A: an integer array
     * @return: a tree node
     */
    public TreeNode sortedArrayToBST(int[] A) {  
        // write your code here
        if(A == null || A.length == 0) return null;
        return sortedArrayToBST(A, 0, A.length-1);
    }
    public TreeNode sortedArrayToBST(int[] A, int low, int high){
        if(low > high) return null;
        int mid = (low+high)/2;
        TreeNode root = new TreeNode(A[mid]);
        root.left = sortedArrayToBST(A, low, mid-1);
        root.right = sortedArrayToBST(A, mid+1, high);
        return root;
    }
}

```




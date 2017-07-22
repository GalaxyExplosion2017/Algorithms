## [110 Minimum Path Sum](http://www.lintcode.com/en/problem/minimum-path-sum/)

**Description**

Given a **m x n** grid filled with non-negative numbers, find a path from top left to bottom right which ***minimizes*** the sum of all numbers along its path.

#####  \*Notice

You can only move either down or right at any point in time.

**解题思路**

> 动态规划。从下右方最后一个数倒推，矩阵中的元素grid\[i][j]等于它上方grid\[i-1][j]和左方grid\[i][j-1]的最小值，利用公式，然后初值从左上第一个数开始找下游两个数中的最小值相加，直到遍历完毕**需要注意**单行时grid\[i][j]只能等于grid\[i][j-1]，单列时grid\[i][j]只能等于grid\[i-1][j]。

```java
public class Solution {
    /**
     * @param grid: a list of lists of integers.
     * @return: An integer, minimizes the sum of all numbers along its path
     */
    public int minPathSum(int[][] grid) {
        // write your code here
        int m = grid.length;
        int n = grid[0].length;
        for(int i = 0; i < m; i++)
        {
            for(int j = 0; j < n; j++)
            {
                if(i == 0 && j > 0)
                    grid[i][j] += grid[i][j-1];
                if(i > 0 && j == 0)
                    grid[i][j] += grid[i-1][j];
                if(i > 0 && j > 0)
                    grid[i][j] += Math.min(grid[i][j-1],grid[i-1][j]);
            }
        }
        return grid[m-1][n-1];
    }
}
```


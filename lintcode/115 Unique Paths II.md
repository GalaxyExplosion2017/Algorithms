## [115 Unique Paths II](http://www.lintcode.com/en/problem/unique-paths-ii/)

**Description**

Follow up for "Unique Paths":

Now consider if some obstacles are added to the grids. How many unique paths would there be?

An obstacle and empty space is marked as `1` and `0`respectively in the grid.

##### ** Notice

*m* and *n* will be at most 100.

**Example**

For example,
There is one obstacle in the middle of a 3x3 grid as illustrated below.

```
[
  [0,0,0],
  [0,1,0],
  [0,0,0]
]
```

The total number of unique paths is `2`.

**解题思路**

> 对输入数组的左上两个边界进行赋值，第一个数obstacleGrid\[0][0]为0，其余的数若为1，则赋予0；若不为1，则与前一个数相同。除了左上边界的数的值，若为1，则赋予0；若不为1，则等于左上两个数之和。

```java
public class Solution {
    /**
     * @param obstacleGrid: A list of lists of integers
     * @return: An integer
     */
    public int uniquePathsWithObstacles(int[][] obstacleGrid) {
        // write your code here
        int m = obstacleGrid.length;
        int n = obstacleGrid[0].length;
        obstacleGrid[0][0] ^= 1;
        for(int i = 1; i < m; i++)
            obstacleGrid[i][0] = obstacleGrid[i][0] == 1 ? 0 : obstacleGrid[i-1][0];
        for(int j = 1; j < n; j++)
            obstacleGrid[0][j] = obstacleGrid[0][j] == 1 ? 0 : obstacleGrid[0][j-1];
        for(int i = 1 ; i < m; i++)
            for(int j = 1; j < n; j++)
                obstacleGrid[i][j] = obstacleGrid[i][j] == 1 ?  0 : obstacleGrid[i-1][j]+obstacleGrid[i][j-1];
        return obstacleGrid[m-1][n-1];
    }
}
```


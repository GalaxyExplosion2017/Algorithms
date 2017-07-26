## [114 Unique Paths](http://www.lintcode.com/en/problem/unique-paths/)

**Description**

A robot is located at the top-left corner of a *m* x *n* grid.

The robot can only move either down or right at any point in time. The robot is trying to reach the bottom-right corner of the grid.

How many possible unique paths are there?

##### ** Notice

***m*** and ***n*** will be at most 100.

**Example**Given m = `3` and n = `3`, return `6`.
Given m = `4` and n = `5`, return `35`.

**解题思路**

> 动态规划。除了最上行和最左行，只有一种走法，其余行的走法等于左边格子走法与上边格子走法之和。初始化一个二维数组，值记录走法，因此推出公式：f\[i][j] = f\[i-1][j]+f\[i][j-1]

| 1    | 1    | 1    | 1    | 1    | 1    |
| ---- | ---- | ---- | ---- | ---- | ---- |
| 1    | 2    | 3    | 4    | 5    | 6    |
| 1    | 3    | 6    | 10   | 15   | 21   |
| 1    | 4    | 10   | 20   | 35   | 56   |



```java
public class Solution {
    /**
     * @param n, m: positive integer (1 <= n ,m <= 100)
     * @return an integer
     */
    public int uniquePaths(int m, int n) {
        // write your code here 
        int[][] f = new int[m][n];
        for(int i = 0; i < m; i++)
        {
            for(int j = 0; j < n; j++)
            {
                if(i == 0 || j == 0)
                    f[i][j] = 1;
                else
                    f[i][j] = f[i-1][j] + f[i][j-1];
            }
        }
        return f[m-1][n-1];
    }
}

```

> 一维数组作为额外空间存储值，每次遍历后覆盖上一次的值，直到遍历完毕，返回f\[n-1]

```java
public class Solution {
    /**
     * @param n, m: positive integer (1 <= n ,m <= 100)
     * @return an integer
     */
    public int uniquePaths(int m, int n) {
        // write your code here 
        int[] f = new int[n];
        for(int i = 0; i < m; i++)
            for(int j = 0; j < n; j++)
            {
                if(i == 0 || j == 0)
                    f[j] = 1;
                else
                    f[j] += f[j-1];
            }
        return f[n-1];
    }
}
```


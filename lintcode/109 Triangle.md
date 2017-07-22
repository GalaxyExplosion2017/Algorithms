## [109 Triangle](http://www.lintcode.com/en/problem/triangle/)

**Description**

Given a triangle, find the minimum path sum from top to bottom. Each step you may move to adjacent numbers on the row below.

> ##### \* Notice
>
> Bonus point if you are able to do this using only O(n) extra space, where n is the total number of rows in the triangle.

**Example**

Given the following triangle:

```
[
     [2],
    [3,4],
   [6,5,7],
  [4,1,8,3]
]

```

The minimum path sum from top to bottom is 11 (i.e., 2 + 3 + 5 + 1 = 11).

**解题思路 1**

> 动态规划。从倒数第二行开始，把每一行的元素改为其下一行能与之相加的两个数得到的和的最小值。

```java
public class Solution {
    /**
     * @param triangle: a list of lists of integers.
     * @return: An integer, minimum path sum.
     */
    public int minimumTotal(int[][] triangle) {
        // write your code here
         int row = triangle.length;
        //  if(row < 1){
        //      return 0;
        //  }
        //  if(row == 1){
        //      return triangle[0][0];
        //  }
         for(int i = row-2; i >= 0 ; i--)
             for(int j = 0; j <= i; j++)
                 triangle[i][j] += Math.min(triangle[i+1][j],triangle[i+1][j+1]);
         return triangle[0][0];
    }
}
```


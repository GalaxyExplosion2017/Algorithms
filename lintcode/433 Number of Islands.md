## [433 Number of Islands](http://www.lintcode.com/en/problem/number-of-islands/)

##### Description

Given a boolean 2D matrix, `0` is represented as the sea, `1` is represented as the island. If two 1 is adjacent, we consider them in the same island. We only consider up/down/left/right adjacent.

Find the number of islands.

##### Example

Given graph:

```
[
  [1, 1, 0, 0, 0],
  [0, 1, 0, 0, 1],
  [0, 0, 0, 1, 1],
  [0, 0, 0, 0, 0],
  [0, 0, 0, 0, 1]
]
```

return `3`

##### Solution

深度优先遍历，若当前`grid[i][j]`为`true`，则将其周围相邻数全部标记为`false`，用DfsExplore方法递归标记。

```java
public class Solution {
    /**
     * @param grid a boolean 2D matrix
     * @return an integer
     */
    public int numIslands(boolean[][] grid) {
        // Write your code here
        int count = 0;
        for(int i = 0; i < grid.length; i++){
            for(int j = 0; j < grid[0].length; j++){
                if(grid[i][j] == true){
                    count++;
                    DfsExplore(grid,i,j);
                }
            }
        }
        return count;
    }
    public void DfsExplore(boolean[][] grid , int i , int j){
        if(i < 0 || j < 0 || i >= grid.length || j >= grid[0].length || grid[i][j] == false) return;
        grid[i][j] = false;
        DfsExplore(grid,i+1,j);
        DfsExplore(grid,i-1,j);
        DfsExplore(grid,i,j+1);
        DfsExplore(grid,i,j-1);
    }
}
```


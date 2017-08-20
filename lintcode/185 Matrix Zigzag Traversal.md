## [185 Matrix Zigzag Traversal](http://www.lintcode.com/en/problem/matrix-zigzag-traversal/)

**Description**

Given a matrix of *m* x *n* elements (*m* rows, *n* columns), return all elements of the matrix in ZigZag-order.

**Example**

Given a matrix:

```
[
  [1, 2,  3,  4],
  [5, 6,  7,  8],
  [9,10, 11, 12]
]
```

return `[1, 2, 5, 9, 6, 3, 4, 7, 10, 11, 8, 12]`

#### Solution

Z字形走法，从左下到右上，到最上行后右移或者下移一位；再从右上到左下，到最左列下移或右移一位，直到遍历完所有数。其中两个while循环必须是**先走斜上的循环，再走斜下的循环**；两个while循环之后的平移操作，有着**严格的相对顺序**：**斜上之后的平移，先考虑右移，再考虑下移；斜下之后的平移，先考虑下移，再考虑右移。**

```java
public class Solution {
    /**
     * @param matrix: a matrix of integers
     * @return: an array of integers
     */ 
    public int[] printZMatrix(int[][] matrix) {
        // write your code here
        if(matrix == null || matrix.length == 0 || matrix[0].length == 0) 
            return null;
        int m = matrix.length , n = matrix[0].length;
        int[] result = new int[m*n];
        result[0] = matrix[0][0];
        int i = 1 , r = 0 , c = 0;
        while(i < m * n){
            while(r-1 >= 0 && c+1 < n) result[i++] = matrix[--r][++c];
            if(c+1 < n) result[i++] = matrix[r][++c];
            else if(r+1 < m) result[i++] = matrix[++r][c];
            while(r+1 < m && c-1 >= 0) result[i++] = matrix[++r][--c];
            if(r+1 < m) result[i++] = matrix[++r][c];
            else if(c+1 < n) result[i++] = matrix[r][++c];
        }
        return result;
    }
}
```


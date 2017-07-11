# 28 Search a 2D Matrix

**Description:**

Write an efficient algorithm that searches for a value in an *m* x *n* matrix.

This matrix has the following properties:

- Integers in each row are sorted from left to right.
- The first integer of each row is greater than the last integer of the previous row.

**Example:**

Consider the following matrix:

```
[
    [1, 3, 5, 7],
    [10, 11, 16, 20],
    [23, 30, 34, 50]
]

```

Given `target = 3`, return `true`.

**解题思路:**

> 二分查找，从中间开始寻找，比给定的数大则在左边继续二分查找，小则在右边继续二分查找

```java
public class Solution {
    /**
     * @param matrix, a list of lists of integers
     * @param target, an integer
     * @return a boolean, indicate whether matrix contains target
     */
    public boolean searchMatrix(int[][] matrix, int target) {
        // write your code here
        if(matrix==null||matrix.length==0)  return false;
        if(matrix[0]==null||matrix[0].length==0)  return false;
        int row = matrix.length, column = matrix[0].length;
        int start = 0, end = row * column - 1;       
        while (start <= end) {
            int mid =  (end + start) / 2;
            int number = matrix[mid / column][mid % column];
            if (number == target) {
                return true;
            } else if (number < target) {
                start = mid+1;
            } else {
                end = mid-1;
            }
        }       
        return false;
    }
}
```


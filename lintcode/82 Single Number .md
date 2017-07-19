# [**82 Single Number** ](http://www.lintcode.com/en/problem/single-number/)

**Description**

Given `2*n + 1` numbers, every numbers occurs twice except one, find it.

**Example**

Given `[1,2,2,1,3,4,3]`, return `4`

**解题思路**

> ^XOR位运算。

```java
public class Solution {
    /**
      *@param A : an integer array
      *return : a integer 
      */
    public int singleNumber(int[] A) {
        // Write your code here
        int result = 0;
        for(int i : A)
            result ^= i;
        return result;
    }
}
```


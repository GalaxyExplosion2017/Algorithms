# [60 Search Insert Position](http://www.lintcode.com/en/problem/search-insert-position/)

**Description**

Given a sorted array and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You may assume **NO** duplicates in the array.

**Example**

`[1,3,5,6]`, 5 → 2

`[1,3,5,6]`, 2 → 1

`[1,3,5,6]`, 7 → 4

`[1,3,5,6]`, 0 → 0

**解题思路**

> 二分查找

```java
public class Solution {
    /** 
     * param A : an integer sorted array
     * param target :  an integer to be inserted
     * return : an integer
     */
    public int searchInsert(int[] A, int target) {
        // write your code here
        if(A==null||A.length==0) return 0;
        int left=0;
        int right=A.length-1;
        while(left<=right)
        {
            int mid = (left+right)/2;
            if(A[mid]<target)
                left=mid+1;
            else if(A[mid]>target)
                right=mid-1;
            else
                return mid;
        }
        return left;
    }
}
```


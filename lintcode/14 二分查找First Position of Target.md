# 14 [二分查找First Position of Target](http://www.lintcode.com/en/problem/first-position-of-target/)

**Description:**

For a given sorted array (ascending order) and a `target` number, find the first index of this number in `O(log n)` time complexity.

If the target number does not exist in the array, return `-1`.

**Example**

If the array is `[1, 2, 3, 3, 4, 5, 10]`, for given target `3`, return `2`.

**解题思路：**

> 二分查找，保证目标值一定在nums[lo...hi]范围中，否则返回-1；若查找的值大于nums[i]则在右边继续查找，小于则在左边继续寻找，等于则使hi等于mid,直到lo=hi,返回lo;

```java
class Solution {
    /**
     * @param nums: The integer array.
     * @param target: Target to find.
     * @return: The first position of target. Position starts from 0.
     */
    public int binarySearch(int[] nums, int target) {
        //write your code here
        int lo=0;
        int hi=nums.length-1;
        while(lo<hi)
        {
            int mid = (lo+hi)/2;
            if(target>nums[mid])
                lo=mid+1;
            else if(target<nums[mid])
                hi=mid-1;
            else
                hi=mid;
        }
        if(target==nums[lo])
            return lo;
        return -1;
    }
}
```




## [539 Move Zeroes](http://www.lintcode.com/en/problem/move-zeroes/)

##### Description

Given an array `nums`, write a function to move all `0`'s to the end of it while maintaining the relative order of the non-zero elements.

##### ** Notice

1. You must do this **in-place** without making a copy of the array.
2. Minimize the total number of operations.

##### Example

Given `nums = [0, 1, 0, 3, 12]`, after calling your function, `nums` should be `[1, 3, 12, 0, 0]`.

##### Solution

将非负数从数组第一个位置开始依次赋值，然后将数组剩余索引都赋0

```java
public class Solution {
    /**
     * @param nums an integer array
     * @return nothing, do this in-place
     */
    public void moveZeroes(int[] nums) {
        // Write your code here
        if(nums == null || nums.length == 0)
            return ;
        int curr_pos = 0;
        for(int num : nums){
            if(num != 0){
                nums[curr_pos++] = num;
            }
        }
        while(curr_pos < nums.length){
            nums[curr_pos++] = 0; 
        }
    }
}
```


## [457 Classical Binary Search](http://www.lintcode.com/en/problem/classical-binary-search/)

##### Description

Find any position of a target number in a sorted array. Return -1 if target does not exist.

##### Example

Given `[1, 2, 2, 4, 5, 5]`. 

For target = `2`, return 1 or 2.

For target = `5`, return 4 or 5.

For target = `6`, return -1.

##### Solution

二分查找

```java
public class Solution {
    /**
     * @param nums: An integer array sorted in ascending order
     * @param target: An integer
     * @return an integer
     */
    public int findPosition(int[] nums, int target) {
        // Write your code here
        int lo = 0;
        int hi = nums.length-1;
        while(lo <= hi){
            int mid = (lo+hi)/2;
            if(nums[mid] < target) lo = mid+1;
            else if(nums[mid] > target) hi = mid-1;
            else return mid;
        }
        return -1;
    }
}
```


## [373 Partition Array by Odd and Even ](http://www.lintcode.com/en/problem/partition-array-by-odd-and-even/)

##### Description

Partition an integers array into odd number first and even number second.

**Example**

Given `[1, 2, 3, 4]`, return `[1, 3, 2, 4]`

##### Solution

将数组中左边的偶数和右边的奇数交换位置

```java
public class Solution {
    /**
     * @param nums: an array of integers
     * @return: nothing
     */
    public void partitionArray(int[] nums) {
        // write your code here;
       int left = 0;
       int right = nums.length-1;
       while(left < right){
           while(nums[left] % 2 == 1) left++;
           while(nums[right] % 2 == 0) right--;
           if(left < right){
               int temp = nums[left];
               nums[left] = nums[right];
               nums[right] = temp;
           }
       }return ;
    }
}
```


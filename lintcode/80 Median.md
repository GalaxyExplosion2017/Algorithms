# [80 Median](http://www.lintcode.com/en/problem/median/)

**Description**

Given a unsorted array with integers, find the median of it.

A median is the middle number of the array after it is sorted.

If there are even numbers in the array, return the `N/2`-th number after sorted.

**Example**

Given `[4, 5, 1, 2, 3]`, return `3`.

Given `[7, 9, 4, 5]`, return `5`.

**解题思路**

> 先快速排序把给定的整型数组排好顺序，然后返回数nums[(n-1)/2]。

```java
public class Solution {
    /**
     * @param nums: A list of integers.
     * @return: An integer denotes the middle number of the array.
     */
    public int median(int[] nums) {
        // write your code here
        quickSort(nums,0,nums.length-1);
        return nums[(nums.length-1)/2];
    }
    public void quickSort(int[] nums,int start,int end)
    {
        if(start>end) return ;
        int left = start;
        int right = end;
        int pivot = nums[start];
        while(left<=right)
        {
             while(right>=left&&nums[right]>pivot)
            {
                right--;
            }
            while(right>=left&&nums[left]<pivot)
            {
                left++;
            }
            if(left<=right)
            {
                int t = nums[right];
                nums[right] = nums[left];
                nums[left] = t;
                left++;
                right--;
            }
        }
        quickSort(nums,start,right);
        quickSort(nums,left,end);
    }
}
```


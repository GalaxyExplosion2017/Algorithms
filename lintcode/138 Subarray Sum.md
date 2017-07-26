## [138 Subarray Sum](http://www.lintcode.com/en/problem/subarray-sum/)

**Description**

Given an integer array, find a subarray where the sum of numbers is **zero**. Your code should return the index of the first number and the index of the last number.

##### ** Notice

There is at least one subarray that it's sum equals to zero.

**Example**

Given `[-3, 1, 2, -3, 4]`, return `[0, 2]` or `[1, 3]`
**解题思路**

> 用一个hashmap存储数组的每一位index之前的所有元素之和，初始存入(0,-1)。若有重复的sum出现(即sum为0)，说明之前的sum对应的下一位map.get(sum)+1到当前sum对应的第i个元素之间所有元素和为0，即为所求子序列。

```java
public class Solution {
    /**
     * @param nums: A list of integers
     * @return: A list of integers includes the index of the first number 
     *          and the index of the last number
     */
    public ArrayList<Integer> subarraySum(int[] nums) {
        // write your code here
        ArrayList<Integer> arr = new ArrayList<Integer>();
        HashMap<Integer,Integer> map = new HashMap<Integer,Integer>();
        map.put(0,-1);
        int sum = 0;
        for(int i = 0; i < nums.length; i++)
        {
            sum += nums[i];
            if(map.containsKey(sum))
            {
                arr.add(map.get(sum)+1);//get(0)+1
                arr.add(i);//2
                return arr;
            }else
                map.put(sum,i);
        }
        return arr;
    }
}
```


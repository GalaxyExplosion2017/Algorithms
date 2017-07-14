# 44 Minimum Subarray

**Description**

Given an array of integers, find the subarray with smallest sum.

Return the sum of the subarray.

> #####  Notice
>
> The subarray should contain one integer at least.

**Example**

For `[1, -1, -2, 1]`, return `-3`.

**解题思路 1**

> 贪心算法

```java
public class Solution {
    /**
     * @param nums: a list of integers
     * @return: A integer indicate the sum of minimum subarray
     */
    public int minSubArray(ArrayList<Integer> nums) {
        // write your code
        int sum = 0;
        int min = Integer.MAX_VALUE;
        for(int i=0;i<nums.size();i++)
        {
            sum+=nums.get(i);
            min=Math.min(sum,min);
            sum=Math.min(sum,0);
        }
        return min;
    }
}

```

**解题思路 2**

> 动态规划

```java
public class Solution {
    /**
     * @param nums: a list of integers
     * @return: A integer indicate the sum of minimum subarray
     */
    public int minSubArray(ArrayList<Integer> nums) {
        // write your code
        if(nums==null||nums.size()==0) return 0;
        int local=nums.get(0);
        int global=nums.get(0);
        for(int i=1;i<nums.size();i++)
        {
            local = Math.min(nums.get(i),local+nums.get(i));
            global = Math.min(local,global);
        }
        return global;
    }
}

```

**解题思路 3**

> 最大前缀和


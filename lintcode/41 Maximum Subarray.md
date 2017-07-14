# 41 Maximum Subarray

**Description**

Given an array of integers, find a contiguous subarray which has the largest sum.

**Notice**

> The subarray should contain at least one number.

**Example**

Given the array `[−2,2,−3,4,−1,2,1,−5,3]`, the contiguous subarray `[4,−1,2,1]` has the largest sum = `6`.

**解题思路 1**

> 贪心算法：先求局部和，赋给max，然后继续遍历加上后一个数得到新的局部和，拿来和max对比，大的值赋给max；局部和若小于0，则清0重新计算局部和，直到得出最大的max，返回max。

```java
public class Solution {
    /**
     * @param nums: A list of integers
     * @return: A integer indicate the sum of max subarray
     */
    public int maxSubArray(int[] nums) {
        // write your code
        if(nums==null||nums.length==0) return 0;
        int sum = 0;
        int max = Integer.MIN_VALUE;
        for(int i = 0;i<nums.length;i++)
        {
            sum += nums[i];
            max = Math.max(sum,max);
            sum = Math.max(sum,0);
        }
        return max;
    }
}
```

**解题思路 2**

> 动态规划：定义两个变量local,global，存储当前局部最优解和全局最优解。局部最优解必须包含当前元素，从第二个数开始，局部最优解动态规划递推式为：local = Math.max(A[i],local+A[i])，如果local为负数，不如丢掉直接用A[i];全局最优解可以不包含当元素，因此遍历每次的全局最优解为当前局部最优解与前一次全局最优解的最大，即global = Math.max(local,global); 最后返回global。

```java
public class Solution {
    /**
     * @param nums: A list of integers
     * @return: A integer indicate the sum of max subarray
     */
    public int maxSubArray(int[] nums) {
        // write your code
        if(nums==null||nums.length==0) return 0;
        int local = nums[0];
        int global = nums[0];
        for(int i = 1; i<nums.length;i++)
        {
            local = Math.max(nums[i],local+nums[i]);
            global = Math.max(local,global);
        }
        return global;
    }
}
```

**解题思路 3**

> 最小前缀和：定义三个变量sum、minSum、max,分别为遍历的数组和，最小前缀和，最大值。每遍历一次，求出和sum，然后最大值等于前一次的最大值与遍历后的和减去最小前缀和，即max=Math.max(max,sum-minSum)，最小前缀和等于遍历后的和与前一次最小前缀和的最小值，即minSum=Math.min(sum,minSum)。最后返回max。

```java
public class Solution {
    /**
     * @param nums: A list of integers
     * @return: A integer indicate the sum of max subarray
     */
    public int maxSubArray(int[] nums) {
        // write your code
        if(nums==null||nums.length==0) return 0;
        int sum = 0,minSum = 0,max = Integer.MIN_VALUE;
        for(int i=0;i<nums.length;i++)
        {
            sum+=nums[i];
            max=Math.max(max,sum-minSum);
            minSum=Math.min(sum,minSum);
        }
        return max;
    }
}
```


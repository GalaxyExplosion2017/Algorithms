## [111 Climbing Stairs](http://www.lintcode.com/en/problem/climbing-stairs/)

**Description**

You are climbing a stair case. It takes ***n*** steps to reach to the top.

Each time you can either climb ***1*** or ***2*** steps. In how many distinct ways can you climb to the top?

**Example**

Given an example n=3 , 1+1+1=2+1=1+2=3return 3

**解题思路**

> 动态规划。只有一层台阶时，只有1种解法s[1]=1；有两层台阶时，有两种解法s[2]=2；当超过三层台阶时，有两种走法：可以先走一步，后面就还剩两步，有两种走法s[2]=2，也可以先走两步，后面还剩一步，有一种走法s[1]=1。四层五层…类似，因此可以推出公式：s[n] = s[n-1] + s[n-2]，求出第n层的解s[n]。

```java
public class Solution {
    /**
     * @param n: An integer
     * @return: An integer
     */
    public int climbStairs(int n) {
        // write your code here
        if(n == 0) return 1;
        int[] dp = new int[n+1];
        dp[0] = 1;
        dp[1] = 1;
        for (int i = 2; i <= n; i++) dp[i] = dp[i-1] + dp[i-2];
        return dp[n];
    }
}
```


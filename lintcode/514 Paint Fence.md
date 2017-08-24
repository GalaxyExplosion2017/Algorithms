## [514 Paint Fence](http://www.lintcode.com/en/problem/paint-fence/)

##### Description

There is a fence with `n` posts, each post can be painted with one of the `k` colors.
You have to paint all the posts such that no more than two adjacent fence posts have the same color.
Return the total number of ways you can paint the fence.

##### ** Notice

`n` and `k` are non-negative integers.

##### Example

Given `n`=3, `k`=2 return 6

```
      post 1,   post 2, post 3
way1    0         0       1 
way2    0         1       0
way3    0         1       1
way4    1         0       0
way5    1         0       1
way6    1         1       0
```

##### Solution 1

动态规划。涂到第一根柱子又k种涂法，涂到第二根柱子有$k^2$种涂法，第三根柱子若跟第二根同色，则必跟第一根柱子不同色，有k-1种涂法；若跟第二根不同色，则第二根柱子和第一根柱子必同色，有k-1种涂法；则涂到第三根柱子有dp\[2]=(k-1)\*dp[1]+(k-1)\*dp\[0]种涂法；第四根柱子涂法对比第二根柱子和第三根柱子，解法类似第三根柱子，创建数组存储涂到第n个柱子的涂法，返回dp\[n-1]

```java
public class Solution {
    /*
     * @param n: non-negative integer, n posts
     * @param k: non-negative integer, k colors
     * @return: an integer, the total number of ways
     */
    public int numWays(int n, int k) {
        // write your code here
        if(n == 0) return 0;
        if(n == 1) return k;
        int[] dp = new int[n];
        dp[0] = k;
        dp[1] = k*k;
        for(int i = 2 ; i < n ; i++){
            dp[i]=(k-1)*dp[i-1]+(k-1)*dp[i-2];
        }
        return dp[n-1];
    }
}
```

##### Solution 2

解放同1，space:O(1)

```java
public class Solution {
    /*
     * @param n: non-negative integer, n posts
     * @param k: non-negative integer, k colors
     * @return: an integer, the total number of ways
     */
    public int numWays(int n, int k) {
        // write your code here
        if(n == 0) return 0;
        if(n == 1) return k;
        int one = k;
        int two = k*k;
        for(int i = 2 ; i < n ; i++){
            int cur = (k-1)*(one+two);
            one = two;
            two = cur;
        }
        return two;
    }
}
```


### [397 Longest Increasing Continuous Subsequence](http://www.lintcode.com/en/problem/longest-increasing-continuous-subsequence/)

##### Description

Give an integer array，find the longest increasing continuous subsequence in this array.

An increasing continuous subsequence:

- Can be from right to left or from left to right.
- Indices of the integers in the subsequence should be continuous.

##### ** Notice

O(n) time and O(1) extra space.

**Example**

For `[5, 4, 2, 1, 3]`, the LICS is `[5, 4, 2, 1]`, return `4`.

For `[5, 1, 2, 3, 4]`, the LICS is `[1, 2, 3, 4]`, return `4`.

##### Solution 1

贪心算法。创建变量max存储当前最大连续子序列长度，每次序列化顺序改变（up变为down或者反过来），则将原来的存储顺序变化的变量（countUp或者countDown）变为1，直到遍历完毕，返回max。

```java
public class Solution {
    /*
     * @param : An array of Integer
     * @return: an integer
     */
    public int longestIncreasingContinuousSubsequence(int[] A) {
        // write your code here
        if(A == null || A.length == 0) return 0;
        if(A.length == 1) return 1;
        int countUp = 1;
        int countDown =1;
        int max = 0;
        for(int i = 0; i < A.length-1; i++){
            if(A[i]<A[i+1]){
                countDown = 1;
                countUp++;
                max = Math.max(max,countUp);
            }else{
                countUp = 1;
                countDown++;
                max = Math.max(max,countDown);
            }
        }
        return max;
    }
};
```

##### Solution 2

动态规划。创建一个临时数组存储连续顺势最大长度，若是连续顺序，记为前一位置+1，将不连续的位置记为1，然后把max与当前位置比较，大的值赋给max，直到遍历完毕，返回max。

```java
public class Solution {
    /*
     * @param : An array of Integer
     * @return: an integer
     */
    public int longestIncreasingContinuousSubsequence(int[] A) {
        // write your code here
        if(A == null || A.length == 0) return 0;
        if(A.length == 1) return 1;
        int n = A.length;
        int max = 0;
        int[] f = new int[n+1];
        f[0] = 1;
        for(int i = 1; i < A.length; i++){
            f[i] = A[i] > A[i-1] ? f[i-1]+1 : 1;
            max = Math.max(max,f[i]);
        }
        for(int i = 1; i < A.length; i++){
            f[i] = A[i] < A[i-1] ? f[i-1]+1 : 1;
            max = Math.max(max,f[i]);
        }
        return max;
    }
};
```






## [488 Happy Number](http://www.lintcode.com/en/problem/happy-number/)

##### Description

Write an algorithm to determine if a number is *happy*.

A happy number is a number defined by the following process: Starting with any positive integer, replace the number by the sum of the squares of its digits, and repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1. Those numbers for which this process ends in 1 are happy numbers.

**Example**

19 is a happy number

```
1^2 + 9^2 = 82
8^2 + 2^2 = 68
6^2 + 8^2 = 100
1^2 + 0^2 + 0^2 = 1
```

##### Solution

当n不等于1时，对给定的n进行拆分平方和处理，创建一个HashSet将每次处理后的值放入其中，如果HashSet中含有次数，则返回false，否则一直处理下去，直到n等于1，则跳出当前循环，返回True。

```java
public class Solution {
    /*
     * @param n: An integer
     * @return: true if this is a happy number or false
     */
    public boolean isHappy(int n) {
        // write your code here
        Set<Integer> set = new HashSet<Integer>();
        while(n != 1){
            int sum = 0;
            while(n > 0){
                sum += (n % 10) * (n % 10);
                n /= 10;
            }
            if(set.contains(sum))
                return false;
            else
                set.add(sum);
            n = sum;
        }
        return true;
    }
   
}
```


# 2 Trailing Zeros 

> 求n的阶乘中末尾有多少个0，就是求n!中能被5整除的数的个数+能被5次方整除的个数

```java
class Solution {
    /*
     * param n: As desciption
     * return: An integer, denote the number of trailing zeros in n!
     */
    public long trailingZeros(long n) {
        // write your code here
        long sum=0;
        while(n!=0)
        {
            sum+=n/5;
            n/=5;;
        }
        return sum ;
        
    }
};

```


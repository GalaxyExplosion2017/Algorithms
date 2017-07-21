## [413 Reverse Integer](http://www.lintcode.com/en/problem/reverse-integer/)

**Description**

Reverse digits of an integer. Returns 0 when the reversed integer overflows (signed 32-bit integer).

**Example**

Given `x = 123`, return `321`

Given `x = -123`, return `-321`

**解题思路 1**

> 创建变量result储存当前结果，temp为当前零时变量，若当前数n不为0时，不停的求余10并且除以10，得到尾数tail，然后temp = 10*result+tail，将temp的值赋给result，若值溢出(temp/10!=result)，则返回0，直到当前数n等于0，则返回result。

```java
public class Solution {
    /**
     * @param n the integer to be reversed
     * @return the reversed integer
     */
    public int reverseInteger(int n) {
        // Write your code here
        int result = 0;
        int temp = 0;
        while(n != 0)
        {
            int tail = n % 10;
            n /= 10;
            temp = 10*result+tail;
            if(temp/10 != result)
                return 0;
            result = temp;
        }
        return result;
    }
}
```


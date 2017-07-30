## [** 181 Flip Bits](http://www.lintcode.com/en/problem/flip-bits/)

**Description**

Determine the number of bits required to flip if you want to convert integer *n* to integer *m*.

##### ** Notice

Both *n* and *m* are 32-bit integers.

**Example**

Given *n* = `31` (11111), *m* = `14` (01110), return `2`.

##### Solution 1

先a异或b得到c，然后当c !=0时，c的最后一位与1与运算，为1则计数count自增1，直到c = 0，返回count。

```java
class Solution {
    /**
     *@param a, b: Two integer
     *return: An integer
     */
    public static int bitSwapRequired(int a, int b) {
        // write your code here
        int count = 0;
        for(int c = a ^ b; c != 0; c = c >>> 1)
            count += c & 1;
        return count;
    }
};
```

##### Solution 2

将a 与 b异或，得到c，若c是负数，则与MIN_VALUE异或把符号位去掉，count++，然后再把去掉符号位后的c不停的mod2，得到1则count++，然后除以2，直到c为0，返回count。

```java
class Solution {
    /**
     *@param a, b: Two integer
     *return: An integer
     */
    public static int bitSwapRequired(int a, int b) {
        // write your code here
        int c = a ^ b;
        int count = 0;
        if(c < 0){
            c ^= Integer.MIN_VALUE;
            count++;
        }
        while(c != 0){
            count += c % 2;
            c /= 2;
        }
        return count;
    }
};
```


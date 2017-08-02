## [365 Count 1 in Binary](http://www.lintcode.com/en/problem/count-1-in-binary/)

##### Description

Count how many `1` in binary representation of a 32-bit integer.

**Example**

Given `32`, return `1`Given `5`, return `2`Given `1023`, return `9`

##### Solution

定义一个记录1的变量count，如果给定的数是负数，先把它与最小的数（Integer.MIN_VALUE)异或，count+1，然后再把它mod2之后，若等于1则count+1，然后num /=2，直到num为0.

```java
public class Solution {
    /**
     * @param num: an integer
     * @return: an integer, the number of ones in num
     */
    public int countOnes(int num) {
        // write your code here
        int count = 0;
        if(num < 0){
            num ^=Integer.MIN_VALUE;
            count++;
        }  
        while(num != 0){
            if(num % 2 == 1) count++;
            num /= 2;
        }
        return count;
    }
};
```


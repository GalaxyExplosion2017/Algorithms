## [142 O(1) Check Power of 2](http://www.lintcode.com/en/problem/o1-check-power-of-2/)

**Description**

Using O(*1*) time to check whether an integer *n* is a power of `2`.

**Example**

For `n=4`, return `true`;For `n=5`, return `false`;

**解题思路**

> 若n是2的幂次，则它满足：1.大于0；2.n&(n-1)==0

```java
class Solution {
    /*
     * @param n: An integer
     * @return: True or false
     */
    public boolean checkPowerOf2(int n) {
        // write your code here
        return n>0 && (n&(n-1))==0;
    }
};
```


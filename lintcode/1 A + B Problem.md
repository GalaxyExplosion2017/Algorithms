# 1 A + B Problem 

> a+b = a^b+a&b<<1

```java
class Solution {
    /*
     * param a: The first integer
     * param b: The second integer
     * return: The sum of a and b
     */
    public int aplusb(int a, int b) {
        // write your code here, try to do it without arithmetic operators.
        while(b != 0){
            int _a = a^b;
            int _b = (a&b)<<1;
            a = _a;
            b = _b;
        }
        return a;
    }
};
```
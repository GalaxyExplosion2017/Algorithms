## [491 Palindrome Number](http://www.lintcode.com/en/problem/palindrome-number/)

##### Description

Check a positive number is a palindrome or not.

A palindrome number is that if you reverse the whole number you will get exactly the same number.

##### ** Notice

It's guaranteed the input number is a 32-bit integer, but after reversion, the number may exceed the 32-bit integer.

##### Example

`11`, `121`, `1`, `12321` are palindrome numbers.

`23`, `32`, `1232` are not palindrome numbers.

##### Solution

创建变量h，记录给定的数求最高位的10的倍数，然后用o作为存储给定的数，当o大于0时，取两头的数进行比较，若不想等返回false，直到跳出循环，返回true

```java
public class Solution {
    /*
     * @param num: a positive number
     * @return: true if it's a palindrome or false
     */
    public boolean isPalindrome(int num) {
        // write your code here
        if(num < 0)
            return false;
        int o = num;
        int h = 1;
        while(num / h >=10){
            h *= 10;
        }
        while(o > 0){
            if(o / h != o % 10)
                return false;
            o %= h;
            o /= 10;
            h /= 100;
        }
        return true;
    }
}
```


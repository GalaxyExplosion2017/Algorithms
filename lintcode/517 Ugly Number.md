## [517 Ugly Number](http://www.lintcode.com/en/problem/ugly-number/)

##### Description

Write a program to check whether a given number is an `ugly` number`.

`Ugly numbers` are positive numbers whose prime factors only include `2`, `3`, `5`. For example, `6`, `8` are ugly while `14` is not ugly since it includes another prime factor `7`.

##### ** Notice

Note that `1` is typically treated as an ugly number.

##### Example

Given num = `8` return `true`
Given num = `14` return `false`

##### Solution 1

创建一个包含元素2，3，5的数组，遍历数组，当num能被当前元素整除并且num大于0时，num除以当前元素，直到遍历完毕，返回num==1

```java
public class Solution {
    /*
     * @param num: An integer
     * @return: true if num is an ugly number or false
     */
    public boolean isUgly(int num) {
        // write your code here
        int[] div = {2,3,5};
        for(int i : div)
            while(num % i == 0 && num >0)
                num /= i;
        return num == 1;
    }
}
```

##### Solution 2

for循环2到5之间的数，若num能被当前数整出，num除以当前数，直到循环完毕，返回num == 1

```java
public class Solution {
    /*
     * @param num: An integer
     * @return: true if num is an ugly number or false
     */
    public boolean isUgly(int num) {
        // write your code here
        for(int i = 2 ; i < 6 && num > 0 ; i++)
            while(num % i == 0)
                num /= i;
        return num == 1;
    }
}
```


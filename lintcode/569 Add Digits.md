## [569 Add Digits](http://www.lintcode.com/en/problem/add-digits)

##### Description

Given a non-negative integer `num`, repeatedly add all its digits until the result has only one digit.

##### Example

Given `num` = 38.
The process is like: `3 + 8 = 11`, `1 + 1` = `2`. Since `2` has only one digit, return `2`.

##### Solution 1

逐位相加直到小于10

```java
public class Solution {
    /**
     * @param num a non-negative integer
     * @return one digit
     */
    public int addDigits(int num) {
        // Write your code here
        while(num >= 10){
            num = num / 10 + num % 10;
        }
        return num;
    }
}
```

##### Soluton 2

数学归纳法规律 

```java
public class Solution {
    /**
     * @param num a non-negative integer
     * @return one digit
     */
    public int addDigits(int num) {
        // Write your code here
        return 1+(num-1)%9;
    }
}
```



​                            
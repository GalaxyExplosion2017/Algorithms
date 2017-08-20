## [408 Add Binary](http://www.lintcode.com/en/problem/add-binary/)

##### Description

Given two binary strings, return their sum (also a binary string).

**Example**

a = `11`b = `1` Return `100`

##### Solution

定义一个字符串c来拼接每一次的结果，定义变量carry来存储进位权值，遍历给定的字符串a,b，每次求和后和c拼接，并且进位权值赋给carry，直到遍历完a,b所有的字符，若carry =1,则将1拼接在c前面，最后返回c。

```java
public class Solution {
    /**
     * @param a a number
     * @param b a number
     * @return the result
     */
    public String addBinary(String a, String b) {
        // Write your code here
        String c = "";
        int m = a.length()-1;
        int n = b.length()-1;
        int carry = 0;
        while(m >= 0 || n >= 0){
            int sum = carry;
            sum += (m >= 0) ? a.charAt(m)-'0' : 0;
            sum += (n >= 0) ? b.charAt(n)-'0' : 0;
            c = sum % 2 + c;
            carry = sum /2;
            m--;
            n--;
        }
        if(carry == 1){
            c = carry + c;
        }
        return c;
    }
}
```


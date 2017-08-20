## [407 Plus One](http://www.lintcode.com/en/problem/plus-one/)

##### Description

Given a non-negative number represented as an array of digits, plus one to the number.

The digits are stored such that the most significant digit is at the head of the list.

**Example**

Given `[1,2,3]` which represents 123, return `[1,2,4]`.Given `[9,9,9]` which represents 999, return `[1,0,0,0]`.

##### Solution

先求出最后一位数，用变量carry保存进位权值，然后从倒数第二个数开始往前便利，每个数等于当前数加上carry然后mod10，进位权值carry等于改变后的数除以10，到遍历完毕若carry=0则返回当前数组，若等于1则创建一个比给定数组长度大于1的新数组，数组的第一位是1，其余位跟给定数组变化后的值一样，然后返回这个数组。

```java
public class Solution {
    /**
     * @param digits a number represented as an array of digits
     * @return the result
     */
    public int[] plusOne(int[] digits) {
        // Write your code here
        int carry = (digits[digits.length-1]+1)/10;
        digits[digits.length-1] = (digits[digits.length-1]+1) % 10;
        for(int i = digits.length-2; i >= 0; i--){
            int cur = digits[i] + carry;
            carry = cur/10;
            digits[i] = cur % 10;
        }
        if(carry == 1){
            int[] res = new int[digits.length+1];
            res[0] = 1;
            for(int i = 1; i < res.length; i++){
                res[i] = digits[i-1];
            }
            return res;
        }
        return digits;
    }
}
```


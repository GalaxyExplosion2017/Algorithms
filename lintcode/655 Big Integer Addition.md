## [655 Big Integer Addition](http://www.lintcode.com/en/problem/big-integer-addition/)

##### Description

Given two non-negative integers `num1` and `num2`represented as string, return the sum of `num1` and `num2`.

##### ** Notice

- The length of both num1 and num2 is < 5100.
- Both num1 and num2 contains only digits 0-9.
- Both num1 and num2 does not contain any leading zero.
- You must not use any built-in BigInteger library or convert the inputs to integer directly.

##### Example

Given num1 = `"123"`, num2 = `"45"`
return `"168"`

##### Solution

创建一个数组，把每一位数相加存到数组中，最后字符串拼接

```java
public class Solution {
    /*
     * @param num1: a non-negative integers
     * @param num2: a non-negative integers
     * @return: return sum of num1 and num2
     */
    public String addStrings(String num1, String num2) {
        // write your code here
        if(num1.equals("0")){
            return num2;
        }
        if(num2.equals("0")){
            return num1;
        }
        int len1 = num1.length();
        int len2 = num2.length();
        int len = Math.max(len1,len2);
        char[] result = new char[len+1];
        for(int k = 0; k < len+1; k++){
            result[k] = '0';
        }
        int carry = 0;
        int n1 = 0;
        int n2 = 0;
        for(int i = 0;i < len+1; i++){
            if(i < len1){
                n1 = num1.charAt(len1 - 1 - i) - '0';
            }else{
                n1 = 0;
            }
            
            if(i < len2){
                n2 = num2.charAt(len2 - 1 - i) - '0';
            }else{
                n2 = 0;
            }
            int temp = n1 + n2 +carry;
            result[len-i] = (char)(temp % 10 + '0');
            carry = temp / 10;
        }
        
        int count = 0;  
        for(;count<len + 1;count++){  
            if(result[count] != '0'){  
                break;  
            }  
        }
        
        String res = "";  
        for(int i = count;i<len + 1;i++){  
            res += result[i];  
        }  
        return res;
    }
}
```


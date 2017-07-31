## [212 Space Replacement](http://www.lintcode.com/en/problem/space-replacement/)

**Description**

Write a method to replace all spaces in a string with `%20`. The string is given in a characters array, you can assume it has enough space for replacement and you are given the true length of the string.

You code should also return the new length of the string after replacement.

##### ** Notice

If you are using Java or Python，please use characters array instead of string.

**Example**

Given `"Mr John Smith"`, length = `13`.The string after replacement should be `"Mr%20John%20Smith"`, you need to change the string in-place and return the new length `17`.

#### Solution

先遍历一次数组，找到原来数组中有多少个空格，得出新的长度，再把数组按照新的长度，把原长度数组中的空格换成 ` %20`，最后返回新长度。

```java
public class Solution {
    /*
     * @param string: An array of Char
     * @param length: The true length of the string
     * @return: The true length of new string
     */
    public int replaceBlank(char[] string, int length) {
        // write your code here
        if(string == null ||length == 0) return 0;
        int count = 0;
        int len = length;
        for(char c : string)
            if(c == ' ') 
                count++;
        len += 2*count;
        int j = 1;
        for(int i = length-1; i >= 0; i--){
            if(string[i] == ' '){
                string[len-j++] ='0';
                string[len-j++] ='2';
                string[len-j++] ='%';
            }else string[len-j++] = string[i];
        }
        return len;
    }
};
```


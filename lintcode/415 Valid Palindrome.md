### [415 Valid Palindrome](http://www.lintcode.com/en/problem/valid-palindrome/)

##### Description

Given a string, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.

##### ** Notice

Have you consider that the string might be empty? This is a good question to ask during an interview.

For the purpose of this problem, we define empty string as valid palindrome.

**Example**

`"A man, a plan, a canal: Panama"` is a palindrome.

`"race a car"` is not a palindrome.

##### Solution

先把字符串全部变为小写，然后用字符串两端开始相向遍历，若不是字符或者数字，则前进，当两边的两个字符不相等时，则返回false，若遍历完，则返回true。

```java
public class Solution {
    /**
     * @param s A string
     * @return Whether the string is a valid palindrome
     */
    public boolean isPalindrome(String s) {
        // Write your code here
        if(s == null || s.length() < 2){
            return true;   
        } 
        s = s.toLowerCase();
        int start = 0;
        int end = s.length() - 1;
        while(start < end){
            if(!Character.isLetterOrDigit(s.charAt(start))){
                start++;
                continue;
            }
            if(!Character.isLetterOrDigit(s.charAt(end))){
                end--;
                continue;
            }
            if(s.charAt(start) != s.charAt(end)){
                return false;
            }
            start++;
            end--;
        }
        return true;
    }
}
```


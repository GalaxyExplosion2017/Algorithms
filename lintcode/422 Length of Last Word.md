## [422 Length of Last Word](http://www.lintcode.com/en/problem/length-of-last-word/)

##### Description

Given a string s consists of upper/lower-case alphabets and empty space characters `' '`, return the length of last word in the string.

If the last word does not exist, return `0`. 

##### Notice

A word is defined as a character sequence consists of non-space characters only.

##### Example

Given s = `"Hello World"`, return `5`.

##### Solution

从给定的字符最后一个位置开始向前遍历，到空格位置就是最后一个单词的长度` ' '`，输出这个长度

```java
public class Solution {
    /**
     * @param s A string
     * @return the length of last word
     */
    public int lengthOfLastWord(String s) {
        // Write your code here
        //return s.trim().length()-s.trim().lastIndexOf(" ")-1;
        int len=s.length(), lastLength=0;
        while(len > 0 && s.charAt(len-1)==' '){
            len--;
        }
        while(len > 0 && s.charAt(len-1)!=' '){
            lastLength++;
            len--;
        }
        return lastLength;
    }
}
```


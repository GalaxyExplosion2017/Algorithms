## [627 Longest Palindrome](http://www.lintcode.com/en/problem/longest-palindrome/)

##### Description

Given a string which consists of lowercase or uppercase letters, find the length of the longest palindromes that can be built with those letters.

This is case sensitive, for example `"Aa"` is not considered a palindrome here.

##### ** Notice

Assume the length of given string will not exceed `1010`.

##### Example

Given s = `"abccccdd"` return `7`

One longest palindrome that can be built is `"dccaccd"`, whose length is `7`.

##### Solution

创建一个HashSet，遍历给定字符串中的每一个字符，如果HashSet中不存在当前字符，则加入当前字符；若存在，则移除字符，计数count++，直到遍历完毕，若HashSet不为空，则返回count\*2+1，若为空，则返回count\*2。

```java
public class Solution {
    /**
     * @param s a string which consists of lowercase or uppercase letters
     * @return the length of the longest palindromes that can be built
     */
    public int longestPalindrome(String s) {
        // Write your code here
        HashSet<Character> set = new HashSet<>();
        int count = 0;
        for(char c : s.toCharArray()){
            if(!set.contains(c)){
                set.add(c);
            }else{
                set.remove(c);
                count++;
            }
        }
        if(set.isEmpty()){
            return count*2;
        }else{
            return count*2+1;
        }
    }
}
```


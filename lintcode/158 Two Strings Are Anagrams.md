## [158 Two Strings Are Anagrams](http://www.lintcode.com/en/problem/two-strings-are-anagrams/)

**Description**

Write a method `anagram(s,t)` to decide if two strings are anagrams or not.

**Clarification**

What is **Anagram**?
\- Two strings are anagram if they can be the same after change the order of characters.

**Example**

Given s = `"abcd"`, t = `"dcab"`, return `true`.
Given s = `"ab"`, t = `"ab"`, return `true`.
Given s = `"ab"`, t = `"ac"`, return `false`.

**解题思路 1**

> 创建一个数组，记录数组s中每个元素出现的次数，然后再遍历数组t中每个元素，减去每个元素出现的次数，若有元素的值小于0，则返回false；其它情况下返回True。

```java
public class Solution {
    /**
     * @param s: The first string
     * @param b: The second string
     * @return true or false
     */
    public boolean anagram(String s, String t) {
        // write your code here
        int[] counts = new int[256];
        for(int i = 0; i < s.length(); i++)
            counts[s.charAt(i)]++;
        for(int i = 0; i < t.length(); i++)
        {
            counts[t.charAt(i)]--;
            if(counts[t.charAt(i)]<0) return false;
        }
        return true;
    }
}
```

**解题思路 2**

> 利用字符数组的排序方法

```java
public class Solution {
    /**
     * @param s: The first string
     * @param b: The second string
     * @return true or false
     */
    public boolean anagram(String s, String t) {
        // write your code here
        char[] schar = s.toCharArray();
        char[] tchar = t.toCharArray();
        Arrays.sort(schar);
        Arrays.sort(tchar);
        return String.valueOf(schar).equals(String.valueOf(tchar));
    }
}
```


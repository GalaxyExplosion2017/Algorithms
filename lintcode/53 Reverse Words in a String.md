# 53 Reverse Words in a String 

**Description**

Given an input string, reverse the string word by word.

For example,
Given s = "`the sky is blue`",
return "`blue is sky the`".

**Clarification**

- What constitutes a word?
  A sequence of non-space characters constitutes a word.
- Could the input string contain leading or trailing spaces?
  Yes. However, your reversed string should not contain leading or trailing spaces.
- How about multiple spaces between two words?
  Reduce them to a single space in the reversed string.

**解题思路**

> 将字符串划分成字符数组，然后遍历字符数组，将字符数组中的元素逆序组合到新字符串上，直到遍历结束，返回新字符串

```java
public class Solution {
    /**
     * @param s : A string
     * @return : A string
     */
    public String reverseWords(String s) {
        // write your code
        String[] arr = s.split(" ");
        String str = "";
        for(int i=arr.length-1;i>=0;i--)
        {                
                str+=arr[i]+" ";             
        }
        return str.length() == 0 ? "" : str.substring(0, str.length() - 1);
    }
}
```


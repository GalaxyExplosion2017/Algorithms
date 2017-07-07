# 13 [字符串查找|strStr](http://www.lintcode.com/en/problem/strstr/)

 **Description:**

> For a given source string and a target string, you should output the **first** index(from 0) of target string in source string.
>
> If target does not exist in source, just return `-1`.

**Example:**

> If source = `"source"` and target = `"target"`, return `-1`.
>
> If source = `"abcdabcdefg"` and target = `"bcd"`, return `1`.

**解题思路：**

> 暴力查找法：在源字符串中查找目标字符串中第一个字符的位置，然后依次连续对比每一个字符，如果对比完连续的字符长度和目标字符串长度相同，则返回源字符串中出现的第一个是字符的索引。

```java
class Solution {
    /**
     * Returns a index to the first occurrence of target in source,
     * or -1  if target is not part of source.
     * @param source string to be scanned.
     * @param target string containing the sequence of characters to match.
     */
    public int strStr(String source, String target) {
        // write your code here
        if(source==null||target==null) return -1;
        int s = source.length();
        int t = target.length();
        for(int i=0;i<=s-t;i++)
        {
            int j;
            for(j=0;j<t;j++)
                if(source.charAt(i+j) !=target.charAt(j))
                    break;
            if(j==t) return i;
        }
        return -1;
    }
}
```


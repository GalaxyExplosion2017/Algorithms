## [157 Unique Characters](http://www.lintcode.com/en/problem/unique-characters/#)

**Description**

Implement an algorithm to determine if a string has all unique characters.

**Example**

Given `"abc"`, return `true`.

Given `"aab"`, return `false`.

**解题思路**

创建一个HashSet（元素不能相同），遍历字符串中的每一个字符，添加到HashSet中，如果添加不进去(HashSet中含有此元素)，则说明字符不是唯一的，返回false；若遍历完字符全部添加进去了，则返回True。

```java
public class Solution {
    /**
     * @param str: a string
     * @return: a boolean
     */
    public boolean isUnique(String str) {
        // write your code here
        Set<Character> set = new HashSet<Character>();
        for(int i = 0; i < str.length(); i++)
        {
            if(set.contains(str.charAt(i)))
                return false;
            set.add(str.charAt(i));
        }
        return true;
    }
}
```


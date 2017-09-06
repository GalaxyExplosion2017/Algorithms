## [647 Substring Anagrams](http://www.lintcode.com/en/problem/substring-anagrams/)

##### Description

Given a string `s` and a **non-empty** string `p`, find all the start indices of `p`'s anagrams in `s`.

Strings consists of lowercase English letters only and the length of both strings **s** and **p** will not be larger than 40,000.

The order of output does not matter.

##### Example

Given s = `"cbaebabacd"` p = `"abc"`

return `[0, 6]`

```
The substring with start index = 0 is "cba", which is an anagram of "abc".
The substring with start index = 6 is "bac", which is an anagram of "abc".
```

##### Solution

创建一个数组，将p中的字符存入数组中，然后遍历给定的字符串，若遍历完p中的字符，若符合前三个字符，将第一个字符索引加入list中，知道遍历完毕，返回list

```java
public class Solution {
    /*
     * @param s: a string
     * @param p: a string
     * @return: a list of index
     */
    public List<Integer> findAnagrams(String s, String p) {
        // write your code here
        List<Integer> list = new ArrayList<>();
        if(s == null || s.length() == 0 || p == null || p.length() == 0){
            return list;
        }
        int[] hash = new int[256];
        for(char c : p.toCharArray()){
            hash[c]++;
        }
        int left = 0, right = 0, count = p.length();
        while(right < s.length()){
            if(hash[s.charAt(right++)]-- >= 1){
                count--;
            }
            if(count == 0){
                list.add(left);
            }
            if(right-left == p.length() && hash[s.charAt(left++)]++ >= 0){
                count++;
            }
        }
        return list;
    }
}
```


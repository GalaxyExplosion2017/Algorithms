## [638 Strings Homomorphism](http://www.lintcode.com/en/problem/strings-homomorphism/)

##### Description

Given two strings **s** and **t**, determine if they are isomorphic.

Two strings are isomorphic if the characters in s can be replaced to get t.

All occurrences of a character must be replaced with another character while preserving the order of characters. No two characters may map to the same character but a character may map to itself.

##### ** Notice

You may assume both s and t have the `same length`.

##### Example

Given s = `"egg"`, t = `"add"`, return `true`.

Given s = `"foo"`, t = `"bar"`, return `false`.

Given s = `"paper"`, t = `"title"`, return `true`.

##### Solution

创建一个HashMap类型的record，和HashSet类型的repeat，分别记录给定字符串s和t对应的映射和已经确定的值的记录，同时遍历s和t，若键record中不存在，但值中缺存在，则返回false，否则将键值对\<s.chatAt(i)，t.charAt(i)>加入到record中，将t.charAt(i)加入repeat中;若键中存在，则取它的值与t.charAt(i)进行比较，若不相等返回false，直到遍历完毕，返回True。

```java
public class Solution {
    /**
     * @param s a string
     * @param t a string
     * @return true if the characters in s can be replaced to get t or false
     */
    public boolean isIsomorphic(String s, String t) {
        // Write your code here
        HashMap<Character,Character> record = new HashMap<>();
        HashSet<Character> repeat = new HashSet<>();
        for(int i = 0; i < s.length(); i++){
            if(!record.containsKey(s.charAt(i))){
                if(repeat.contains(t.charAt(i))){
                    return false;
                }
                record.put(s.charAt(i),t.charAt(i));
                repeat.add(t.charAt(i));
            }else{
                if(record.get(s.charAt(i)) != t.charAt(i)){
                    return false;
                }
            }
        }return true;
        
    }
}
```


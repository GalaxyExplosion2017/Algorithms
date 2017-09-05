[646 First Position Unique Character]

##### Description

Given a string, find the first non-repeating character in it and return it's index. If it doesn't exist, return `-1`.

#####Example

Given s = `"lintcode"`, return `0`.

Given s = `"lovelintcode"`, return `2`.

##### Solution

创建一个HashMap，遍历给定的String中的每一个字符，如果map中不存在当前字符，则以键为当前元素，值为1加入map中；如果存在则值加1。然后遍历map，当值为1时，输出当前键在字符串中的索引

```java
public class Solution {
    /*
     * @param s: a string
     * @return: it's index
     */
    public int firstUniqChar(String s) {
        // write your code here
        HashMap<Character,Integer> map = new HashMap<>();
        for(char c : s.toCharArray()){
            if(map.containsKey(c)){
                map.put(c,map.get(c)+1);
            }else{
                map.put(c,1);
            }
        }
        for(int i = 0; i < s.length(); i++){
            if(map.get(s.charAt(i)) == 1){
                return i;
            }
        }return -1;
    }
}
```


## [**133 Longest Words**](http://www.lintcode.com/en/problem/longest-words)

**Description**

Given a dictionary, find all of the longest words in the dictionary.

**Example**

Given

```
{
  "dog",
  "google",
  "facebook",
  "internationalization",
  "blabla"
}

```

the longest words are(is) `["internationalization"]`.

Given

```
{
  "like",
  "love",
  "hate",
  "yes"
}
```

the longest words are `["like", "love", "hate"]`.

**解题思路**

> 创建一个链表arr，遍历给予的词组，若当前链表为空或者当前单词比链表内第一个单词长，则将链表清空，将当前词组加入链表；若当前单词长度与链表内第一个单词长度相等，加入链表中；其他情况，则继续遍历词组，直到遍历完毕，返回链表arr。

```java
class Solution {
    /**
     * @param dictionary: an array of strings
     * @return: an arraylist of strings
     */
    ArrayList<String> longestWords(String[] dictionary) {
        // write your code here
        ArrayList<String> arr = new ArrayList<String>();
        for(String words : dictionary)
        {
            if(arr.isEmpty() || words.length()>arr.get(0).length())
            {
                arr.clear();
                arr.add(words);
            }else if(words.length() == arr.get(0).length())
                arr.add(words);
            else
                continue;
        }
        return arr;
    }
};
```


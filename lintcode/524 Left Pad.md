## [524 Left Pad](http://www.lintcode.com/en/problem/left-pad/)

##### Description

You know what, left pad is javascript package and referenced by React: 
[Github link](https://github.com/azer/left-pad)

One day his author unpublished it, then a lot of javascript projects in the world broken.

You can see from github it's only 11 lines.

You job is to implement the left pad function. If you do not know what left pad does, see examples below and guess.

##### Example

```
leftpad("foo", 5)
>> "  foo"

leftpad("foobar", 6)
>> "foobar"

leftpad("1", 2, "0")
>> "01"
```

##### Solution

创建一个StringBuffer类型的sb，将数组前面给定长度减去字符串长度的位置追加padChar，然后再把追加给定的字符串，返回sb。

```java
public class StringUtils {
    /**
     * @param originalStr the string we want to append to with spaces
     * @param size the target length of the string
     * @return a string
     */
    static public String leftPad(String originalStr, int size) {
        // Write your code here
        return leftPad(originalStr, size, ' ');
    }

    /**
     * @param originalStr the string we want to append to
     * @param size the target length of the string
     * @param padChar the character to pad to the left side of the string
     * @return a string
     */
    static public String leftPad(String originalStr, int size, char padChar) {
        // Write your code here
        StringBuffer sb = new StringBuffer();
        for(int i = 0; i < size - originalStr.length(); i++){
            sb.append(padChar);
        }
        sb.append(originalStr);
        return sb.toString();
    }
}
```


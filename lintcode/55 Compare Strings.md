# 55 Compare Strings 

**Description**

Compare two strings A and B, determine whether A contains all of the characters in B.

The characters in string A and B are all **Upper Case** letters.

> #####  Notice
>
> The characters of B in A are not necessary continuous or ordered.

**解题思路**

> 英文字母有26个，因此创建一个26个元素的数组counts，先遍历字符串A中的所有字符，每遍历一个把字符个数赋值给counts中的对应元素，再遍历字符串B中的所有字符，把出现的次数在相应的元素个数counts中减去，若元素个数counts中有任意一个小于0，则字符串A不包含字符串B，返回false；若都大于等于0，则字符串A包含字符串B，返回true。

```java
public class Solution {
    /**
     * @param A : A string includes Upper Case letters
     * @param B : A string includes Upper Case letter
     * @return :  if string A contains all of the characters in B return true else return false
     */
    public boolean compareStrings(String A, String B) {
        // write your code here
       int[] counts = new int[26];
       for(int i = 0;i < A.length();i++)
           counts[A.charAt(i)-'A']++;
       for(int j = 0;j < B.length();j++)
       {
           counts[B.charAt(j)-'A']--;
           if(counts[B.charAt(j)-'A']<0)
                return false;
       }
       return true;
    }
}
```


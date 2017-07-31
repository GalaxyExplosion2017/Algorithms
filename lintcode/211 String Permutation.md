## [211 String Permutation](http://www.lintcode.com/en/problem/string-permutation/)

**Description** 

Given two strings, write a method to decide if one is a permutation of the other.

**Example**

`abcd` is a permutation of `bcad`, but `abbe` is not a permutation of `abe`

##### Solution

用一个数组存储数组A中所有元素出现次数减去数组B中所有元素出现的次数，遍历数组，若有元素不等于0，则返回false，否则返回true。

```java
public class Solution {
    /*
     * @param A: a string
     * @param B: a string
     * @return: a boolean
     */
    public boolean Permutation(String A, String B) {
        // write your code here
        int[] arr = new int[256];
        for(int i = 0; i < A.length(); i++)
            arr[A.charAt(i)]++;
        for(int i = 0; i < B.length(); i++)
            arr[B.charAt(i)]--;
        for(int i : arr)
            if(i!=0) return false;
        return true;
    }
};
```


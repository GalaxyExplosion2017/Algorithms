## [172 Remove Element](http://www.lintcode.com/en/problem/remove-element/)

**Description**

Given an array and a value, remove all occurrences of that value in place and return the new length.

The order of elements can be changed, and the elements after the new length don't matter.

**Example**

Given an array `[0,4,4,0,0,2,4,4]`, `value=4`return `4` and front four elements of the array is `[0,0,0,2]`

**Intuition 1**

遍历数组，将不等于elem的元素从数组头n=0处开始覆盖，直到遍历完毕，返回n。

```javascript
public class Solution {
    /** 
     *@param A: A list of integers
     *@param elem: An integer
     *@return: The new length after remove
     */
    public int removeElement(int[] A, int elem) {
        // write your code here
        int n = 0;
        for(int i : A)
            if(i != elem)
                A[n++] = i;
        return n;
    }
}

```

**Intuition 2**

定义两个变量i,n，分别代表数组A的起始位置和长度，当i < n 时，如果A[i]==elem，则将A[—n]赋给A[i];其它情况下i自增，最后返回n

```java
public class Solution {
    /** 
     *@param A: A list of integers
     *@param elem: An integer
     *@return: The new length after remove
     */
    public int removeElement(int[] A, int elem) {
        // write your code here
        int i = 0;
        int n = A.length;
        while(i <  n)
        {
            if(A[i] == elem) A[i] = A[--n];
            else i++;
        }
        return n;
    }
}
```


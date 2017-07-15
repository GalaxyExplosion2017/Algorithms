#  [**50 Product of Array Exclude Itself**](http://www.lintcode.com/en/problem/product-of-array-exclude-itself/#)

**Description**

Given an integers array A.

Define B[i] = A[0] * ... * A[i-1] * A[i+1] * ... * A[n-1], calculate B **WITHOUT** divide operation.

**Example**

For A = `[1, 2, 3]`, return `[6, 3, 2]`.

**解题思路**

> 左右分治法，将B[i]分成left[i]*right[i]，left[i]=A[0]\*...\*A[i-1]，right[i]=A[i+1]\*...\*A[A.size()-1]，并且设不可再分值left[0]=1,right[A.size()-1]=1，将得到的结果加入集合B中，返回B。

```java
public class Solution {
    /**
     * @param A: Given an integers array A
     * @return: A Long array B and B[i]= A[0] * ... * A[i-1] * A[i+1] * ... * A[n-1]
     */
    public ArrayList<Long> productExcludeItself(ArrayList<Integer> A) {
        // write your code
        ArrayList<Long> B = new ArrayList<Long>();
        long[] left = new long[A.size()];
        long[] right = new long[A.size()];
        left[0]=1;
        for(int i=1;i<A.size();i++)
            left[i]=left[i-1]*A.get(i-1);
        right[A.size()-1]=1;
        for(int i=A.size()-2;i>=0;i--)
            right[i]=right[i+1]*A.get(i+1);
        for(int i=0;i<A.size();i++)
            B.add(left[i]*right[i]);
        return B;        
    }
}
```


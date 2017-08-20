## [197 Permutation Index](http://www.lintcode.com/en/problem/permutation-index/)

**Description**

Given a permutation which contains no repeated number, find its index in all the permutations of these numbers, which are ordered in lexicographical order. The index begins at 1.

**Example**

Given [1,2,4], return 1.

#### Solution

排列组合，一个n位数在字典顺序中的编号，等于每一位数后面比它小的数的个数的乘以它从后往前数位置的阶乘，例如对4个数的排列，各位的权值为：3！，2！，1！，0！。第一位之后的数小于第一位的个数是x，第二位之后的数小于第二位的个数是y，第三位之后的数小于第三的个数是z，第四位之后的数小于第四位的个数是w，则abcd排列所在的序列号:index = x\*3！+y\*2!+z\*1!

```java
public class Solution {
    /**
     * @param A an integer array
     * @return a long integer
     */
    public long permutationIndex(int[] A) {
        // Write your code here
        if(A == null || A.length == 0) return 0;
        long fact = 1;
        long index = 0;
        for(int i = A.length-2; i >= 0; i--){
            int count = 0;
            for(int j = i+1; j < A.length; j++)
                if(A[i]>A[j]) count++;
            index += fact * count;
            fact*=(A.length-i);
        }
        return index+1;
    }
}
```


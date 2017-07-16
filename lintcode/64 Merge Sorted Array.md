# [64 Merge Sorted Array](http://www.lintcode.com/en/problem/merge-sorted-array/)

**Description**

Given two sorted integer arrays A and B, merge B into A as one sorted array.

> #####  Notice
>
> You may assume that A has enough space (size that is greater or equal to *m* + *n*) to hold additional elements from B. The number of elements initialized in A and B are *m* and *n* respectively.

**Example**

A = `[1, 2, 3, empty, empty]`, B = `[4, 5]`

After merge, A will be filled as `[1, 2, 3, 4, 5]`

**解题思路**

> 有序表的合并，m，n分别为数组A，B元素的个数，创建一个合并后数组A的最后一个元素额索引index=m+n-1，分别遍历比较A，B数组中元素的大小，大的元素放在最后一位，直到有一个数组遍历完毕，将另一个数组剩余的元素有序地放入合并后的数组中。

```java
class Solution {
    /**
     * @param A: sorted integer array A which has m elements, 
     *           but size of A is m+n
     * @param B: sorted integer array B which has n elements
     * @return: void
     */
    public void mergeSortedArray(int[] A, int m, int[] B, int n) {
        // write your code here
        int i = m-1;
        int j = n-1;
        int index = m+n-1;
        while(i>=0&&j>=0)
        {
            if(A[i]>B[j])
                A[index--]=A[i--];
            else
                A[index--]=B[j--];
        }
        while(i>=0)
            A[index--]=A[i--];
        while(j>=0)
            A[index--]=B[j--];
    }
}
```


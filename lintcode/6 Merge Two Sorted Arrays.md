# 6 Merge Two Sorted Arrays 

### **Description:**

> Merge two given sorted integer array *A* and *B* into a new sorted integer array.

#### Example:

> A=`[1,2,3,4]`
>
> B=`[2,4,5,6]`
>
> return `[1,2,2,3,4,4,5,6]`

#### 解题思路：

>若两个**有序**数组A、B都不为空，先初始化一个新数组Result，长度为两个组数长度之和，然后比较A、B两个数组中元素的大小，小的元素赋值给新数组的第一个元素，直到原来A、B数组其中一个全部赋值完，再把另外一个数组剩余元素赋值给新数组

```java
class Solution {
    /**
     * @param A and B: sorted integer array A and B.
     * @return: A new sorted integer array
     */
    public int[] mergeSortedArray(int[] A, int[] B) {
        // Write your code here
        if(A==null ||B==null) 
            return null;
        int i=0;
        int j=0;
        int index=0;
        int[] result =new int[A.length+B.length];
        while(i<A.length&&j<B.length)
        {
            if(A[i]<B[j])
                result[index++]=A[i++];
            else
                result[index++]=B[j++];
        }
        while(i<A.length)
            result[index++]=A[i++];
        while(j<B.length)
            result[index++]=B[j++];
        return result;
    }
}
```


## 464.整数排序 Sort Integers II 

> 效率比较高的快速排序算法：
>
> 先选定一个权值pivot，用来作为基准，定义两个变量left,right，一个从右边往左边查找比pivot小的元素，一个从左边往右边查找比较pivot大的元素，然后交换，直到left>right，然后分成三个片区，再次递归[0,right],[left,A.length-1],直到完全有序。

```java
public class Solution {
    /**
     * @param A an integer array
     * @return void
     */
    public void sortIntegers2(int[] A) {
        quickSort(A, 0, A.length - 1);
    }
    
    private void quickSort(int[] A, int start, int end) {
        if (start >= end) {
            return;
        }
        
        int left = start, right = end;
        // key point 1: pivot is the value, not the index
        int pivot = A[(start + end) / 2];

        // key point 2: every time you compare left & right, it should be 
        // left <= right not left < right
        while (left <= right) {
            while (left <= right && A[left] < pivot) {
                left++;
            }
            while (left <= right && A[right] > pivot) {
                right--;
            }
            if (left <= right) {
                int temp = A[left];
                A[left] = A[right];
                A[right] = temp;
                
                left++;
                right--;
            }
        }
        
        quickSort(A, start, right);
        quickSort(A, left, end);
    }
}
```


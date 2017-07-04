## 463.整数排序 Sort Integers

> 主要思想:三种基本排序算法里面,性能排序:插入排序>选择排序>冒泡排序,因此选择使用插入排序算法。  	

##### 插入排序

> 升序，以数组中第一个数为基准,从第二个数开始依次去前一个数进行比较，若小于前一个数，则继续往前边进行比较，直到插入到合适位置形成升序

```java
public class Solution {
    /**
     * @param A an integer array
     * @return void
     */
    public void sortIntegers(int[] A) {
        // Write your code here
        //insertSort
        for(int i = 1;i<=A.length-1;i++){
          for(int j=i;j>0;j--){
              if(A[j]<=A[j-1]){
                  int t=A[j];
                  A[j]=A[j-1];
                  A[j-1]=t;
              }else
                break;
          }
        }        
    }
}	
```



##### 选择排序

>主要思想：初始用一个临时变量min存储第i个元素，然后拿它依次与后面的元素比较，找出最小的元素，存储最小元素的下标，然后与第i个元素交换位置,知道数组有序.

```java
public class Solution {
    /**
     * @param A an integer array
     * @return void
     */
    public void sortIntegers(int[] A) {
        // Write your code here
        //insertSort
        for(int i=0;i<A.length-1;i++){
            int min = i;
            for(int j=A.length-1;j>i;j--){
                if(A[min]>A[j])
                    min=j;    
               
                   }
                  if(i!=min)
                  { int t=A[min];
                    A[min]=A[i];
                    A[i]=t;
                  }
        }        
    }
}


	
```



##### 改进的冒泡排序

>主要思想:以一个标志True记录状态，成为循环判断条件，然后使标志为false，从最后一个元素开始,与前一个元素进行比较，若小于前一个元素，则交换位置，标记为True，直到最小元素移动到最前面，直到第二个元素与第一个元素进行比较；若后面已经有序，则标志不改为True，跳出循环，直到所有元素都有序。

```java
public class Solution {
    /**
     * @param A an integer array
     * @return void
     */
    public void sortIntegers(int[] A) {
        // Write your code here
        boolean flag = true;
        for(int i=0;i<(A.length-1)&&flag;i++){
            flag=false;
            for(int j=A.length-1;j>i;j--){
                if(A[j]<A[j-1])
                  {  
                    int t=A[j];
                    A[j]=A[j-1];
                    A[j-1]=t;
                    flag=true;
                  }
            }
        }        
    }
}
```


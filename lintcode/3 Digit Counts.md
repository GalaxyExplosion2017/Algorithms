## [3 Digit Counts](http://www.lintcode.com/en/problem/digit-counts/#)

##### Description

Count the number of *k*'s between *0* and *n*. *k* can be *0* - *9*.

##### Example

if n = `12`, k = `1` in

```
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12]

```

we have FIVE 1's (1, 10, 11, 12)

##### Solution

遍历0到n，当前数不为0中，判断每一位是否含k，含k则个数count++，最后返回所有数中含k的个数totalCount.

```java
class Solution {
    /*
     * param k : As description.
     * param n : As description.
     * return: An integer denote the count of digit k in 1..n
     */
    public int digitCounts(int k, int n) {
        // write your code here
        int totalCount = 0;
        for(int i = 0; i <= 12; i++){
            totalCount += count(k,i);
        }
        return totalCount;
    }
    
    public int count(int k, int value){
        int n = 0;
        while(value != 0){
            int temp = value % 10;
            if(temp == k){
                n++;
            }
            value /= 10;
        }
        return n;
    }
};

```




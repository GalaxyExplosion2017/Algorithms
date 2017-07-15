# 46 Majority Number

**Description**

Given an array of integers, the majority number is the number that occurs `more than half` of the size of the array. Find it.

> **Notice**
>
> You may assume that the array is non-empty and the majority number always exist in the array.

**Example**

Given `[1, 1, 1, 1, 2, 2, 2]`, return `1`

**解题思路**

> 将第一个数设置为候选数candidate，个数count设置为1，遍历后面的每个数，与侯选数相同则个数count加1，不同则减1，若个数count=0,则设置当前数为侯选数candidate，继续执行之前操作，直到遍历结束。

```java
public class Solution {
    /**
     * @param nums: a list of integers
     * @return: find a  majority number
     */
    public int majorityNumber(ArrayList<Integer> nums) {
        // write your code
       int candidate=-1;
       int count=0;
       for(int i=0;i<nums.size();i++)
       {
           if(count==0)
           {
               candidate=nums.get(i);
               count=1;
           }else if(candidate==nums.get(i))
           {
               count++;
           }else
                count--;
       }return candidate;
    }
}
```




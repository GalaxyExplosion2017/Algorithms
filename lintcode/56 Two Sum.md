# 56 Two Sum 

**Description**

Given an array of integers, find two numbers such that they add up to a specific target number.

The function `twoSum` should return *indices* of the two numbers such that they add up to the target, where index1 must be less than index2. Please note that your returned answers (both index1 and index2) are **NOT** zero-based.

> #####  Notice
>
> You may assume that each input would have exactly one solution

**Example**

numbers=`[2, 7, 11, 15]`, target=`9`

return `[1, 2]`

**解题思路**

> 建立一个哈希表map，key存放数，value存放索引，若map.get(numbers[i])==null，则将target-numbers[i]存放在map的key中，若map.get(numbers[i])!=null,则说明之前存在一个数个当前数numbers[i]之和等于target，返回之前数map.get(numbers[i])的索引+1，和当前数的索引+1，放入结果中，返回结果。

```java
public class Solution {
    /*
     * @param numbers : An array of Integer
     * @param target : target = numbers[index1] + numbers[index2]
     * @return : [index1 + 1, index2 + 1] (index1 < index2)
     */
    public int[] twoSum(int[] numbers, int target) {
        // write your code here
        HashMap<Integer,Integer> map = new HashMap<Integer,Integer>();
        int[] index =new int[]{0,1};
        for(int i=0;i<=numbers.length-1;i++)
        {
            if(map.get(numbers[i])!=null)
            {
                index[0]=map.get(numbers[i])+1;
                index[1]=i+1;
                return index;
            }
            map.put(target-numbers[i],i);
        }
        index = new int[]{};
        return index;
    }
}
```


# [100 Remove Duplicates from Sorted Array](http://www.lintcode.com/en/problem/remove-duplicates-from-sorted-array/)

**Description**

Given a sorted array, remove the duplicates in place such that each element appear only once and return the new length.

Do not allocate extra space for another array, you must do this in place with constant memory.

**Example**

Given input array `A = [1,1,2]`,

Your function should return `length = 2`, and A is now `[1,2]`.

**解题思路** 1

> 如果有序数组不为空，创建记录初始长度的变量length=1,初始岗哨dump数组第一个元素nums[0],遍历数组，若当前元素与岗哨不相等，则将当前元素nums[i]赋给数组中的元素nums[length++]的位置，并且也赋给岗哨dump，直到遍历完毕，返回长度length。

```java
public class Solution {
    /**
     * @param A: a array of integers
     * @return : return an integer
     */
    public int removeDuplicates(int[] nums) {
        // write your code here
        if(nums == null||nums.length == 0) return 0;
        int length = 1;
        int dump = nums[0];
        for(int i = 1;i < nums.length;i++)
        {
            if(dump != nums[i])
            {
                nums[length++] = nums[i];
                dump = nums[i];
            }
        }
        return length;
    }
}
```

**解题思路 2**

> foreach遍历。创建一个变量n记为数组长度，若数组不为空，初始值长度为1，设置第一个元素为岗哨，foreach遍历数组，若当前元素大于岗哨，则将当前元素移动到岗哨位置后面，将当前元素设置为岗哨，直到遍历完毕数组。

```java
public class Solution {
    /**
     * @param A: a array of integers
     * @return : return an integer
     */
    public int removeDuplicates(int[] nums) {
        // write your code here
        int n = nums.length > 0 ? 1:0;
        for(int i : nums)
            if(i>nums[n-1])
            	nums[n++] = i;
        return n;
    }
}
```


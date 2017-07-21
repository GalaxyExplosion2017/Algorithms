## [101 Remove Duplicates from Sorted Array II ](http://www.lintcode.com/en/problem/remove-duplicates-from-sorted-array-ii/)

**Description**

Follow up for "Remove Duplicates":
What if duplicates are allowed at most *twice*?

*For example,*
Given sorted array A = `[1,1,1,2,2,3]`,

Your function should return length = `5`, and A is now `[1,1,2,2,3]`.

**解题思路**

> 若数组不为空，将数组第一个元素设为岗哨dump，创建变量n记录数组中的位置，初始为0，创建出现次数的变量index,然后遍历数组中的每一个元素，若index大于0，index减1，则将当然元素移动到数组中第n个位置，并且设为岗哨，然后n加1，重复上述方法，直到遍历完数组中所有的元素，返回n。

```java
public class Solution {
    /**
     * @param A: a array of integers
     * @return : return an integer
     */
    public int removeDuplicates(int[] nums) {
        // write your code here
        if(nums==null||nums.length==0) return 0;
        int n =  0;
        int index = 2;
        int dump = nums[n];
        for(int i = 0;i<nums.length;i++)
        {
            if(nums[i]==dump&&index>0)
            {
                dump = nums[n++] = nums[i];
                index--;
            }
            if(nums[i]>dump)
            {
                index = 2;
                dump = nums[n++] = nums[i];
                index--;
            }
        }
        return n;
    }
}
```

**解题思路 2**

> 创建一个变量n，记录删除后数组的长度，遍历数组，若n小于2或者当前数大于nums[n-2],将当前数赋给nums[n++],直到遍历完毕，返回n。

```java
public class Solution {
    /**
     * @param A: a array of integers
     * @return : return an integer
     */
    public int removeDuplicates(int[] nums) {
        // write your code here
        int n = 0;
        for(int i : nums)
            if(n < 2 || i > nums[n-2])
                nums[n++] = i;
        return n;
    }
}
```


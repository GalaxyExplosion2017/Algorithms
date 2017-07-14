# 39  [**Recover Rotated Sorted Array**](http://www.lintcode.com/en/problem/recover-rotated-sorted-array/#)

**Description:**

Given a **rotated** sorted array, recover it to sorted array in-place.

**Clarification**:

What is rotated array?

- For example, the orginal array is [1,2,3,4], The rotated array of it can be [1,2,3,4], [2,3,4,1], [3,4,1,2], [4,1,2,3]

**Example**:

`[4, 5, 1, 2, 3]` -> `[1, 2, 3, 4, 5]`

**解题思路：**

> 找到一个比后一个数大的数的索引i，然后将[0,i],[i+1,nums.size()-1]分别逆置，最后将[0,nums.size()-1]逆置

```java
public class Solution {
    /**
     * @param nums: The rotated sorted array
     * @return: void
     */
    public void recoverRotatedSortedArray(ArrayList<Integer> nums) {
        // write your code
        for(int i = 0;i < nums.size()-1;i++)
        {
            if(nums.get(i)>nums.get(i+1))
            {
                reverse(nums,0,i);
                reverse(nums,i+1,nums.size()-1);
                reverse(nums,0,nums.size()-1);
                return;
            }
        }
    }
    public void reverse(ArrayList<Integer> nums,int start,int end)
    {
        for(int i = start,j = end;i<j;i++,j--)
        {
            int temp = nums.get(i);
            nums.set(i,nums.get(j));
            nums.set(j,temp);
        }
    }
}
```


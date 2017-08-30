## [547 Intersection of Two Arrays](http://www.lintcode.com/en/problem/intersection-of-two-arrays/)

##### Description

Given two arrays, write a function to compute their intersection.

##### ** Notice

- Each element in the result must be unique.
- The result can be in any order.

##### Example

Given *nums1* = `[1, 2, 2, 1]`, *nums2* = `[2, 2]`, return `[2]`.

##### Solution

两个HashSet，第一个用来存储nums1，然后遍历第二个数组，如果第二个数组中存在于第一个数组，则将当前元素加入第二个HashSet中，再把第二个HashSet中的元素放入一个数组中，返回次数组。

```java
public class Solution {
    /**
     * @param nums1 an integer array
     * @param nums2 an integer array
     * @return an integer array
     */
    public int[] intersection(int[] nums1, int[] nums2) {
        // Write your code here
        Set<Integer> set = new HashSet<Integer>();
        Set<Integer> intersection = new HashSet<>();
        for(int i : nums1){
            set.add(i);
        }
        for(int j : nums2){
            if(set.contains(j)){
                intersection.add(j);
            }
        }
        int[] res = new int[intersection.size()];
        int index = 0;
        for(int k : intersection){
            res[index++] = k;
        }
        return res;
    }
}
```


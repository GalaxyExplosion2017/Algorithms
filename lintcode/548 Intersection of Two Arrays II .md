## [548 Intersection of Two Arrays II ](http://www.lintcode.com/en/problem/intersection-of-two-arrays-ii/)

##### Description

Given two arrays, write a function to compute their intersection.

##### ** Notice

- Each element in the result should appear as many times as it shows in both arrays.
- The result can be in any order. 

##### Example

Given *nums1* = `[1, 2, 2, 1]`, *nums2* = `[2, 2]`, return `[2, 2]`.

##### Solution

创建HashMap用来存第一个数组，遍历第二个数组，若HashMap中存在当前元素，则将当前元素放入List中，最后将List中的元素放入熟组中，返回熟组.

```java
public class Solution {
    /**
     * @param nums1 an integer array
     * @param nums2 an integer array
     * @return an integer array
     */
    public int[] intersection(int[] nums1, int[] nums2) {
        // Write your code here
        Map<Integer,Integer> map = new HashMap<Integer,Integer>();
        List<Integer> list = new ArrayList<Integer>();
        for(int i : nums1){
            if(!map.containsKey(i)){
                map.put(i,1);
            }else{
                map.put(i,map.get(i)+1);
            }
        }
        for(int j : nums2){
            if(map.containsKey(j) && map.get(j) > 0){
                list.add(j);
                map.put(j,map.get(j)-1);
            }
        }
        int[] res = new int[list.size()];
        int index = 0;
        for(int k : list){
            res[index++] = k;
        }
        return res;
    }
}
```



##### Soluton 2

```java
public class Solution {
    /**
     * @param nums1 an integer array
     * @param nums2 an integer array
     * @return an integer array
     */
    public int[] intersection(int[] nums1, int[] nums2) {
        // Write your code here
        List<Integer> list1 = new ArrayList<Integer>();
        List<Integer> list2 = new ArrayList<Integer>();
        for(int i : nums1){
            list1.add(i);
        }
        for(int j : nums2){
            if(list1.contains(j)){
                list2.add(j);
                list1.remove((Integer)j);
            }
        }
        int[] res = new int[list2.size()];
        int index = 0;
        for(int k : list2){
            res[index++] = k;
        }
        return res;
    }
}
```


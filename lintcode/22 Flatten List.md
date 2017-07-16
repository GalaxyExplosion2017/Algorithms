# [22 Flatten List](http://www.lintcode.com/en/problem/flatten-list/)

**Description**

Given a list, each element in the list can be a list or integer. flatten it into a simply list with integers.

> #####  Notice
>
> If the element in the given list is a list, it can contain list too.

**Example**

Given `[1,2,[1,2]]`, return `[1,2,1,2]`.

Given `[4,[3,[2,[1]]]]`, return `[4,3,2,1]`.

> 解题思路：创建一个结果集list，遍历集合nestedList中的每一个元素，判断若是Integer类型，则添加到list中，若不是，先获取列表中的元素，迭代，继续判断，直到迭代结束，将所有Integer类型元素添加到list中。

```java
/**
 * // This is the interface that allows for creating nested lists.
 * // You should not implement it, or speculate about its implementation
 * public interface NestedInteger {
 *
 *     // @return true if this NestedInteger holds a single integer,
 *     // rather than a nested list.
 *     public boolean isInteger();
 *
 *     // @return the single integer that this NestedInteger holds,
 *     // if it holds a single integer
 *     // Return null if this NestedInteger holds a nested list
 *     public Integer getInteger();
 *
 *     // @return the nested list that this NestedInteger holds,
 *     // if it holds a nested list
 *     // Return null if this NestedInteger holds a single integer
 *     public List<NestedInteger> getList();
 * }
 */
public class Solution {

    // @param nestedList a list of NestedInteger
    // @return a list of integer
    public List<Integer> flatten(List<NestedInteger> nestedList) {
        // Write your code here
        List<Integer> list = new ArrayList<Integer>();
        for(NestedInteger nl:nestedList)
        {
            if(nl.isInteger())
                list.add(nl.getInteger());
            else
                list.addAll(flatten(nl.getList()));                
        }
        return list;
    }
}
```


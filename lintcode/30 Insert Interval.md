# 30 Insert Interval

**Description:**

Given a non-overlapping interval list which is sorted by start point.

Insert a new interval into it, make sure the list is still in order and** non-overlapping **(merge intervals if necessary).

**Example:**

Insert **[2, 5]** into **[[1,2], [5,9]]**, we get **[[1,9]]**.

Insert **[3, 4]** into **[[1,2], [5,9]]**, we get **[[1,2], [3,4], [5,9]]**.

**解题思路：**

> 如果插入区间的左端点大于遍历区间的右端点，result中添加遍历区间，插入位置索引insertPos++；如果插入区间的右端点小于遍历区间的左端点，result中添加遍历区间，插入位置索引insertPos不变；如果插入区间的左端点小于等于遍历区间的右端点或者插入区间的右端点大于等于遍历区间的左端点，则将这两个区间合并，分别比较两个区间左端点和右端点，两个左端点的最小值就是合并后区间的左端点，两个右端点的最大值就是合并后区间的右端点。

```java
/**
 * Definition of Interval:
 * public classs Interval {
 *     int start, end;
 *     Interval(int start, int end) {
 *         this.start = start;
 *         this.end = end;
 *     }
 */

class Solution {
    /**
     * Insert newInterval into intervals.
     * @param intervals: Sorted interval list.
     * @param newInterval: A new interval.
     * @return: A new sorted interval list.
     */
    public ArrayList<Interval> insert(ArrayList<Interval> intervals, Interval newInterval) {
        if(intervals==null||newInterval==null) return intervals;
        ArrayList<Interval> result = new ArrayList<Interval>();
        // write your code here
        int insertPos=0;
        for(Interval interval:intervals)
        {
            if(interval.start>newInterval.end)
            {
                result.add(interval);
            }else if(interval.end<newInterval.start)
            {   
                result.add(interval);
                insertPos++;
            }else
            {
               newInterval.start = Math.min(interval.start, newInterval.start);
               newInterval.end = Math.max(interval.end, newInterval.end);
            }
        }
        result.add(insertPos,newInterval);       
        return result;
    }
}
```


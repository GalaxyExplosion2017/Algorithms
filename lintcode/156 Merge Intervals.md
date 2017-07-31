## [156 Merge Intervals](http://www.lintcode.com/en/problem/merge-intervals/)

#### Description

Given a collection of intervals, merge all overlapping intervals.

**Example**

Given intervals => merged intervals:

```
[                     [
  [1, 3],               [1, 6],
  [2, 6],      =>       [8, 10],
  [8, 10],              [15, 18]
  [15, 18]            ]
]
```

#### Solution

将给定的链表按照start排序，然后再比较链表中前一个元素的end与当前元素的start，若end < start，则将当前元素加入到ist中，否则前一个元素的end取它和当前元素end的最大值，直到遍历完给定的链表，返回list。

```java
/**
 * Definition of Interval:
 * public class Interval {
 *     int start, end;
 *     Interval(int start, int end) {
 *         this.start = start;
 *         this.end = end;
 *     }
 */

class Solution {
    /**
     * @param intervals, a collection of intervals
     * @return: A new sorted interval list.
     */
    public List<Interval> merge(List<Interval> intervals) {
        // write your code here
        List<Interval> list = new ArrayList<Interval>();
        if(intervals == null || intervals.size() < 2) return intervals;
        Collections.sort(intervals, new Comparator<Interval>(){
            public int compare(Interval i1, Interval i2){
                return i1.start - i2.start;
            }
        });
        Interval last = null;
        for(Interval interval : intervals){
            if(last == null || interval.start > last.end){
                list.add(interval);
                last = interval;
            }else
                last.end = Math.max(last.end,interval.end);
        }
        return list;
    }
}
```


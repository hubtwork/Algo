## LeetCode Problems



#### 57. Insert Interval

- **link**  [57. Insert Interval](https://leetcode.com/problems/insert-interval/description/)

- **lang**  `kotlin` 
- **tags**  `Array` 

```kotlin
import kotlin.math.max
class Solution {
    fun insert(intervals: Array<IntArray>, newInterval: IntArray): Array<IntArray> {
        var answer = mutableListOf<IntArray>()
        var i = 0
        var size = intervals.size
        // pass prev-intervals than newInterval's start
        while (
            i < size && 
            intervals[i][0] <= newInterval[0]
        ) answer.add(intervals[i++])
        // case 1. current interval includes newInterval's start
        // case 2. add newInterval as new interval
        if (
            i > 0 && 
            intervals[i-1][1] >= newInterval[0]
        ) intervals[i-1][1] = max(intervals[i-1][1], newInterval[1])
        else answer.add(intArrayOf(newInterval[0], newInterval[1]))
        // consume include-possible intervals
        while (
            i < size &&
            answer.last()[1] >= intervals[i][0]
        ) answer.last()[1] = max(answer.last()[1], intervals[i++][1])
        // add rest intervals
        while (i < size) answer.add(intervals[i++])
        return answer.toTypedArray()
    }
}
```

---


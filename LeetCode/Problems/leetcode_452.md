## LeetCode Problems



#### 452. Minimum Number of Arrows to Burst Balloons

- **link**  [452. Minimum Number of Arrows to Burst Balloons](https://leetcode.com/problems/minimum-number-of-arrows-to-burst-balloons/description/)

- **lang**  `kotlin` 
- **tags**  `Array` `Greedy` `Sorting`

```kotlin
class Solution {
    fun findMinArrowShots(points: Array<IntArray>): Int {
        // sort by endPoint ( startPoint will miss some targeting points )
        points.sortBy({ it[1] })
        var arrowCount = 1
        var target = points[0][1]
        // iterate
        for (i in 1..points.size-1) {
            // if current balloon is out of range, shot new arrow.
            if (points[i][0] > target) {
                arrowCount++
                target = points[i][1]
            }
        }
        return arrowCount
    }
}
```

---


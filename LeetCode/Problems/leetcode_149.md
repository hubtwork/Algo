## LeetCode Problems



#### 149. Max Points on a Line

- **link**  [149. Max Points on a Line](https://leetcode.com/problems/max-points-on-a-line/)

- **lang**  `kotlin` 
- **tags**  `Array` `Math` `Hash Table`

```kotlin
import kotlin.math.max
class Solution {
    fun maxPoints(points: Array<IntArray>): Int {
        var result = 0
        // full-scan for each point pair.
        for (i in 0 until points.size) {
            /*
                Line-Point-Calculation-Condition.
                #1) same with seed => Unconditionally counted.
                #2) same point X => can'be computed n/0, so separate from increments.
                #3) record increment between current and seed count.
             */
            val seed = points[i]
            var samePoint = 1
            var sameX = 0
            var maxCount = 0
            val incs = mutableMapOf<Double, Int>()
            // scan other points.
            for(j in 0 until points.size) {
                if (i == j) continue
                // check each point is at conditions #1 ~ #3. 
                if (seed[0] == points[j][0] && seed[1] == points[j][1]) samePoint++
                else if (seed[0] == points[j][0]) sameX++
                else {
                    val inc = (points[j][1] - seed[1]).toDouble() / (points[j][0] - seed[0])
                    incs[inc]
                        ?.let { incs[inc] = it + 1 }
                        ?:run { incs[inc] = 1 }
                    maxCount = max(maxCount, incs[inc]!!)
                }
            }
            // maxCount of all lines from this seed = max-point-line's count + current point's count
            maxCount = max(maxCount, sameX) + samePoint
            result = max(result, maxCount)
        }
        return result
    }
}
```

---


## LeetCode Problems



#### 1011. Capacity To Ship Packages Within D Days

- **link**  [1011. Capacity To Ship Packages Within D Days](https://leetcode.com/problems/capacity-to-ship-packages-within-d-days/)

- **lang**  `kotlin` 
- **tags** `Array`  `Binary Search`

```kotlin
import kotlin.math.max
class Solution {
    fun shipWithinDays(weights: IntArray, days: Int): Int {
        if (weights.isEmpty()) return 0
        var start = 0
        var end = 0
      	// reduce search range.
        weights.forEach { weight ->
            start = max(start, weight)
            end += weight
        }
        // binary search
        while (start < end) {
            val mid = (start + end) / 2
            if (weights.check(mid, days)) end = mid
            else start = mid + 1
        }
        return start
    }
    // check function for current capacity is valid
    fun IntArray.check(capacity: Int, days: Int): Boolean {
        var dayPath = 1
        var sum = 0
        for (i in 0 until size) {
            if (sum + this[i] > capacity) {
                dayPath ++
                sum = this[i]
                if (dayPath > days) return false
            } else {
                sum += this[i]
            }
        }
        return true
    }
}
```

---


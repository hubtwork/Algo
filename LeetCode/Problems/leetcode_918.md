## LeetCode Problems



#### 918. Maximum Sum Circular Subarray

- **link**  [918. Maximum Sum Circular Subarray](https://leetcode.com/problems/maximum-sum-circular-subarray/)

- **lang**  `kotlin` 
- **tags** `Array` `DP` `Divide and Conquer`

```kotlin
import kotlin.math.max
import kotlin.math.min
class Solution {
    fun maxSubarraySumCircular(nums: IntArray): Int {
        // get sum of total-array
        var sum = 0
        // use local min, max value for calculate max sum from circular-subarray
        var localMin = 30001
        var localMax = -30001
        var globalMin = 30001
        var globalMax = -30001
        // iterate
        nums.forEach { num ->
            sum += num
            // local min/max means result compared by 2 things (only current, passed-sum + current)
            localMin = min(localMin + num, num)
            localMax = max(localMax + num, num)
            // global min/max means overall-min/max
            globalMin = min(globalMin, localMin)
            globalMax = max(globalMax, localMax)
        }
        // if global-max is negative, best is itself.
        // if global-max is positive, best is max between itself and sum of rest-array (except for globalMin-family)
        return if (globalMax > 0) max(globalMax, sum - globalMin) else globalMax
    }
}
```

---


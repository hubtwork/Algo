## LeetCode Problems



#### 2444. Count Subarrays With Fixed Bounds

- **link**  [2444. Count Subarrays With Fixed Bounds](https://leetcode.com/problems/count-subarrays-with-fixed-bounds/)

- **lang**  `kotlin` 
- **tags**  `Array` `Queue` `Sliding Window`

```kotlin
import kotlin.math.min
class Solution {
    fun countSubarrays(nums: IntArray, minK: Int, maxK: Int): Long {
        var result = 0L
        var rangeStart = 0
        var minStart: Int? = null
        var maxStart: Int? = null
        
        nums.forEachIndexed { idx, num ->
            // if it's not in range, clear current record with new range start-idx
            if (num < minK || num > maxK) {
                minStart = null
                maxStart = null
                rangeStart = idx + 1
            }
            // mark each minK and maxK 
            if (num == minK) minStart = idx
            if (num == maxK) maxStart = idx
            // if current record is in range, add to result count
            if (minStart != null && maxStart != null) {
                result += min(minStart!!, maxStart!!) - rangeStart + 1
            }
        }
        return result
    }
}
```

---


## LeetCode Problems



#### 2187. Minimum Time to Complete Trips

- **link**  [2187. Minimum Time to Complete Trips](https://leetcode.com/problems/minimum-time-to-complete-trips/)

- **lang**  `kotlin` 
- **tags** `Array` `Binary Search`

```kotlin
class Solution {
    fun minimumTime(time: IntArray, totalTrips: Int): Long {
        var left = 0L
        var right = Long.MAX_VALUE
        // binary search to find best valid tripTime
        while (left <= right) {
            val mid: Long = left + (right - left) / 2
            if (isTimeValid(time, totalTrips, mid)) right = mid - 1
            else left = mid + 1
        }
        return left
    }

    fun isTimeValid(time: IntArray, totalTrips: Int, tripTime: Long): Boolean {
        var sum = 0L
        for (i in time) {
            // add all possible trip-handling-time for each bus
            sum += (tripTime / i)
            // if possibly handling in given tripTime, return true
            if (sum >= totalTrips) return true
        }
        return false
    }
}
```

---


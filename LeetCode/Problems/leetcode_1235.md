## LeetCode Problems



#### 1235. Maximum Profit in Job Scheduling

- **link**  [1235. Maximum Profit in Job Scheduling](https://leetcode.com/problems/maximum-profit-in-job-scheduling/)

- **lang**  `kotlin` 
- **tags**  `Array` `Binary Search` `DP` `Sorting`

```kotlin
import kotlin.math.max
class Solution {
    data class Job(
        val start: Int,
        val end: Int,
        val profit: Int
    )
    fun jobScheduling(startTime: IntArray, endTime: IntArray, profit: IntArray): Int {]
        // sorting jobs by endTime
        val jobs = mutableListOf<Job>()
        for (i in 0..startTime.size-1) jobs.add(Job(startTime[i], endTime[i], profit[i]))
        jobs.sortBy { it.end }
        /*
            from min endTime to max endTime,
            calculate current endTime job based bestProfit.
            
            conditional about endTime
            1. current time's best profit is max(beforeTime, current profit)
            2. track backward and seek more best profit is exists
                (check) if job exists with endTime before current's startTime:
                        current time's bestProfit = max(current best, before's best + current's profit)
        */
        val bestProfit = IntArray(startTime.size).apply { this[0] = jobs[0].profit }
        for (current in 1..jobs.size-1) {
            bestProfit[current] = max(bestProfit[current-1], jobs[current].profit)
            for (back in current-1 downTo 0) {
                if (jobs[back].end <= jobs[current].start) {
                    bestProfit[current] = max(bestProfit[current], bestProfit[back] + jobs[current].profit)
                    break
                }
            }
        }
        var result = -1
        bestProfit.forEach { profit -> result = max(result, profit) }
        return result
    }
}
```

---


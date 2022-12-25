## LeetCode Problems



#### 2389. Longest Subsequence With Limited Sum

- **link**  [2389. Longest Subsequence With Limited Sum](https://leetcode.com/problems/longest-subsequence-with-limited-sum/description/)

- **lang**  `kotlin` 
- **tags**  `Array` `Greedy` `Sorting`

```kotlin
class Solution {
    fun answerQueries(nums: IntArray, queries: IntArray): IntArray {
        nums.sort()
        val answer = IntArray(queries.size)
        for (i in 0..queries.size-1) {
            var sum = 0
            // check given queries' each possibilities.
            for (j in 0..nums.size-1) {
                sum += nums[j]
                // if sum is over, current idx ( used number's count - 1 ) is LS.
                if (sum > queries[i]) {
                    answer[i] = j
                    break
                }
                // if reached at last and sum is less than / equal to query, all count is LS.
                if (j == nums.size-1 && sum <= queries[i]) answer[i] = j+1
            }
        }
        return answer
    }
}
```

---


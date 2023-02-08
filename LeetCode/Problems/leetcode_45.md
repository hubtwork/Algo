## LeetCode Problems



#### 45. Jump Game II

- **link**  [45. Jump Game II](https://leetcode.com/problems/jump-game-ii/description/)

- **lang**  `kotlin` 
- **tags**  `Array` `DP` `Greedy`

```kotlin
class Solution {
    fun jump(nums: IntArray): Int {
        val len = nums.size
        if (len == 1) return 0
        val dp = IntArray(len)
        // jump from each block.
        for (curr in 0 until len) {
            // record each block's mean approach steps.
            for (next in 1 until nums[curr] + 1) {
                // if reached fast-forward to last block, return answer
                if (curr + next >= len - 1) return dp[curr] + 1
                // if recorded minimum step exists, pass it. ( it's not a fastest step )
                if (dp[curr + next] > 0) continue
                // record fastest step.
                dp[curr + next] = dp[curr] + 1
            }
        }
        return dp[len-1]
    }
}
```

---


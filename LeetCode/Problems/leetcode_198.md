## LeetCode Problems



#### 198. House Robber

- **link**  [198. House Robber](https://leetcode.com/problems/house-robber/description/)

- **lang**  `kotlin` 
- **tags**  `Array` `DP`

```kotlin
import kotlin.math.max
class Solution {
    fun rob(nums: IntArray): Int {
        // avoid logic : if 1 house 
        val size = nums.size
        if (size == 1) return nums[0]
        // with Dynamic Programming for get maximum profit on each house.
        val dp = IntArray(size)
        dp[0] = nums[0]
        dp[1] = max(nums[0], nums[1])
        // robber can steal not-adjacent house.
        // so in each step, max profit is 2-before max profit + current house or 1-before max profit.
        for (i in 2..size-1) dp[i] = max(dp[i-1], dp[i-2] + nums[i])
        return max(dp[size-1], dp[size-2])
    }
}
```

---


## LeetCode Problems



#### 70. Climbing Stairs

- **link**  [70. Climbing Stairs](https://leetcode.com/problems/climbing-stairs/description/)

- **lang**  `kotlin` 
- **tags**  `Math` `DP` `Memoization`

```kotlin
class Solution {
    fun climbStairs(n: Int): Int {
        if (n < 3) return n
        var dp = IntArray(n).apply {
            // way to reach 1 stair : 1, 2 stair : 2 ( 1+1, 2 ) 
            set(0, 1)
            set(1, 2)
        }
        // can reach each stair by 2 ways ( dp[i-2] + dp[i-1] )
        // 1) way for dp[i-2] + jump 2steps
        // 2) way for dp[i-1] + jump 1steps
        for (i in 2..n-1) dp[i] = dp[i-1] + dp[i-2]
        return dp[n-1]
    }
}
```

---


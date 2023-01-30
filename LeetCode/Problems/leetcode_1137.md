## LeetCode Problems



#### 1137. N-th Tribonacci Number

- **link**  [1137. N-th Tribonacci Number](https://leetcode.com/problems/n-th-tribonacci-number/description/)

- **lang**  `kotlin` 
- **tags**  `Math`  `DP`

```kotlin
class Solution {
    fun tribonacci(n: Int): Int {
        // process definitive cases
        if (n == 0) return 0
        if (n <= 2) return 1
        // if not, do case by case for Tribonacci
        val dp = IntArray(n + 1)
        dp[1] = 1
        dp[2] = 1
        // iterate
        for (i in 3 until n + 1) {
            dp[i] = dp[i-1] + dp[i-2] + dp[i-3]
        }
        return dp[n]
    }
}
```

---


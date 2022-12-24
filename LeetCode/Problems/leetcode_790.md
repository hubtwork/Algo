## LeetCode Problems



#### 790. Domino and Tromino Tiling

- **link**  [790. Domino and Tromino Tiling](https://leetcode.com/problems/domino-and-tromino-tiling/)

- **lang**  `kotlin` 
- **tags** `DP`

```kotlin
class Solution {
    fun numTilings(n: Int): Int {
        if (n <= 2) return n
        val mod = 1000000007
        val dp = IntArray(n+1)
        dp[0] = 1   // correction value for iteration
        dp[1] = 1   // shape only vertical pair
        dp[2] = 2   // shape ( vertical, horizontal pair )
        for(i in 3..n) {
            /* 
                assume n'th shape.
                (1) (n-1)'th + |
                (2) (n-2)'th + =
                (3) iterate range of 0 ~ n-3
                    - adding tromino & domino(0 or upper)
                    - which has tromino pair can be reversed.
             */
            dp[i] = (dp[i] + dp[i-1]) % mod
            dp[i] = (dp[i] + dp[i-2]) % mod
            for (j in 0..i-3) {
                dp[i] = (dp[i] + dp[j]) % mod   // correct pair
                dp[i] = (dp[i] + dp[j]) % mod   // reversed pair
            }
        }
        return dp[n]
    }
}
```

---


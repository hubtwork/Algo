## LeetCode Problems



#### 926. Flip String to Monotone Increasing

- **link**  [926. Flip String to Monotone Increasing](https://leetcode.com/problems/flip-string-to-monotone-increasing/)

- **lang**  `kotlin` 
- **tags** `String` `DP`

```kotlin
import kotlin.math.min
class Solution {
    fun minFlipsMonoIncr(s: String): Int {
        var result = s.length
        var zeroCount = 0
        var oneCount = 0
        // count all 0 in given string
        for (i in 0 until s.length) if (s[i] == '0') zeroCount++
        // iterate
        for (i in 0 until s.length) {
            // rest 0 count after current cursor
            if (s[i] == '0') zeroCount--
            // current cursor's best-flip : flip all passed-1 to 0 and all rest-0 to 1
            // best flip-count is minimum of (rest-0 + passed-1)
            result = min(result, oneCount + zeroCount)
            // passed 1 count before next cursor
            if (s[i] == '1') oneCount++
        }
        return result
    }
}
```

---


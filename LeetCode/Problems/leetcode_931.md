## LeetCode Problems



#### 931. Minimum Falling Path Sum

- **link**  [931. Minimum Falling Path Sum](https://leetcode.com/problems/minimum-falling-path-sum/description/)

- **lang**  `kotlin` 
- **tags** `Array` `DP` `Matrix`

```kotlin
import kotlin.math.min
class Solution {
    fun minFallingPathSum(matrix: Array<IntArray>): Int {
        var result = Integer.MAX_VALUE
        // topDp is dp table of before-row
        val width = matrix[0].size
        var topDp = IntArray(width)
        // traverse
        for (row in 0..matrix.size-1) {
            val currentDp = IntArray(width)
            for (col in 0..width - 1) {
                // get minimum sum for correct path.
                // ## avoid logic : if width == 1, summation will be constructed with one path.
                currentDp[col] = matrix[row][col] + when {
                    width == 1 -> topDp[0]
                    col == 0 -> min(topDp[0], topDp[1])
                    col == width-1 -> min(topDp[width-2], topDp[width-1])
                    else -> min(topDp[col-1], min(topDp[col], topDp[col+1]))
                }
                if (row == matrix.size-1) result = min(result, currentDp[col])
            }
            // refresh topDp for next step's calculations
            topDp = currentDp
        }
        return result
    }
}
```

---


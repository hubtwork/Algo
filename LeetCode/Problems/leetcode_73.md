## LeetCode Problems



#### 73. Set Matrix Zeroes

- **link**  [73. Set Matrix Zeroes](https://leetcode.com/problems/set-matrix-zeroes/description/)

- **lang**  `kotlin` 
- **tags**  `Array` `Hash Table` `Matrix`

```kotlin
class Solution {
    fun setZeroes(matrix: Array<IntArray>): Unit {
        val m = matrix.size
        val n = matrix[0].size
        var col_0 = 1
        /*
            Mark each row's and col's to-be-changed state at first. ( top-down )
            # mark using first row / col
            * but first col can be none-0, so manage separately is it to-be-changed state.
        */
        for(i in 0 until m) {
            if (matrix[i][0] == 0) col_0 = 0
            for (j in 1 until n) {
                if (matrix[i][j] == 0) {
                    matrix[i][0] = 0
                    matrix[0][j] = 0
                }
            }
        }
        // reflect mark state ( bottom-up )
        // # to restore first col state at each loop's last.
        for(i in m-1 downTo 0) {
            for(j in n-1 downTo 1) {
                if (matrix[i][0] == 0 || matrix[0][j] == 0) matrix[i][j] = 0
            }
            if (col_0 == 0) matrix[i][0] = 0
        }
    }
}
```

---


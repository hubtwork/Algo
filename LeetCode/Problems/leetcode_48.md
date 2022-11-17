## LeetCode Problems



#### 48. Rotate Image

- **link**  [48. Rotate Image](https://leetcode.com/problems/rotate-image/)

- **lang**  `kotlin` 
- **tags**  `Math` `Array` `Matrix`

```kotlin
class Solution {
    fun rotate(matrix: Array<IntArray>): Unit {
        // step 1. transpose matrix
        for(y in 0..matrix.size-1) {
            for (x in y+1..matrix[0].size-1) {
                val temp = matrix[x][y]
                matrix[x][y] = matrix[y][x]
                matrix[y][x] = temp
            }
        }
        // step 2. reverse each row
        val size = matrix.size
        for (row in 0..size-1) {
            for (i in 0..size/2-1) {
                val temp = matrix[row][size-1-i]
                matrix[row][size-1-i] = matrix[row][i]
                matrix[row][i] = temp
            }
        }
    }
}
```

---


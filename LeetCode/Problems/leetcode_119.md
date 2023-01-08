## LeetCode Problems



#### 119. Pascal's Triangle II

- **link**  [119. Pascal's Triangle II](https://leetcode.com/problems/pascals-triangle-ii/)

- **lang**  `kotlin` 
- **tags**  `Array` `DP`

```kotlin
class Solution {
    fun getRow(rowIndex: Int): List<Int> {
        val triangle = mutableListOf<List<Int>>()
        // build pascal triangle's each rows.
        for (i in 0..rowIndex) {
            val row = mutableListOf<Int>()
            for (j in 0..i) {
                if (j == 0 || j == i) row.add(1)
                else row.add(triangle[i-1][j-1] + triangle[i-1][j])
            }
            // if current row's index is given index, return row
            if (i == rowIndex) return row
            triangle.add(row)
        }
        return triangle.last()
    }
}
```

---


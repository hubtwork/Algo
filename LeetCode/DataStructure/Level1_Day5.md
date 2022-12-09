## LeetCode DataStructure StudyPlan

<img src="../../assets/leetcode_ds_lv1_day5.png" alt="leetcode_data_structure_level1_day5" style="zoom:50%;" />

### Day 5

- [36. Valid Sudoku](https://leetcode.com/problems/valid-sudoku/?envType=study-plan&id=data-structure-i)
- [74. Search a 2D Matrix](https://leetcode.com/problems/search-a-2d-matrix/?envType=study-plan&id=data-structure-i)

---

#### 36. Valid Sudoku

- **lang**  `kotlin` 
- **tags**  `Array` `Matrix` `Hash Table`

```kotlin
class Solution {
    fun isValidSudoku(board: Array<CharArray>): Boolean {
        val checkSet = mutableSetOf<String>()
        // traverse
        board.forEachIndexed { row, rowData ->
            rowData.forEachIndexed { col, value ->
                // if is treatable number
                if (value != '.') {
                    /*
                        it's difficult to distinguish each rule, so build as string.
                        (1) no same value in row
                        (2) no same value in col
                        (3) no same value in box ( rowNum, colNum )
                     */
                    if (
                        !checkSet.add("$value/row/$row") ||
                        !checkSet.add("$value/col/$col") ||
                        !checkSet.add("$value/box/${row/3},${col/3}")
                    ) return false
                }
            }
        }
        return true
    }
}
```

---

#### 74. Search a 2D Matrix

- **lang**  `kotlin` 
- **tags**  `Array` `Matrix` `Binary Search`

```kotlin
class Solution {
    fun searchMatrix(matrix: Array<IntArray>, target: Int): Boolean {
        // initialize variables
        val m = matrix.size
        val n = matrix[0].size
        var l = 0
        var r = m-1
        // seek target row to find which row is possible to have target number ( binary search )
        while (l <= r) {
            val mid = (l + r)/2
            // find row1.end < target < row2.end (l)
            when {
                matrix[mid][n - 1] == target -> return true
                matrix[mid][n - 1] < target -> l = mid + 1
                matrix[mid][n - 1] > target -> r = mid - 1
            }
        }
        // if target row is bigger than size, return false
        if (l >= m) return false
        // find target number in target row with binary search
        val targetRow: Int = l
        l = 0
        r = n - 1
        while (l <= r) {
            val mid = (l + r)/2
            when {
                matrix[targetRow][mid] == target -> return true
                matrix[targetRow][mid] < target -> l = mid + 1
                matrix[targetRow][mid] > target -> r = mid - 1
            }
        }
        return false
    }
}
```

---


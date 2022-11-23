## LeetCode Problems



#### 36. Valid Sudoku

- **link**  [36. Valid Sudoku](https://leetcode.com/problems/valid-sudoku/)

- **lang**  `kotlin` 
- **tags**  `Array` `Hash Table` `Matrix` 

```kotlin
class Solution {
    fun isValidSudoku(board: Array<CharArray>): Boolean {
        val set = mutableSetOf<String>()
        // traverse all value
        board.forEachIndexed { x, row ->
            row.forEachIndexed { y, value ->
                if (value != '.') {
                    /*
                        if current value is number, check rules for sudoku
                        (1) is it already in same row ?
                        (2) is it already in same col ?
                        (3) is it already in same box ?
                    */
                    if (
                        !set.add("$value row $y")
                        || !set.add("$value col $x")
                        || !set.add("$value box ${x/3}, ${y/3}")
                    ) return false
                }
            }
        }
        return true
    }
}
```

---


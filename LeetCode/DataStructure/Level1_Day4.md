## LeetCode DataStructure StudyPlan

<img src="../../assets/leetcode_ds_lv1_day4.png" alt="leetcode_data_structure_level1_day4" style="zoom:50%;" />

### Day 4

- [566. Reshape the Matrix](https://leetcode.com/problems/reshape-the-matrix/?envType=study-plan&id=data-structure-i)
- [118. Pascal's Triangle](https://leetcode.com/problems/pascals-triangle/?envType=study-plan&id=data-structure-i)

---

#### 566. Reshape the Matrix

- **lang**  `kotlin` 
- **tags**  `Array` `Matrix` `Simulation`

```kotlin
class Solution {
    fun matrixReshape(mat: Array<IntArray>, r: Int, c: Int): Array<IntArray> {
        // if given matrix is nonshapeable, return itself
        if (mat.size * mat[0].size != r * c) return mat
        // setup base tracking variables
        var row = 0
        var column = 0
        var result = arrayOf<IntArray>()
        for(i in 1..r) result += IntArray(c)
        // traverse
        mat.forEach { matRow ->
            matRow.forEach { value ->
                // set current value as transformed location
                result[row][column] = value
                // if reached to each columns' end, change row.
                if (++column == c) {
                    row ++
                    column = 0
                }
            }
        }
        return result
    }
}
```

---

#### 118. Pascal's Triangle

- **lang**  `kotlin` 
- **tags**  `Array` `DP` 

```kotlin
class Solution {
    fun generate(numRows: Int): List<List<Int>> {
        // root container
        val container = mutableListOf<List<Int>>()
        /*
            memorize each before step's row, and create now step's row.
            (1) if it's edge, filled with 1
            (2) else, filled with sum of before's nearest 2.
            (3) add now to container, and renew before with now
         */
        var up: List<Int> = listOf(1)
        for (i in 1..numRows-1) {
            val now = mutableListOf<Int>()
            for (n in 0..i) {
                // (1) and (2)
                if (n == 0 || n == i) now.add(1)
                else now.add(up[n-1] + up[n])
            }
            // (3)
            container.add(up)
            up = now
        }
        container.add(up)
        return container
    }
}
```

---


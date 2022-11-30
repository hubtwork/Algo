## LeetCode ProgrammingSkills StudyPlan

<img src="../../assets/leetcode_program_lv1_da7.png" alt="leetcode_programming_skills_level1_day7" style="zoom:50%;" />

### Day 7

- [1572. Matrix Diagonal Sum](https://leetcode.com/problems/matrix-diagonal-sum/?envType=study-plan&id=programming-skills-i)
- [566. Reshape the Matrix](https://leetcode.com/problems/reshape-the-matrix/?envType=study-plan&id=programming-skills-i)

---

#### 1572. Matrix Diagonal Sum

- **lang**  `kotlin` 
- **tags**  `Array` `Matrix`

```kotlin
class Solution {
    fun diagonalSum(mat: Array<IntArray>): Int {
        var result = 0
        val len = mat.size
        // loop
        for (i in 0..len/2-1) {
            // add each 4-direction's element from edge to center
            result += (
                mat[i][i] + mat[i][len-1-i] + mat[len-1-i][len-1-i] + mat[len-1-i][i]
            )
        }
        // if length is odd number, add center element
        return if (len % 2 == 1) result + mat[len/2][len/2] else result
    }
}
```

---


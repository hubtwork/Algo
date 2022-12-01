## LeetCode ProgrammingSkills StudyPlan

<img src="../../assets/leetcode_program_lv1_day9.png" alt="leetcode_programming_skills_level1_day9" style="zoom:50%;" />

### Day 9

- [709. To Lower Case](https://leetcode.com/problems/to-lower-case/?envType=study-plan&id=programming-skills-i)
- [1309. Decrypt String from Alphabet to Integer Mapping](https://leetcode.com/problems/decrypt-string-from-alphabet-to-integer-mapping/?envType=study-plan&id=programming-skills-i)
- [953. Verifying an Alien Dictionary](https://leetcode.com/problems/verifying-an-alien-dictionary/?envType=study-plan&id=programming-skills-i)

---

#### 709. To Lower Case

- **lang**  `kotlin` 
- **tags**  `String`

```kotlin
class Solution {
    fun toLowerCase(s: String): String {
        val arr = mutableListOf<Char>().apply {
            // in ascii - solution
            s.forEach { c ->
                add(if (c.toInt() in 65..90) (c+32).toChar() else c)
            }
        }
        return arr.joinToString("")
    }
}
```

---


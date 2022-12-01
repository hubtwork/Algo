## LeetCode ProgrammingSkills StudyPlan

<img src="../../assets/leetcode_program_lv1_day8.png" alt="leetcode_programming_skills_level1_day8" style="zoom:50%;" />

### Day 8

- [1768. Merge Strings Alternately](https://leetcode.com/problems/merge-strings-alternately/?envType=study-plan&id=programming-skills-i)
- [1678. Goal Parser Interpretation](https://leetcode.com/problems/goal-parser-interpretation/?envType=study-plan&id=programming-skills-i)
- [389. Find the Difference](https://leetcode.com/problems/find-the-difference/?envType=study-plan&id=programming-skills-i)

---

#### 1768. Merge Strings Alternately

- **lang**  `kotlin` 
- **tags**  `String` `Two Pointers`

```kotlin
import kotlin.math.max
class Solution {
    fun mergeAlternately(word1: String, word2: String): String {
        return word1 merge word2
    }
    // practice for infix
    infix fun String.merge(target: String): String {
        var result = mutableListOf<Char>()
        // pointer for each reader
        var (pointer1, pointer2) = 0 to 0
        while (pointer1 < length || pointer2 < target.length) {
            // get() not handle nullable, so use elementAtOrNull()
            elementAtOrNull(pointer1++)?.let { result.add(it) }
            target.elementAtOrNull(pointer2++)?.let { result.add(it) }
        }
        return result.joinToString("")
    }
}
```

---


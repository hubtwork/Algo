## LeetCode Algorithm StudyPlan

<img src="../../assets/leetcode_study_day4.png" alt="leetcode_study_day2" style="zoom:50%;" />

### Day 4

- [344. Reverse String](https://leetcode.com/problems/reverse-string/?envType=study-plan&id=algorithm-i)
- [557. Reverse Words in a String III](https://leetcode.com/problems/reverse-words-in-a-string-iii/?envType=study-plan&id=algorithm-i)

---

#### 344. Reverse String

- **lang**  `kotlin` 
- **tags**  `String`  `Two Pointers`

```kotlin
class Solution {
    fun reverseString(s: CharArray): Unit {
        s.reverseStringPrimitive()
    }
  	// with kotlin native - built in function
    fun CharArray.reverseStringBuiltIn() {
        reverse()
    }
  	// with traditional way with primitive Two Pointer
    fun CharArray.reverseStringPrimitive() {
        var cursor = 0
        val mid = this.size / 2
        while (cursor < mid) {
            val temp = this[this.size-1-cursor]
            this[this.size-1-cursor] = this[cursor]
            this[cursor++] = temp
        }
    }
}
```

---


## LeetCode Algorithm StudyPlan

<img src="../../assets/leetcode_study_day6.png" alt="leetcode_study_day2" style="zoom:50%;" />

### Day 6

- [3. Longest Substring Without Repeating](https://leetcode.com/problems/longest-substring-without-repeating-characters/?envType=study-plan&id=algorithm-i)
- [567. Permutation in String](https://leetcode.com/problems/permutation-in-string/?envType=study-plan&id=algorithm-i)

---

#### 3. Longest Substring Without Repeating

- **lang**  `kotlin` 
- **tags**  `Hash Table`  `String` `Sliding Window`

```kotlin
class Solution {
    fun lengthOfLongestSubstring(s: String): Int {
        /*
            means length of [last ch ~ current ch]
            so renew area each indexes
        */
        val characterPosition = mutableMapOf<Char, Int>()
        var maxLength = 0
        var start = 0
        s.forEachIndexed { pos, ch ->
            // start = max ( origin start, character last occurrance )
            start = Math.max(start, characterPosition[ch] ?: 0)
            // maxLength = max ( origin max length, current pointer length )
            maxLength = Math.max(maxLength, pos-start+1)
            // renew current character's position
            characterPosition[ch] = 1 + pos
        }
        return maxLength
    }
}
```

---


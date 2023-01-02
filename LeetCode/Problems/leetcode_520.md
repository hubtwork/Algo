## LeetCode Problems



#### 520. Detect Capital

- **link**  [520. Detect Capital](https://leetcode.com/problems/detect-capital/)

- **lang**  `kotlin` 
- **tags** `String`

```kotlin
class Solution {
    fun detectCapitalUse(word: String): Boolean {
        // Capital must be on leading positions.
        var count = 0
        for (i in 0..word.length-1) {
            // count all of upper-case ( check by ascii-calculation )
            if (word[i].toInt() - 97 < 0) {
                count++
                // if upper-count != index+1, it means have lower-case is between uppers.
                if (count != i+1) return false
            }
        }
        // return if "word" is case 1 or 2 or 3
        return count == word.length || count == 0 || count == 1
    }
}
```

---


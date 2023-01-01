## LeetCode Problems



#### 290. Word Pattern

- **link**  [290. Word Pattern](https://leetcode.com/problems/word-pattern/description/)

- **lang**  `kotlin` 
- **tags**  `Hash Table` `String`

```kotlin
class Solution {
    fun wordPattern(pattern: String, s: String): Boolean {
        // hash-map for pattern check, set for word check.
        val map = mutableMapOf<Char, String>()
        val registered = mutableSetOf<String>()
        val words = s.split(" ")
        // if word count not same with pattern count, return false.
        if (pattern.length != words.size) return false
        // iterate all given words.
        words.forEachIndexed { idx, word ->
            /*
                if there is word registered in current pattern, check is same with word.
                else register the word to pattern.
             */
            map[pattern[idx]]
                ?.let { if (it != word) return false }
                ?:run { 
                    if (!registered.add(word)) return false
                    map[pattern[idx]] = word
                }
        }
        return true
    }
}
```

---


## LeetCode Problems



#### 438. Find All Anagrams in a String

- **link**  [438. Find All Anagrams in a String](https://leetcode.com/problems/find-all-anagrams-in-a-string/)

- **lang**  `kotlin` 
- **tags** `HashTable` `String` `Sliding Window`

```kotlin
class Solution {
    fun findAnagrams(s: String, p: String): List<Int> {
        // if original string is longer than to-calculate-string, return empty
        if (s.length < p.length) return listOf()
        // build original-window
        val len = p.length
        val result = mutableListOf<Int>()
        var zeroCounter = 26
        val window = IntArray(26)
        for (i in 0 until len) {
            window.whatIf(p[i] - 'a', true, { zeroCounter++ }, { zeroCounter-- })
            window.whatIf(s[i] - 'a', false, { zeroCounter++ }, { zeroCounter-- })
        }
        // if first window-area is anagram, add to result
        if (zeroCounter == 26) result.add(0) 
        // iterate
        for( i in len until s.length ) {
            window.whatIf(s[i - len] - 'a', true, { zeroCounter++ }, { zeroCounter-- })
            window.whatIf(s[i] - 'a', false, { zeroCounter++ }, { zeroCounter-- })
            // after window moving ) if evaluation fufilled, add to result.
            if (zeroCounter == 26) result.add(i - len + 1)
        }
        return result
    }
    // syntactic sugar for zero-count-correction
    private fun IntArray.whatIf(
        index: Int,
        add: Boolean,
        ifZero: () -> Unit,
        ifEscapeZero: () -> Unit
    ) {
        if (index >= this.size) return
        if (this[index] == 0) ifEscapeZero()
        if (add) this[index] ++ else this[index] --
        if (this[index] == 0) ifZero()
    }
}
```

---


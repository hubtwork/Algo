## LeetCode Problems



#### 567. Permutation in String

- **link**  [567. Permutation in String](https://leetcode.com/problems/permutation-in-string/)

- **lang**  `kotlin` 
- **tags** `String` `Sliding Window`

```kotlin
class Solution {
    fun checkInclusion(s1: String, s2: String): Boolean {
        if (s1.length > s2.length) return false
        // build counter
        val len = s1.length
        var zeroCounter = 26
        val window = IntArray(26)
        for (i in 0 until s1.length) {
            window.whatIf(s1[i] - 'a', true, { zeroCounter++ }, { zeroCounter-- })
            window.whatIf(s2[i] - 'a', false, { zeroCounter++ }, { zeroCounter-- })
        }
        if (zeroCounter == 26) return true
        // sliding window
        for (i in len until s2.length) {
            window.whatIf(s2[i - len] - 'a', true, { zeroCounter++ }, { zeroCounter-- })
            window.whatIf(s2[i] - 'a', false, { zeroCounter++ }, { zeroCounter-- })
            if (zeroCounter == 26) return true
        }
        return false
    }
    // syntactic sugar for counting zero easily
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


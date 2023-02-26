## LeetCode Problems



#### 72. Edit Distance

- **link**  [72. Edit Distance](https://leetcode.com/problems/edit-distance/)

- **lang**  `kotlin` 
- **tags**  `String` `DP`

```kotlin
import kotlin.math.max
import kotlin.math.min
class Solution {
    fun minDistance(word1: String, word2: String): Int {
        if (word1.isEmpty()) return word2.length
        if (word2.isEmpty()) return word1.length
        // memoize array for minimum Distance of each position
        val mem = Array(word1.length + 1, { IntArray(word2.length + 1) })
        return find(word1, word2, mem, 0, 0)
    }

    private fun find(word1: String, word2: String, mem: Array<IntArray>, _r1: Int, _r2: Int): Int {
        // already passed
        if (mem[_r1][_r2] != 0) return mem[_r1][_r2]
        // find first-unmatched index
        var r1 = _r1
        var r2 = _r2
        while (r1 < word1.length && r2 < word2.length) {
            if (word1[r1] != word2[r2]) break
            r1 ++
            r2 ++
        }
        // if one reached at last index, return 
        if (r1 == word1.length || r2 == word2.length) return max(word1.length - r1, word2.length - r2)
        // find from insert, delete, replace position
        val minIns = find(word1, word2, mem, r1, r2 + 1)
        val minDel = find(word1, word2, mem, r1 + 1, r2) 
        val minRep = find(word1, word2, mem, r1 + 1, r2 + 1)
        // get best minimum distance
        val bestMin = getMin(minIns, minDel, minRep)
        mem[r1][r2] = bestMin + 1
        return mem[r1][r2]
    }
    // utilize function for get minimum value from iterable Int.
    private fun getMin(vararg num: Int): Int {
        var min = Integer.MAX_VALUE
        for (i in num) { if (i < min) min = i }
        return min
    }
}
```

---


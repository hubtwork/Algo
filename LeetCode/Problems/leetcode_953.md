## LeetCode Problems



#### 953. Verifying an Alien Dictionary

- **link**  [953. Verifying an Alien Dictionary](https://leetcode.com/problems/verifying-an-alien-dictionary/)

- **lang**  `kotlin` 
- **tags** `Array` `Hash Table` `String`

```kotlin
import kotlin.math.min
class Solution {
    fun isAlienSorted(words: Array<String>, order: String): Boolean {
        val map = mutableMapOf<Char, Int>()
        order.forEachIndexed { idx, ch -> map[ch] = idx }
        // compare one by one ( brute-force consuming )
        for (i in 1 until words.size) {
            val prev = words[i-1]
            val curr = words[i]
            val shortLength = min(prev.length, curr.length)
            // compare one by one on same character-position
            for (cursor in 0 until shortLength) {
                val prevCursor = map[prev[cursor]]!!
                val currCursor = map[curr[cursor]]!!
                // if character dict-order is decreasing, return false
                // if cursor is on short's last but prev's length is bigger, return false
                // if iterate ended but prev is shorter than current, stop iterate.
                if (prevCursor > currCursor) return false
                else if (cursor == shortLength-1 && prevCursor == currCursor && prev.length > curr.length) return false
                else if (prevCursor < currCursor) break
            }
        }
        return true
    }
}
```

---


## LeetCode Problems



#### 6. Zigzag Conversion

- **link**  [6. Zigzag Conversion](https://leetcode.com/problems/zigzag-conversion/)

- **lang**  `kotlin` 
- **tags**  `String` 

```kotlin
class Solution {
    fun convert(s: String, numRows: Int): String {
        if (numRows == 1) return s
        // jumpSize means each Zigzag loop-gap
        val len = s.length
        var jumpSize = 2 * (numRows - 1)
        val answer = CharArray(len)
        // answer Index
        var index = 0
        // iterate
        for (i in 0 until numRows) {
            var cursor = i
            if (i == 0 || i == numRows - 1) {
                // if first or last row, get each ziazag loop's seil and floor
                while (cursor < len) {
                    answer[index++] = s[cursor]
                    cursor += jumpSize
                }
            } else {
                // marker for next-loop-seil
                var time = jumpSize
                while (cursor < len) {
                    answer[index++] = s[cursor]
                    // current row's trail number's index is (next-loop-seil - rowNumber)
                    val trail = time - i
                    // if trail index is in given string, add to answer
                    if (trail < len) answer[index++] = s[trail]
                    cursor += jumpSize
                    time += jumpSize
                }
            }
        }
        return String(answer)
    }
}
```

---


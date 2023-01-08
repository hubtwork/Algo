## LeetCode Problems



#### 58. Length of Last Word

- **link**  [58. Length of Last Word](https://leetcode.com/problems/length-of-last-word/)

- **lang**  `kotlin` 
- **tags**  `String`

```kotlin
class Solution {
    fun lengthOfLastWord(s: String): Int {
        // just check last word (characters between white-spaces)
        var lastWordCount = 0
        var isStart = true
        // iterate
        s.forEach { c -> 
            // if white-space, turn-on flag.
            if (c == ' ') isStart = true
            else {
                // if flag is on, reset wordCount
                if (isStart) {
                    lastWordCount = 1
                    isStart = false
                } else lastWordCount++
            }
        }
        return lastWordCount
    }
}
```

---


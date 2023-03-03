## LeetCode Problems



#### 28. Find the Index of the First Occurrence in a String

- **link**  [28. Find the Index of the First Occurrence in a String](https://leetcode.com/problems/find-the-index-of-the-first-occurrence-in-a-string/description/)

- **lang**  `kotlin` 
- **tags**  `Two Pointers` `String` `String Matching`

```kotlin
class Solution {
    fun strStr(haystack: String, needle: String): Int {
        // block edge case.
        if (needle.length > haystack.length) return -1
        var cursor = 0
        var count = 0
        // iterate
        for (i in 0 until haystack.length) {
            // cond 1) find needle-posible position ( starting matcher )
            // cond 2) do not reach to needle's length - IndexOutOfRange
            if (
                haystack[i] == needle[0] && 
                needle.length <= haystack.length - i
            ) {
                // start with cursor pointer
                cursor = i
                // check match stacks from needle
                for (c in needle) {
                    if (haystack[cursor ++] != c) break
                    count ++
                }
                // if acquire, return starting point
                if (count == needle.length) return i
            }
            count = 0
        }
        return -1
    }
}
```

---


## LeetCode Problems



#### 1704. Determine if String Halves Are Alike

- **link**  [1704. Determine if String Halves Are Alike](https://leetcode.com/problems/determine-if-string-halves-are-alike/)

- **lang**  `kotlin` 
- **tags**  `String` `Counting`

```kotlin
class Solution {
    fun halvesAreAlike(s: String): Boolean {
        var count = 0
        // optimize with using half
        /*
            if back-half has more vowel, it'll not traverse all.
            but if using two pointer, it have to traversel all.
        */
        val half = s.length/2
        // traverse
        for (i in 0..s.length-1) {
            if (s[i].isVowel()) {
                // add break during traverse back-half side.
                if (i < half) count++
                else if (count-- == 0) return false
            }
        }
        return count == 0
    }
    // func for check if it is vowel
    fun Char.isVowel(): Boolean {
        return this == 'a' || this == 'A' ||
        this == 'e' || this == 'E' ||
        this == 'i' || this == 'I' ||
        this == 'o' || this == 'O' ||
        this == 'u' || this == 'U'
    }
}
```

---


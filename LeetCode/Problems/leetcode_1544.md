## LeetCode Problems



#### 1544. Make The String Great

- **link**  [1544. Make The String Great](https://leetcode.com/problems/make-the-string-great/)

- **lang**  `kotlin` 
- **tags**  `String` `Stack` 

```kotlin
class Solution {
    fun makeGood(s: String): String {
        return withList(s)
    }
    fun withList(s: String): String {
        return mutableListOf<Char>().apply {
            s.forEach { c ->
                if (isNotEmpty() && last() sameWith c) removeAt(size - 1)
                else add(c)
            }
        }.joinToString("")
    }
    infix fun Char.sameWith(c: Char): Boolean {
        // alphabet upper / lower 's ascii gap is 32
        return Math.abs(this - c) == 32
    }
}
```

---


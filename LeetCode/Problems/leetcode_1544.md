## LeetCode Problems



#### 1544. Make The String Great

- **link**  [1544. Make The String Great](https://leetcode.com/problems/make-the-string-great/)

- **lang**  `kotlin` 
- **tags**  `String` `Stack` 

```kotlin
class Solution {
    fun makeGood(s: String): String {
        return withStack(s)
    }
    fun withStack(s: String): String {
        return Stack<Char>().apply {
            s.forEach { c ->
                if (isNotEmpty() && peek() adjacentWith c) pop()
                else push(c)
            }
        }.joinToString("")
    }
    fun withList(s: String): String {
        return mutableListOf<Char>().apply {
            s.forEach { c ->
                if (isNotEmpty() && last() adjacentWith c) removeAt(size - 1)
                else add(c)
            }
        }.joinToString("")
    }
    infix fun Char.adjacentWith(c: Char): Boolean {
        // alphabet upper / lower 's ascii gap is 32
        return Math.abs(this - c) == 32
    }
}
```

---


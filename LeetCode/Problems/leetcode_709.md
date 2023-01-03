## LeetCode Problems



#### 709. To Lower Case

- **link**  [709. To Lower Case](https://leetcode.com/problems/to-lower-case/)

- **lang**  `kotlin` 
- **tags**  `String`

```kotlin
class Solution {
    fun toLowerCase(s: String): String {
        // return s.toLowerCase()
        val ca = s.toCharArray()
        // iterate
        for (i in 0..ca.size-1) {
            // check using Range ext.
            if (('A'..'Z').contains(ca[i])) ca[i] = ca[i] + 32
        }
        return String(ca)
    }
}
```

---


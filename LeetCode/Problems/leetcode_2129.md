## LeetCode Problems



#### 2129. Capitalize the Title

- **link**  [2129. Capitalize the Title](https://leetcode.com/problems/capitalize-the-title/)

- **lang**  `kotlin` 
- **tags** `String`

```kotlin
class Solution {
    fun capitalizeTitle(title: String): String {
        return title.split(" ").map { word ->
            // parse word to lowercase
            val lower = word.toLowerCase()
            if (lower.length <= 2) lower
            else {
                // if it has more than 2 characters, capitalize.
                val arr = lower.toCharArray()
                arr[0] = arr[0] - 32
                String(arr)
            } 
        }.joinToString(" ")
    }
}
```

---


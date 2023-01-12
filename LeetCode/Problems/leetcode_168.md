## LeetCode Problems



#### 168. Excel Sheet Column Title

- **link**  [168. Excel Sheet Column Title](https://leetcode.com/problems/excel-sheet-column-title/)

- **lang**  `kotlin` 
- **tags**  `Math` `String`

```kotlin
class Solution {
    fun convertToTitle(columnNumber: Int): String {
        var result = ""
        var sheet = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
        var n = columnNumber
        // iterate
        while (n > 0) {
            // get column title by (n-1)%26
            // reason : A = 1 , so to match A = 0
            result = sheet[--n%26] + result
            n /= 26
        }
        return result
    }
}
```

---


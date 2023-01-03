## LeetCode Problems



#### 944. Delete Columns to Make Sorted

- **link**  [944. Delete Columns to Make Sorted](https://leetcode.com/problems/delete-columns-to-make-sorted/)

- **lang**  `kotlin` 
- **tags** `String` `Array`

```kotlin
class Solution {
    fun minDeletionSize(strs: Array<String>): Int {
        var count = 0
        // to avoid useless memory-usage in nested loop. 
        val wordCount = strs.size-1
        // iterate
        for (i in 0..strs[0].length-1) {
            // check each column
            for (c in 1..wordCount) {
                // if not lexicographical, increment to-delete-count
                if (strs[c][i] < strs[c-1][i]) {
                    count++
                    break
                }
            }
        }
        return count
    }
}
```

---


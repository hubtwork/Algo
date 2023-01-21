## LeetCode Problems



#### 93. Restore IP Addresses

- **link**  [93. Restore IP Addresses](https://leetcode.com/problems/restore-ip-addresses/)

- **lang**  `kotlin` 
- **tags**  `String` `Back Tracking` 

```kotlin
class Solution {
    fun restoreIpAddresses(s: String): List<String> {
        val bucket = mutableSetOf<String>()
        seek(bucket, listOf(), 0, s)
        return bucket.toList()
    }
    fun seek(bucket: MutableSet<String>, holder: List<Int>, current: Int, s: String) {
        if (holder.size == 4) {
            if (current == s.length) bucket.add(holder.joinToString("."))
            else return
        }
        var idx = current
        var cString = ""
        var consume = 0
        while (idx < s.length) {
            cString += s[idx]
            consume = cString.toInt()
            if (consume > 255) break
            seek(bucket, holder + listOf(consume), idx++ + 1, s)
            if (consume == 0) break
        }
    }
}
```

---


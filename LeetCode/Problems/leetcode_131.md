## LeetCode Problems



#### 131. Palindrome Partitioning

- **link**  [131. Palindrome Partitioning](https://leetcode.com/problems/palindrome-partitioning/)

- **lang**  `kotlin` 
- **tags**  `String` `DP` `Back Tracking`

```kotlin
class Solution {
    fun partition(s: String): List<List<String>> {
        val bucket = mutableListOf<List<String>>()
        seek(bucket, listOf(), 0, s)
        return bucket
    }
    fun seek(bucket: MutableList<List<String>>, holder: List<String>, currentIdx: Int, s: String) {
        if (currentIdx == s.length) {
            bucket.add(holder)
            return
        }
        var temp = ""
        // iterate
        for (idx in currentIdx until s.length) {
            // find all possible-pelindromes start from given idx to string's length
            temp += s[idx]
            if (temp.isPelindrome()) seek(bucket, holder + listOf(temp), idx + 1, s)
        }
    }
    // pelindrome check-util
    fun String.isPelindrome(): Boolean {
        if (length == 1) return true
        // use two-pointer for check 
        var l = 0
        var r = length-1
        while (l < r) if (this[l++] != this[r--]) return false
        return true
    }
}
```

---


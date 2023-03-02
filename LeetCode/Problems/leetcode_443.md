## LeetCode Problems



#### 443. String Compression

- **link**  [443. String Compression](https://leetcode.com/problems/string-compression/)

- **lang**  `kotlin` 
- **tags** `Two Pointers` `String` 

```kotlin
class Solution {
    fun compress(chars: CharArray): Int {
        var write = 0	// write cursor
        var count = 0
      	// iterate with read cursor
        for (read in 0 until chars.size) {
            count ++
          	// if read cursor is end of given charArray or value-changing edge
            if (read == chars.size - 1 || chars[read] != chars[read + 1]) {
              	// write cursor with read data
                chars[write ++] = chars[read]
                if (count != 1) "$count".forEach { chars[write ++] = it }
                count = 0
            }
        }
        return write
    }
}
```

---


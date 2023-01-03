## LeetCode Problems



#### 69. Sqrt(x)

- **link**  [69. Sqrt(x)](https://leetcode.com/problems/sqrtx/description/)

- **lang**  `kotlin` 
- **tags**  `Math` `Binary Search` 

```kotlin
class Solution {
    fun mySqrt(x: Int): Int {
        // filter edge-cases.
        if (x <= 1) return x
        // do binary search.
        var l = 1
        var r = x
        while (l <= r) {
            val mid = (l + r) / 2
            /*
                if x / mid => mid : answer
                else if x / mid < mid => search l-side.
                else => search r-side.
             */
            when {
                x / mid == mid -> return mid
                x / mid < mid -> r = mid - 1
                else -> l = mid + 1
            }
        }
        return l - 1
    }
}
```

---


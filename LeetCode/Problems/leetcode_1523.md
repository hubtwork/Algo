## LeetCode Problems



#### 1523. Count Odd Numbers in an Interval Range

- **link**  [1523. Count Odd Numbers in an Interval Range](https://leetcode.com/problems/count-odd-numbers-in-an-interval-range/)

- **lang**  `kotlin` 
- **tags**  `Math` 

```kotlin
class Solution {
    fun countOdds(low: Int, high: Int): Int {
        // basically, odd numbers in range is (n2 - n1) / 2.
        // but if n1 or n2 is odd, have to count inclusive.
        return (high - low) / 2  + if (high % 2 == 1 || low % 2 == 1) 1 else 0
    }
}
```

---


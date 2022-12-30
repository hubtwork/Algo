## LeetCode Problems



#### 66. Plus One

- **link**  [66. Plus One](https://leetcode.com/problems/plus-one/description/)

- **lang**  `kotlin` 
- **tags**  `Math` `Array`

```kotlin
class Solution {
    fun plusOne(digits: IntArray): IntArray {
        // iterate reverse-order and check it.
        for (i in digits.size-1 downTo 0) {
            // if increased number is 10, assign it as 0.
            // else it means it's single-digit, so escape.
            if (++digits[i] == 10) digits[i] = 0
            else break
        }
        // if first one is 0, have to attach new 1 to front.
        return if (digits[0] == 0) intArrayOf(1) + digits else digits
    }
}
```

---


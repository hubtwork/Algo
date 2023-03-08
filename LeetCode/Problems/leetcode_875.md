## LeetCode Problems



#### 875. Koko Eating Bananas

- **link**  [875. Koko Eating Bananas](https://leetcode.com/problems/koko-eating-bananas/description/)

- **lang**  `kotlin` 
- **tags** `Array` `Binary Search`

```kotlin
import kotlin.math.ceil
class Solution {
    fun minEatingSpeed(piles: IntArray, h: Int): Int {
        var left = 1
        var right = 1000000000
        while (left <= right) {
            val mid = left + (right - left) / 2
            if (isValid(piles, h, mid)) right = mid - 1
            else left = mid + 1
        }
        return left
    }
    // validate given k is enough to consume all piles in h
    fun isValid(piles: IntArray, h: Int, k: Int): Boolean {
        var sum = 0
        for (pile in piles) {
            sum += ceil(pile.toDouble() / k).toInt()
            if (sum > h) return false
        }
        return true
    }
}
```

---


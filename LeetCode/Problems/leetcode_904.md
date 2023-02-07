## LeetCode Problems



#### 904. Fruit Into Baskets

- **link**  [904. Fruit Into Baskets](https://leetcode.com/problems/fruit-into-baskets/)

- **lang**  `kotlin` 
- **tags** `Array` `Hash Table` `Sliding Window`

```kotlin
import kotlin.math.max
class Solution {
    fun totalFruit(fruits: IntArray): Int {
        var answer = 0
        var map = mutableMapOf<Int, Int>()
        var prev = 0
        // iterate
        for (curr in 0 until fruits.size) {
            val fruit = fruits[curr]
            map[fruit] = (map[fruit] ?: 0) + 1
            // if bucket is full, move window-prev cursor to reduce bucket to size 2
            while (map.size > 2) {
                val prevFruit = fruits[prev]
                val prevCount = map[prevFruit]!!
                // remove one-by-one from prev
                if (prevCount > 1) map[prevFruit] = prevCount - 1
                else map.remove(prevFruit)
                prev ++
            }
            // refresh answer with current bucket's full count
            answer = max(answer, map.values.sum())
        }
        return answer
    }
}
```

---


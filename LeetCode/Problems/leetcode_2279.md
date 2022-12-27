## LeetCode Problems



#### 2279. Maximum Bags With Full Capacity of Rocks

- **link**  [2279. Maximum Bags With Full Capacity of Rocks](https://leetcode.com/problems/maximum-bags-with-full-capacity-of-rocks/description/)

- **lang**  `kotlin` 
- **tags**  `Array` `Greedy` `Sorting`

```kotlin
class Solution {
    fun maximumBags(capacity: IntArray, rocks: IntArray, additionalRocks: Int): Int {
        // check rest spaces of each bags
        val spaces = IntArray(capacity.size, { i -> capacity[i] - rocks[i] })
        // tracking rest rocks and counts of bag with full capacity.
        var restRocks = additionalRocks
        var count = 0
        // to get maximum bags, fill bags from small spaces to upper.
        spaces.sort()
        // iterate
        for (i in 0..spaces.size-1) {
            // if current bag is possible to be full, add count
            // else exit
            if (spaces[i] <= restRocks) {
                restRocks -= spaces[i]
                count ++
            } else break
        }
        return count
    }
}
```

---


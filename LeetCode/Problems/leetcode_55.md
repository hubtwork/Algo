## LeetCode Problems



#### 55. Jump Game

- **link**  [55. Jump Game](https://leetcode.com/problems/jump-game/description/)

- **lang**  `kotlin` 
- **tags**  `Array` `DP` `Greedy`

```kotlin
class Solution {
    fun canJump(nums: IntArray): Boolean {
        // tracker for checking can be reached.
        val arr = BooleanArray(nums.size)
        arr[0] = true
        // iterate
        nums.forEachIndexed { idx, jumpDistance ->
            // if can reached tile,
            if (arr[idx]) {
                // check reachable tiles.
                for (i in 1..jumpDistance) {
                    if (idx + i == nums.size) break
                    arr[idx + i] = true
                }
            }
        }
        return arr[nums.size-1]
    }
}
```

---


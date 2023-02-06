## LeetCode Problems



#### 1470. Shuffle the Array

- **link**  [1470. Shuffle the Array](https://leetcode.com/problems/shuffle-the-array/)

- **lang**  `kotlin` 
- **tags**  `Array`

```kotlin
class Solution {
    fun shuffle(nums: IntArray, n: Int): IntArray {
        // build new IntArray with given rule.
        return IntArray(nums.size, { idx -> if (idx % 2 == 0) nums[idx/2] else nums[nums.size/2 + idx/2] })
    }
}
```

---


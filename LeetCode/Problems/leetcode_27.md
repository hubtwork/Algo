## LeetCode Problems



#### 27. Remove Element

- **link**  [27. Remove Element](https://leetcode.com/problems/remove-element/)

- **lang**  `kotlin` 
- **tags**  `Array` `Two Pointers`

```kotlin
class Solution {
    fun removeElement(nums: IntArray, `val`: Int): Int {
        // using index marker + `val` count
        var mark = 0
        var count = 0
        // iterate
        for(i in 0..nums.size-1) {
            // if not `val`, assign value to mark index
            // else increase `val` count
            if (nums[i] != `val`) nums[mark++] = nums[i]
            else count++
        }
        // removed size is total - `val` count
        return nums.size-count
    }
}
```

---


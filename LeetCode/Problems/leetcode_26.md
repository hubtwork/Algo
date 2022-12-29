## LeetCode Problems



#### 26. Remove Duplicates from Sorted Array

- **link**  [26. Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)

- **lang**  `kotlin` 
- **tags**  `Array` `Two Pointers`

```kotlin
class Solution {
    fun removeDuplicates(nums: IntArray): Int {
        if (nums.size == 0) return 0
        // last number marker
        var marker = 0
        // iterate
        for (i in 0..nums.size-1) {
            // if faced new number, move current to next marker position.
            if (nums[i] != nums[marker]) nums[++marker] = nums[i]
        }
        // to return last, size is marker + 1
        return marker + 1
    }
}
```

---


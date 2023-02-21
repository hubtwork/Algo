## LeetCode Problems



#### 540. Single Element in a Sorted Array

- **link**  [540. Single Element in a Sorted Array](https://leetcode.com/problems/single-element-in-a-sorted-array/)

- **lang**  `kotlin` 
- **tags** `Array` `Binary Search`

```kotlin
class Solution {
    fun singleNonDuplicate(nums: IntArray): Int {
        var left = 0
        var right = nums.size / 2
        // binary search
        while (left < right) {
            // real idx is mul 2
            val mid = (left + right) / 2
            val idx = mid * 2
            // move
            when {
                nums[idx] == nums[idx+1] -> left = mid + 1
                else -> right = mid
            }
        }
        return nums[left * 2]
    }
}
```

---


## LeetCode Problems



#### 35. Search Insert Position

- **link**  [35. Search Insert Position](https://leetcode.com/problems/search-insert-position/)

- **lang**  `kotlin` 
- **tags**  `Array` `Binary Search`

```kotlin
class Solution {
    fun searchInsert(nums: IntArray, target: Int): Int {
        // prepare binary search
        var l = 0
        var r = nums.size - 1
        // execute search
        while (l <= r) {
            val mid = (l + r) / 2
            // conditional computation
            when {
                nums[mid] > target -> r = mid - 1
                nums[mid] < target -> l = mid + 1
                nums[mid] == target -> return mid
            }
        }
        // if find best-target, return it.
        return l
    }
}
```

---


## LeetCode Algorithm StudyPlan

### Day 1

- [704. Binary Search](https://leetcode.com/problems/binary-search/?envType=study-plan&id=algorithm-i)
- [278. First Bad Version](https://leetcode.com/problems/first-bad-version/?envType=study-plan&id=algorithm-i)
- [35. Search Insert Position](https://leetcode.com/problems/search-insert-position/?envType=study-plan&id=algorithm-i)

---

#### 704. Binary Search

- **lang**  `kotlin` 
- **tags**  `Binary Search`

```kotlin
class Solution {
  	// main function
    fun search(nums: IntArray, target: Int): Int {
        return binarySearch(nums, target, 0, nums.size)
    }
    // with recursive function
    fun binarySearch(nums: IntArray, target: Int, l: Int, r: Int): Int {
      	// if l pointer pass over r pointer, it means search failure
        if (l >= r) return -1
      	// get search pointer
        val mid = (l+r) / 2
        return when {
          	// move search scope to (middle ~ end) 
            nums[mid] < target -> binarySearch(nums, target, mid + 1, r)
          	// move search scope to (start ~ middle)
            nums[mid] > target -> binarySearch(nums, target, l, mid)
          	// search success
            else -> mid
        }
    }
}
```

---


## LeetCode Algorithm StudyPlan

<img src="/Users/alenheo/Desktop/repo/algo/assets/leetcode_study_day1.png" alt="leetcode_study_day1" style="zoom:50%;" />

### Day 2

- [977. Squares of a Sorted Array](https://leetcode.com/problems/squares-of-a-sorted-array/?envType=study-plan&id=algorithm-i)
- [189. Rotate Array](https://leetcode.com/problems/rotate-array/?envType=study-plan&id=algorithm-i)

---

#### 977. Squares of a Sorted Array

- **lang**  `kotlin` 
- **tags**  `Array` `Sort` `Two Pointer`

```kotlin
// Basic Solution with first pow all and sort array
class Solution {
    fun sortedSquares(nums: IntArray): IntArray {
        return nums.map { it * it }.sorted().toIntArray()
    }
}
```

```kotlin
// Time-C O(n) Solution with additional array + Two Pointer
class Solution {
    fun sortedSquares(nums: IntArray): IntArray {
        var arr = IntArray(nums.size)
        var l = 0
        var r = nums.size - 1
        var i = nums.size
        while ( i-- > 0) {
            if (Math.abs(nums[l]) < Math.abs(nums[r])) arr.set(i, nums[r] * nums[r--])
            else arr.set(i, nums[l] * nums[l++])
        }
        return arr
    }
}
```

---

#### 189. Rotate Array

- **lang**  `kotlin` 
- **tags**  `Array` `Sort` `Two Pointer`

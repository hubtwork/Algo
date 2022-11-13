## LeetCode Algorithm StudyPlan

<img src="/Users/alenheo/Desktop/repo/algo/assets/leetcode_study_day3.png" alt="leetcode_study_day2" style="zoom:50%;" />

### Day 3

- [283. Move Zeroes](https://leetcode.com/problems/move-zeroes/?envType=study-plan&id=algorithm-i)
- [167. Two Sum II - Input Array Is Sorted](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/?envType=study-plan&id=algorithm-i)

---

#### 283. Move Zeroes

- **lang**  `kotlin` 
- **tags**  `Array`  `Two Pointer`

```kotlin
class Solution {
    fun moveZeroes(nums: IntArray): Unit {
        // pointer indicates zero
        var zero = 0
        // seek which is non-zero
        for(nonZero in 0..nums.size-1) {
            // if it's non-zero, swap and move last zero pointer
            if (nums[nonZero] != 0) {
                // avoid worst case : many nonZero numbers in leading
                // -- avoid useless swap
                if (zero != nonZero) {
                    val data = nums[nonZero]
                    nums[nonZero] = nums[zero]
                    // if swap occur, it means
                    nums[zero] = data
                }
                zero++
            }
        }
    }
}
```

---

#### 283. Move Zeroes

- **lang**  `kotlin` 
- **tags**  `Array`  `Two Pointer`
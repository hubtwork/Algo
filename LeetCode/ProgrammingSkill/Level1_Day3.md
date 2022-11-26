## LeetCode Algorithm StudyPlan

<img src="../../assets/leetcode_program_lv1_day3.png" alt="leetcode_programming_skills_level1_day3" style="zoom:50%;" />

### Day 2

- [976. Largest Perimeter Triangle](https://leetcode.com/problems/largest-perimeter-triangle/?envType=study-plan&id=programming-skills-i)
- [1779. Find Nearest Point That Has the S](https://leetcode.com/problems/find-nearest-point-that-has-the-same-x-or-y-coordinate/?envType=study-plan&id=programming-skills-i)

---

#### 976. Largest Perimeter Triangle

- **lang**  `kotlin` 
- **tags**  `Array` `Math` `Greedy` `Sorting`

```kotlin
class Solution {
    fun largestPerimeter(nums: IntArray): Int {
        if (nums.size < 3) return 0
        // sort as reverse order
        nums.sortDescending()
        // if 8, 5, 2, 2, 1 => 8 5 2 miss ? 8 can't make triangle. so pass to next
        for (i in 0..nums.size-3) {
            if (nums[i+2] + nums[i+1] > nums[i]) return nums[i] + nums[i+1] + nums[i+2]
        }
        return 0
    }
}
```

---


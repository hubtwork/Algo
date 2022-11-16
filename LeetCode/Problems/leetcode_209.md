## LeetCode Problems



#### 209. Minimum Size Subarray Sum

- **link**  [209. Minimum Size Subarray Sum](https://leetcode.com/problems/minimum-size-subarray-sum/)

- **lang**  `kotlin` 
- **tags**  `Array` `Binary Search` `Sliding Window` 

```kotlin
class Solution {
    fun minSubArrayLen(target: Int, nums: IntArray): Int {
        var result = nums.size + 1
        var sum = 0
        var left = 0
        // seek minimum count of summation is greater or equal than target
        for (right in 0..nums.size-1) {
            // move right pointer
            sum += nums[right]
            // move left pointer and seek minimum count
            while (sum >= target) {
                result = Math.min(result, right-left + 1)
                sum -= nums[left++]
            }
        }
        return if (result == nums.size+1) 0 else result
    }
}
```

---


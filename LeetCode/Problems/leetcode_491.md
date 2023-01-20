## LeetCode Problems



#### 491. Non-decreasing Subsequences

- **link**  [491. Non-decreasing Subsequences](https://leetcode.com/problems/non-decreasing-subsequences/description/)

- **lang**  `kotlin` 
- **tags** `Array` `Hash Table`

```kotlin
class Solution {
    // feature
    // 1. subarrays are must be registered by increasing or same- order
    // - in [4,4,5,6,7] -> [4,6,7] ( jump is enabled. )
    // implement seek for spread ( n is just 15 , so no time-complexity have to be considered. )
    fun findSubsequences(nums: IntArray): List<List<Int>> {
        val answer = mutableSetOf<List<Int>>()
        seek(answer, listOf(), 0, nums)
        return answer.toList()
    }
    fun seek(bucket: MutableSet<List<Int>>, holder: List<Int>, current: Int, nums: IntArray) {
        // if it fulfill requirements, add to answer.
        if (holder.size >= 2) bucket.add(holder)
        // iterate
        for (i in current until nums.size) {
            // if holder is empty = start of seek
            // if holder's last element is same or larger than current element, pass new holder with added.
            if (holder.isEmpty() || (holder.last() <= nums[i])) seek(bucket, holder + listOf(nums[i]), i + 1, nums)
        }
    }
}
```

---


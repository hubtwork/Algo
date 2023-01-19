## LeetCode Problems



#### 974. Subarray Sums Divisible by K

- **link**  [974. Subarray Sums Divisible by K](https://leetcode.com/problems/subarray-sums-divisible-by-k/)

- **lang**  `kotlin` 
- **tags** `Array` `Hash Table` `Prefix Sum`

```kotlin
class Solution {
    fun subarraysDivByK(nums: IntArray, k: Int): Int {
        // container for each mod-result counts
        val modGroups = IntArray(k)
        var sum = 0
        // iterate
        for (i in 0 until nums.size) {
            // p[i] - p[j] = k * (a - b) + (r1 - r2)
            // => if divisible by K, r2 must be same with r1
            // get each passed-summation and mod it by k.
            sum += nums[i]
            var group = sum % k
            // if passed-summation is negative, pull up to positive by adding k.
            if (group < 0) group += k
            // add mod-count for each possible division.
            modGroups[group]++
        }
        var total = 0
        // pick nC2 to made p[i] = p[j] pair from each mod groups
        modGroups.forEach { n -> total += n * (n-1) / 2 }
        return modGroups[0] + total
    }
}
```

---


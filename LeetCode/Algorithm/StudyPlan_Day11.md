## LeetCode Algorithm StudyPlan

<img src="../../assets/leetcode_study_day11.png" alt="leetcode_study_day11" style="zoom:50%;" />

### Day 11

- [77. Combinations](https://leetcode.com/problems/combinations/?envType=study-plan&id=algorithm-i)
- [46. Permutations](https://leetcode.com/problems/permutations/?envType=study-plan&id=algorithm-i)
- [784. Letter Case Permutation](https://leetcode.com/problems/letter-case-permutation/?envType=study-plan&id=algorithm-i)

---

#### 77. Combinations

- **lang**  `kotlin` 
- **tags**  `BackTracking` 

```kotlin
class Solution {
    private val result = mutableListOf<List<Int>>()
    
    fun combine(n: Int, k: Int): List<List<Int>> {
        track(listOf<Int>(), 1, n, k)
        return result
    }
    // track sorted - order and adding branches
    fun track(list: List<Int>, i: Int, n: Int, k: Int) {
        // if k-elements all filled, add result
        if (list.size == k) {
            result.add(list)
            return
        }
        // add rest elements
        for (j in i..n) {
            // for temporary immutable list
            var current = list
            track(current + j, j+1, n, k)
        }
    }
}
```

---

#### 46. Permutations

- **lang**  `kotlin` 
- **tags**  `BackTracking` `Array`

```kotlin
class Solution {
    private val result = mutableListOf<List<Int>>()
    fun permute(nums: IntArray): List<List<Int>> {
        track(setOf<Int>(), listOf<Int>(), nums)
        return result
    }
    // track all given numbers and add each.
    fun track(registered: Set<Int>, list: List<Int>, nums: IntArray) {
        // if all numbers added, add as result
        if (registered.size == nums.size) {
            result.add(list)
            return
        }
        // traverse all given numbers
        for (i in 0..nums.size-1) {
            // if this is already added, skip it.
            val num = nums[i]
            if (registered.contains(num)) continue
            // track rest seats
            var newSet = registered
            var newList = list
            track(newSet + num, newList + num, nums)
        }
    }
}
```

---

#### 784. Letter Case Permutation

- **lang**  `kotlin` 
- **tags**  `BackTracking` `String`

```kotlin
class Solution {
    private val result = mutableListOf<String>()
    fun letterCasePermutation(s: String): List<String> {
        track("", s, 0)
        return result
    }
    // track in order
    fun track(string: String, s: String, idx: Int) {
        // if read all string, add as result
        if (idx == s.length) {
            result.add(string)
            return
        }
        // add current idx, and track next
        track(string + s[idx], s, idx+1)
        // if it's alphabet, add additional string with reversed character
        if (!s[idx].isDigit()) {
            val reversed = string + (s[idx] + if (s[idx].isLowerCase()) -32 else 32)
            track(reversed, s, idx+1)
        }
    }
}
```

---


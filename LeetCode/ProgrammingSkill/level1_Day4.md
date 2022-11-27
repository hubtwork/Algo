## LeetCode Algorithm StudyPlan

<img src="../../assets/leetcode_program_lv1_day4.png" alt="leetcode_programming_skills_level1_day4" style="zoom:50%;" />

### Day 4

- [1822. Sign of the Product of an Array](https://leetcode.com/problems/sign-of-the-product-of-an-array/?envType=study-plan&id=programming-skills-i)
- [1502. Can Make Arithmetic Progression From Sequence ](https://leetcode.com/problems/can-make-arithmetic-progression-from-sequence/?envType=study-plan&id=programming-skills-i)
- [202. Happy Number](https://leetcode.com/problems/happy-number/?envType=study-plan&id=programming-skills-i)
- [1790. Check if One String Swap Can Make Strings Equal](https://leetcode.com/problems/check-if-one-string-swap-can-make-strings-equal/?envType=study-plan&id=programming-skills-i)

---

#### 1822. Sign of the Product of an Array

- **lang**  `kotlin` 
- **tags**  `Array` `Math` 

```kotlin
class Solution {
    fun arraySign(nums: IntArray): Int {
        var result = 1
        // sign(product nums) = product of each sign(num in nums)
        nums.forEach { value -> result *= when {
            value > 0 -> 1
            value < 0 -> -1
            else -> 0
        }}
        return result
    }
}
```

---

#### 1502. Can Make Arithmetic Progression From Sequence

- **lang**  `kotlin` 
- **tags**  `Array` `Sorting`

```kotlin
class Solution {
    fun canMakeArithmeticProgression(arr: IntArray): Boolean {
        // find optimal gap
        arr.sort()
        val gap = arr[1] - arr[0]
        // loop each elements, but not same with optimal gap, return false
        for(i in 2..arr.size-1) if (arr[i]-arr[i-1] != gap) return false
        return true
    }
}
```

---

#### 202. Happy Number

- **lang**  `kotlin` 
- **tags**  `Hash Table` `Math` `Two Pointers`

```kotlin
class Solution {
    // memorize passed number
    private val memo = mutableSetOf<Int>()
    fun isHappy(n: Int): Boolean {
        return beHappy(n)
    }
    fun beHappy(n: Int): Boolean {
        // if memorized refaced, it's cycle.
        if (memo.contains(n)) return false
        // find happy number
        if (n == 1) return true
        memo.add(n)
        // create next number based on happy rule
        var happyRule = 0
        var num = n
        while (num > 0) {
            val mod = num%10
            happyRule += mod * mod
            num /= 10
        }
        return beHappy(happyRule)
    }
}
```

---

#### 1790. Check if One String Swap Can Make Strings Equal

- **lang**  `kotlin` 
- **tags**  `Hash Table` `String` `Counting`

```kotlin
class Solution {
    // memorize first unmatched pair
    private var memo: Pair<Char, Char>? = null
    fun areAlmostEqual(s1: String, s2: String): Boolean {
        var count = 0
        // seek unmatched pair
        for (i in 0..s1.length-1) {
            if (s1[i] != s2[i]) {
                // if found umatched pair already twice, it can't be accquire rule.
                if (count++ > 2) return false
                memo?.let {
                    // if memo is exists but it's not matched with reversed pair, return false
                    if (!(it.first == s2[i] && it.second == s1[i])) return false
                }?: run {
                    // memorize this pair for next compare
                    memo = s1[i] to s2[i]
                }
            }
        }
        return if (count == 1) false else true
    }
}
```

---


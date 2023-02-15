## LeetCode Problems



#### 997. Add to Array-Form of Integer

- **link**  [997. Add to Array-Form of Integer](https://leetcode.com/problems/add-to-array-form-of-integer/)

- **lang**  `kotlin` 
- **tags** `Array` `Math`

```kotlin
class Solution {
    fun addToArrayForm(num: IntArray, k: Int): List<Int> {
        var result = mutableListOf<Int>()
        var pointer = num.size
        var kNum = k
        // iterate with moving pointer
        while (--pointer >= 0 || kNum > 0) {
            // if pointer is possible to move, add current index-number
            if (pointer >= 0) kNum += num[pointer]
            // add current summation's index number to answer list
            result.add(kNum % 10)
            // modular calculation for next iteration
            kNum /= 10
        }
        // return reversed array
        return result.reversed() 
    }
}
```

---


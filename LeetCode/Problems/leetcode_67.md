## LeetCode Problems



#### 67. Add Binary

- **link**  [67. Add Binary](https://leetcode.com/problems/add-binary/description/)

- **lang**  `kotlin` 
- **tags**  `Math` `String` `Bit Manipulation`

```kotlin
class Solution {
    fun addBinary(a: String, b: String): String {
        // read backward by move pointers
        var aPtr = a.length-1
        var bPtr = b.length-1
        // carry for each next step.
        var carry = 0
        var answer = ""
        // iterate
        while (aPtr >= 0 || bPtr >= 0) {
            var sum = 0
            if (aPtr >= 0) sum += a[aPtr--] - '0'
            if (bPtr >= 0) sum += b[bPtr--] - '0'
            sum += carry
            carry = sum / 2
            sum = sum % 2
            answer = sum.toString() + answer
        }
        if (carry == 1) answer = "1$answer"
        return answer
    }
}
```

---


## LeetCode Problems



#### 67. Add Binary

- **link**  [67. Add Binary](https://leetcode.com/problems/add-binary/description/)

- **lang**  `kotlin` 
- **tags**  `Math` `String` `Bit Manipulation`

```kotlin
class Solution {
    fun addBinary(a: String, b: String): String {
        // start with 0-index ( string is reversed )
        var aPtr = a.length - 1
        var bPtr = b.length - 1
        // use carry and sum for iteration
        var carry = 0
        var sum = 0
        var result = ""
        // iterate single pointer and with carry possibility
        while (aPtr >= 0 || bPtr >= 0 || carry > 0) {
            // check if is iterative and add to temporary sum
            if (aPtr >= 0) sum += a[aPtr--] - '0'
            if (bPtr >= 0) sum += b[bPtr--] - '0'
            // add current index's summation to result
            result = ('0' + (sum % 2)) + result
            // carry and sum relocate for next index
            carry = sum / 2
            sum = carry
        }
        return result
    }
}
```

---


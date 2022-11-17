## LeetCode Problems



#### 43. Multiply Strings

- **link**  [43. Multiply Strings](https://leetcode.com/problems/multiply-strings/)

- **lang**  `kotlin` 
- **tags**  `Math` `String` `Simulation`

```kotlin
class Solution {
    fun multiply(num1: String, num2: String): String {
        val result = IntArray(num1.length + num2.length)
        var start = 0
        /*
            calculate each digits on basic - math
                913
              x  21
            ->  913
              1826
              -----
              19173
        */
        for (second in num2.length-1 downTo 0) {
            for (first in num1.length-1 downTo 0) {
                // char to int and multiply
                val mul = (num1[first]-'0') * (num2[second] -'0')
                val target = first + second + 1
                // sum multiplied with origin digit
                val sum = mul + result[target]
                result[target-1] += sum / 10
                result[target] = sum % 10
            }
        }
        var answer = ""
        result.forEach { if(!(answer.length == 0 && it == 0)) answer += it.toString() }
        return if (answer.length == 0) "0" else answer
    }
}
```

---


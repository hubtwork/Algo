## LeetCode Problems



#### 224. Basic Calculator

- **link**  [224. Basic Calculator](https://leetcode.com/problems/basic-calculator/)

- **lang**  `kotlin` 
- **tags**  `Math` `String` `Stack` `Recursion` 

```kotlin
class Solution {
    fun calculate(s: String): Int {
        val stack = Stack<Int>()
        // live summation, current number, last sign for distinguish expression
        var sum: Int = 0
        var num: Int = 0
        var sign: Int = 1
        s.forEach { ch ->
            // whitespace is not included sequence.
            if (ch != ' ') {
                if (ch.isDigit()) {
                    // if num, convert this character to cache-number
                    num = num * 10 + Character.getNumericValue(ch)
                } else if (ch == '+') {
                    // if sign value is +, change last sign as 1
                    // add number with before sign value to live summation
                    sum += num * sign
                    sign = 1
                    num = 0
                } else if (ch == '-') {
                    // if sign value is -, change last sign as -1
                    // add number with before sign value to live summation
                    sum += num * sign
                    sign = -1
                    num = 0
                } else if (ch == '(') {
                    // if '(' start, save live summation and last sign value.
                    stack.add(sum)
                    stack.add(sign)
                    sum = 0
                    sign = 1
                } else if (ch == ')') {
                    // if ')' met, get saved summation and add to live summation
                    sum += num * sign
                    sum = sum * stack.pop() + stack.pop()
                    num = 0
                    sign = 1
                }
            }
        }
        // return result
        return sum + num * sign
    }
}
```

---


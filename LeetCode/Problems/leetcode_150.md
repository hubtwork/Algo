## LeetCode Problems



#### 150. Evaluate Reverse Polish Notation

- **link**  [150. Evaluate Reverse Polish Notation](https://leetcode.com/problems/evaluate-reverse-polish-notation/)

- **lang**  `kotlin` 
- **tags**  `Array` `Math` `Stack`

```kotlin
class Solution {
    fun evalRPN(tokens: Array<String>): Int {
        val stack = Stack<Int>()
        // traverse
        tokens.forEach { c ->
            // use try / catch for "fun String.toInt()"
            // if it's not convertible to cast to int, it'll throw NumberFormatException
            try { 
                stack.push(c.toInt())
            } catch(e: Throwable) {
                // get 2 peek numbers from stack
                val a = stack.pop()
                val b = stack.pop()
                // calculate with given operator
                stack.push(when (c) {
                    "+" -> b + a
                    "-" -> b - a
                    "/" -> b / a
                    else -> b * a
                })
            }
        }
        return stack.pop()
    }
}
```

---


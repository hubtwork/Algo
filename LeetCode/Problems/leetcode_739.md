## LeetCode Problems



#### 739. Daily Temperatures

- **link**  [739. Daily Temperatures](https://leetcode.com/problems/daily-temperatures/description/)

- **lang**  `kotlin` 
- **tags** `Array` `Stack` `Monotonic Stack`

```kotlin
class Solution {
    fun dailyTemperatures(temperatures: IntArray): IntArray {\
        /*
            use Monotonic Stack. ( get each pos's first lower or first upper)
            Q : get each node's first upper.
            iterate reverse-order.
         */
        val stack = Stack<Int>()
        val result = IntArray(temperatures.size)
        result[temperatures.size-1] = 0
        stack.add(temperatures.size-1)
        // iterate
        for (pos in temperatures.size-2 downTo 0) {
            // if value at pos in stack is smaller than current, pop
            while (stack.isNotEmpty() && temperatures[stack.peek()] <= temperatures[pos]) stack.pop()
            // if stack is empty, no upper value in next.
            // first upper of current is last pos - current.
            result[pos] = if (stack.isEmpty()) 0 else stack.peek() - pos
            stack.add(pos)
        }
        return result
    }
}
```

---


## LeetCode Problems



#### 1675. Minimize Deviation in Array

- **link**  [1675. Minimize Deviation in Array](https://leetcode.com/problems/minimize-deviation-in-array/description/)

- **lang**  `kotlin` 
- **tags**  `Array` `Greedy` `Heap` `Ordered Set`

```kotlin
import kotlin.math.min
class Solution {
    fun minimumDeviation(nums: IntArray): Int {
        // Using Max Heap to decrease diff from min
        val pq = PriorityQueue<Int> { a, b -> b - a }
        var minNum = 1000000001
        // check minimum number and add numbers to PQ
        // if number is odd, mul 2 for atMostOne operation
        nums.forEach { prev ->
            val num = if (prev % 2 == 1) prev * 2 else prev
            minNum = min(minNum, num)
            pq.add(num)
        }
        var diff = 1000000001
        // check until possible even
        while (pq.peek() % 2 == 0) {
            val max = pq.poll()
          	val reducedMax = max / 2
            // reduce max-ceil to reduce range
            diff = min(diff, max - minNum)
            minNum = min(minNum, reducedMax)
            pq.add(reducedMax)
        }
        return min(diff, pq.peek() - minNum)
    }
}
```

---


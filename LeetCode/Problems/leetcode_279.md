## LeetCode Problems



#### 279. Perfect Squares

- **link**  [279. Perfect Squares](https://leetcode.com/problems/perfect-squares/)

- **lang**  `kotlin` 
- **tags**  `Math` `BFS`

```kotlin
import kotlin.math.*
class Solution {
    fun numSquares(n: Int): Int {
        return bfs(n)
    }
    fun bfs(n: Int): Int {
        val queue: Queue<Int> = LinkedList<Int>().apply { add(n) }
        var result = 1
        // traverse
        while (queue.isNotEmpty()) {
            val size = queue.size
            for (component in 0..size-1) {
                val rest = queue.poll()
                /*
                    optimization
                    # current's max perfect number = sqrt(current)
                    # from sqrt(current) to 1, 
                    # if (rest - i^2 == 0) = find result
                    # if (rest - i^2 > 0) = add queue to next calculation
                */
                for (i in sqrt(rest.toDouble()).toInt() downTo 1) {
                    val pw = i * i
                    if (rest - pw == 0) return result
                    else if (rest - pw > 0) queue.add(rest-pw)
                }
            }
            result ++
        }
        return result
    }
}
```

---


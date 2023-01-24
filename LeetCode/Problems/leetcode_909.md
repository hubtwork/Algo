## LeetCode Problems



#### 909. Snakes and Ladders

- **link**  [909. Snakes and Ladders](https://leetcode.com/problems/snakes-and-ladders/description/)

- **lang**  `kotlin` 
- **tags** `Array` `BFS` `Matrix`

```kotlin
import kotlin.math.min
class Solution {
    fun snakesAndLadders(board: Array<IntArray>): Int {
        val n = board.size
        val queue: Queue<Int> = LinkedList<Int>()
        val visited = BooleanArray(n * n + 1)
        visited[1] = true
        queue.add(1)
        // iterate
        var step = 0
        while (queue.isNotEmpty()) {
            val phase = queue.size
            for (i in 0 until phase) {
                val current = queue.poll()
                // check possible-ranges
                val nextRange = (current + 1)..min(current + 6, n * n)
                for (next in nextRange) {
                    // find next's row and col
                    // (1) row : (next - 1) / n from bottom
                    // (2) col : (next - 1) % n by moving-direction ( right-forward / left-forward )
                    val row = (n - 1) - (next - 1) / n
                    val col = if (row % 2 != n % 2) (next - 1) % n else (n - 1) - (next - 1) % n
                    // if destination has jump ( snake or ladder ), align jump destination
                    val destination = if (board[row][col] != -1) board[row][col] else next
                    if (destination == n * n) return step + 1
                    if (!visited[destination]) {
                        queue.add(destination)
                        visited[destination] = true
                    }
                }
            }
            step++
        }
        return -1
    }
}
```

---


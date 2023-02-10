## LeetCode Problems



#### 1162. As Far from Land as Possible

- **link**  [1162. As Far from Land as Possible](https://leetcode.com/problems/as-far-from-land-as-possible/)

- **lang**  `kotlin` 
- **tags**  `Array`  `DP` `BFS`

```kotlin
import kotlin.math.max
class Solution {
    enum class Direction(val x: Int, val y: Int) {
        U(-1, 0), R(0, 1), D(1, 0), L(0, -1)
    }
    fun maxDistance(grid: Array<IntArray>): Int {
        val width = grid[0].size
        val height = grid.size
        // max-step
        var step = -1
        // enroll lands to queue
        val queue: Queue<Pair<Int, Int>> = LinkedList()
        for (x in 0 until height) {
            for (y in 0 until width) {
                if (grid[x][y] == 1) queue.add(x to y)
            }
        }
        // record minimum Manhattan distance to land
        val dist = Array<IntArray>(height, { IntArray(width) })
        while (queue.isNotEmpty()) {
            val curr = queue.poll()
            Direction.values().forEach { di ->
                val nx = curr.first + di.x
                val ny = curr.second + di.y
                // if loc is inside grid and not-yet-visited "water", record dist
                if (
                    nx >= 0 && nx < height && ny >= 0 && ny < width &&
                    grid[nx][ny] == 0 && dist[nx][ny] == 0
                ) {
                    dist[nx][ny] = dist[curr.first][curr.second] + 1
                    queue.add(nx to ny)
                  	// record each best-far steps
                    step = max(step, dist[nx][ny])
                }
            }
        }
    
        return step
    }
}
```

---


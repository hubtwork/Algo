## LeetCode Problems



#### 1926. Nearest Exit from Entrance in Maze

- **link**  [1926. Nearest Exit from Entrance in Maze](https://leetcode.com/problems/nearest-exit-from-entrance-in-maze/)

- **lang**  `kotlin` 
- **tags**  `Array` `BFS` `Matrix`

```kotlin
class Solution {
    enum class Direction(val x: Int, val y: Int) {
        Up(-1, 0),
        Down(1, 0),
        Left(0, -1),
        Right(0, 1);
    }
    private lateinit var map: Array<CharArray>
    fun nearestExit(maze: Array<CharArray>, entrance: IntArray): Int {
        map = maze
        return bfs(entrance)
    }
    // traverse
    fun bfs(entrance: IntArray): Int {
        // mark entrance as already visited ( avoid think as exit )
        map[entrance[0]][entrance[1]] = '-'
        val queue: Queue<Pair<Int, Int>> = LinkedList<Pair<Int, Int>>().apply {
            add(entrance[0] to entrance[1])
        }
        // traverse each distance
        var distance = 0
        while(queue.isNotEmpty()) {
            val len = queue.size
            for (i in 0..len-1) {
                val (x, y) = queue.poll()
                for (di in Direction.values()) {
                    // if next step is inside maze
                    val (dx, dy) = x + di.x to y + di.y
                    if (dx in 0..map.size-1 && dy in 0..map[0].size-1 && map[dx][dy] == '.') {
                        // mark next position as visited ( avoid revisit queue-ing issue )
                        map[dx][dy] = '-'
                        // if it's exit, return distance + 1 else add to queue to continue
                        if (dx == 0 || dx == map.size-1 || dy == 0 || dy == map[0].size-1) return distance + 1
                        else queue.add(dx to dy)
                    }
                }
            }
            distance++
        }
        return -1
    }
}
```

---


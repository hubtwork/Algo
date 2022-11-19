## LeetCode Algorithm StudyPlan

<img src="/Users/alenheo/Desktop/repo/algo/assets/leetcode_study_day9.png" alt="leetcode_study_day9" style="zoom:50%;" />

### Day 9

- [542. 01 Matrix](https://leetcode.com/problems/01-matrix/?envType=study-plan&id=algorithm-i)
- [994. Rotting Oranges](https://leetcode.com/problems/rotting-oranges/?envType=study-plan&id=algorithm-i)

---

#### 542. 01 Matrix

- **lang**  `kotlin` 
- **tags**  `Array` `BFS` `Matrix` `DP`

```kotlin
class Solution {
    enum class Direction(val x: Int, val y: Int) {
        Up(-1, 0),
        Down(1, 0),
        Left(0, -1),
        Right(0, 1);
    }
    private lateinit var map: Array<IntArray>
    fun updateMatrix(mat: Array<IntArray>): Array<IntArray> {
        map = mat
        // bfs()
        dp()
        return map
    }
    fun isInside(x: Int, y: Int): Boolean {
        return x >= 0 && x < map.size && y >= 0 && y < map[0].size
    }
    fun bfs() {
        // mark as -1 have to process, and add 0 to q
        val q: Queue<Pair<Int, Int>> = LinkedList()
        map.forEachIndexed { x, row ->
            row.forEachIndexed { y, value ->
                if (map[x][y] == 0) q.add(Pair(x, y))
                else map[x][y] = -1
            }
        }
        // traverse
        while (q.isNotEmpty()) {
            val tmp = q.poll()
            // check 4 directions of current
            for (di in Direction.values()) {
                val dx = tmp.first + di.x
                val dy = tmp.second + di.y
                // if it's not processed, add length + 1 from current
                if (isInside(dx, dy) && map[dx][dy] == -1) {
                    map[dx][dy] = map[tmp.first][tmp.second] + 1
                    q.add(Pair(dx, dy))
                }
            }
        }
    }
    fun dp() {
        val maxLength = map.size + map[0].size
        // check length from top, left
        map.forEachIndexed { x, row ->
            row.forEachIndexed { y, value -> 
                if (map[x][y] != 0) {
                    val top: Int = if (x >= 1) map[x-1][y] else maxLength
                    val left: Int = if (y >= 1) map[x][y-1] else maxLength
                    // 
                    map[x][y] = Math.min(top, left) + 1
                }
            }
        }
        // check length from bottom, right ( reversed order )
        for (x in map.size-1 downTo 0) {
            for (y in map[0].size-1 downTo 0) {
                if (map[x][y] != 0) {
                    val bottom: Int = if (x < map.size-1) map[x+1][y] else maxLength
                    val right: Int = if (y < map[0].size-1) map[x][y+1] else maxLength
                    map[x][y] = Math.min(map[x][y], Math.min(bottom, right) + 1)
                }
            }
        }
    }
}
```

---

#### 994. Rotting Oranges

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
    private lateinit var orranges: Array<IntArray>
    fun orangesRotting(grid: Array<IntArray>): Int {
        orranges = grid
        return bfs()
    }
    fun isInside(x: Int, y: Int): Boolean =
        x >= 0 && x < orranges.size && y >= 0 && y < orranges[0].size
    fun bfs(): Int {
        // register rotten-start orrange's positions and count fresh-orrange
        var count = 0
        var q: Queue<Pair<Int, Int>> = LinkedList()
        orranges.forEachIndexed { x, row ->
            row.forEachIndexed { y, value ->
                if (value == 2) q.add(Pair(x, y))
                else if (value == 1) count ++
            }
        }
        // if no fresh-orrange, return 0
        if (count == 0) return 0
        // consume fresh-orranges
        var minute = -1
        while (q.isNotEmpty()) {
            val size = q.size
            // each step, consume and register new rotten-orranges
            for (loop in 0..size-1) {
                val current = q.poll()
                for (di in Direction.values()) {
                    val dx = current.first + di.x
                    val dy = current.second + di.y
                    if (isInside(dx, dy) && orranges[dx][dy] == 1) {
                        orranges[dx][dy] = 2
                        q.add(Pair(dx, dy))
                        count--
                    }
                }
            }
            minute++
        }
        // if fresh-orranges remain, return -1
        return if (count != 0) -1 else minute
    }
}
```

---


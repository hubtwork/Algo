## LeetCode Algorithm StudyPlan

<img src="/Users/alenheo/Desktop/repo/algo/assets/leetcode_study_day9.png" alt="leetcode_study_day9" style="zoom:50%;" />

### Day 8

- [542. 01 Matrix](https://leetcode.com/problems/01-matrix/?envType=study-plan&id=algorithm-i)
- [994. Rotting Oranges](https://leetcode.com/problems/rotting-oranges/?envType=study-plan&id=algorithm-i)

---

#### 542. 01 Matrix

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
    private lateinit var map: Array<IntArray>
    fun updateMatrix(mat: Array<IntArray>): Array<IntArray> {
        map = mat
        bfs()
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
    
}
```

---


## LeetCode Algorithm StudyPlan

<img src="/Users/alenheo/Desktop/repo/algo/assets/leetcode_study_day7.png" alt="leetcode_study_day7" style="zoom:50%;" />

### Day 6

- [733. Flood Fill](https://leetcode.com/problems/flood-fill/?envType=study-plan&id=algorithm-i)
- [695. Max Area of Island](https://leetcode.com/problems/max-area-of-island/?envType=study-plan&id=algorithm-i)

---

#### 733. Flood Fill

- **lang**  `kotlin` 
- **tags**  `Array` `DFS` `BFS` `Matrix` 

```kotlin
class Solution {
    enum class Direction(val x: Int, val y: Int) {
        Up(0, -1),
        Down(0, 1),
        Left(-1, 0),
        Right(1, 0);
    }
    private lateinit var image: Array<IntArray>
    private var color: Int = 0
    private var starting: Int = 0
    fun isInside(dx: Int, dy: Int): Boolean {
        return dx >= 0 && dx < image.size && dy >= 0 && dy < image[0].size
    }
  	/*
  			flood fill condition ( in order )
  			1) current pos is inside
  			2) current pos is same as starting color
  			3) current pos is not yet colored
  	*/
    fun floodFill(image: Array<IntArray>, sr: Int, sc: Int, color: Int): Array<IntArray> {
        this.image = image
        this.color = color
        this.starting = image[sr][sc]
        fillBFS(sr, sc)
        // fillDFS(sr, sc)
        return this.image
    }
  	// process dfs with recursive
    fun fillDFS(x: Int, y: Int) {
        if (isInside(x, y) && image[x][y] == starting && image[x][y] != color) {
            image[x][y] = color
            for (di in Direction.values()) {
                fillDFS(x + di.x, y + di.y)
            }
        }
    }
  	// process bfs with processing queue
    fun fillBFS(sr: Int, sc: Int) {
        val fillQ = mutableListOf<Pair<Int,Int>>(Pair(sr, sc))
        while (!fillQ.isEmpty()) {
            val c = fillQ.get(0)
            fillQ.removeAt(0)
            val x = c.first
            val y = c.second
            if (image[x][y] == color) continue
            image[x][y] = color
            for (di in Direction.values()) {
                val dx = x + di.x
                val dy = y + di.y
                if (isInside(dx, dy) && image[dx][dy] == starting) fillQ.add(Pair(dx, dy))
            }
            
        }
    }
}
```

---


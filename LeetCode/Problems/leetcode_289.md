## LeetCode Problems



#### 289. Game of Life

- **link**  [289. Game of Life](https://leetcode.com/problems/game-of-life/description/)

- **lang**  `kotlin` 
- **tags**  `Array` `Matrix` `Simulation`

```kotlin
class Solution {
    fun gameOfLife(board: Array<IntArray>): Unit {
        val h = board.size
        val w = board[0].size
        // Marking Logic ( Dead or Alive )
        // 1 => (2 dead, 1 alive)
        // 0 => (0 dead, -1 alive)
        fun deadOrAlive(x: Int, y: Int) {
            val center = board[x][y]
            var count = 0
            for (i in x-1..x+1) {
                for (j in y-1..y+1) {
                    // if not inside board or it's center, skip it.
                    if (i < 0 || i >= h || j < 0 || j >= w) continue
                    if (i == x && j == y) continue
                    // if cell is live, increase count
                    if (board[i][j] >= 1) count++
                    // avoid useless additional computation
                    if (center == 1 && count > 3) {
                        board[x][y] = 2
                        return
                    }
                }
            }
            // mark dead one if will be dead in next step
            if (center == 1 && count < 2) board[x][y] = 2
            else if (center == 0 && count == 3) board[x][y] = -1
        }
        // iterate and mark
        for (i in 0..h-1) {
            for (j in 0..w-1) {
                deadOrAlive(i, j)
            }
        }
        // reflect next-step-marker
        for (i in 0..h-1) {
            for (j in 0..w-1) {
                if (board[i][j] == -1) board[i][j] = 1
                if (board[i][j] == 2) board[i][j] = 0
            }
        }
    }
}
```

---


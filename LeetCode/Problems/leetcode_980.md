## LeetCode Problems



#### 980. Unique Paths III

- **link**  [980. Unique Paths III](https://leetcode.com/problems/unique-paths-iii/description/)

- **lang**  `kotlin` 
- **tags** `Array` `BackTracking` `DFS`

```kotlin
class Solution {
    data class Tile(val x: Int, val y: Int) {
        fun move(di: Direction): Tile {
            return copy(x = x + di.x, y = y + di.y)
        }
        fun isInside(m: Int, n: Int): Boolean {
            return x >= 0 && x < m && y >= 0 && y < n
        }
    }
    enum class Direction(val x: Int, val y: Int) {
        Up(-1, 0), Right(0, 1), Down(1, 0), Left(0, -1)
    }
    private var result = 0
    private var tileCount = 0

    fun uniquePathsIII(grid: Array<IntArray>): Int {
        var start: Tile? = null
        // traverse
        grid.forEachIndexed { x, rGrid ->
            rGrid.forEachIndexed { y, value ->
                // mark total have-to-visit-tile count.
                if (value == 0) tileCount ++
                // set start location
                if (value == 1) start = Tile(x, y)
            }
        }
        dfs(grid, start!!, 0)
        return result
    }
    private fun dfs(grid: Array<IntArray>, tile: Tile, walked: Int) {
        // if tile is already visited route or obstacle, return.
        if (grid[tile.x][tile.y] < 0) return
        // if tile is ending and walkthrough-distance is tileCount + 1, add endCount
        if (grid[tile.x][tile.y] == 2 && walked == tileCount + 1) {
            result++
            return
        }
        // temporary set to visited for current dfs-trace.
        val value = grid[tile.x][tile.y]
        grid[tile.x][tile.y] = -2
        Direction.values().forEach { di ->
            // if next tile is in grid, trace route.
            val next = tile.move(di)
            if (next.isInside(grid.size, grid[0].size)) {
                dfs(grid, next, walked + 1)
            }
        }
        // recover grid for other dfs-trace.
        grid[tile.x][tile.y] = value
    }
}
```

---


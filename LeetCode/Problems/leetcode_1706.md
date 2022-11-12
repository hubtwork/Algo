## LeetCode Problems



#### 1706. Where Will the Ball Fall

- **link**  [1706. Where Will the Ball Fall](https://leetcode.com/problems/where-will-the-ball-fall/)

- **lang**  `kotlin` 
- **tags**  `Array` `DP` `DFS` `Matrix` `Simulation`

```kotlin
class Solution {
    fun findBall(grid: Array<IntArray>): IntArray {
        val depth = grid.size
        val width = grid[0].size
        val answer = IntArray(width)
        for (startPoint in 0..width-1) {
            var loc = startPoint
            var floor = 0
            // simulate each ball's falling until last floor
            run simulate@ {
                while (floor < depth) {
                    // if can't fallable, cancel simulate
                    if (isNotFallable(grid, width, floor, loc)) {
                        answer[startPoint] = -1
                        return@simulate
                    }
                    // if can fallable, simulate next step
                    loc += grid[floor++][loc]
                }
                // successful escape !
                answer[startPoint] = loc
            }
        }
        return answer
    }
    
    fun isNotFallable(grid: Array<IntArray>, width: Int, floor: Int, loc: Int): Boolean {
        /*
            # not fallable cases ( shape )
            1. \|
            2. |/
            3. \/ ( l side, r side either)
        */
        return (grid[floor][loc] == 1 && loc == width-1) 
        || (grid[floor][loc] == -1 && loc == 0)
        || (grid[floor][loc] == 1 && grid[floor][loc+1] == -1)
        || (grid[floor][loc] == -1 && grid[floor][loc-1] == 1)
    }
}
```

---


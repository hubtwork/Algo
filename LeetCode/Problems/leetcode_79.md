## LeetCode Problems



#### 79. Word Search

- **link**  [79. Word Search](https://leetcode.com/problems/word-search/)

- **lang**  `kotlin` 
- **tags**  `Back Tracking` `Array` `Matrix`

```kotlin
class Solution {
    enum class Direction(val x: Int, val y: Int) {
        Up(-1, 0),
        Down(1, 0),
        Left(0, -1),
        Right(0, 1)
    }
    private lateinit var map: Array<CharArray>
    var answer = ""
    
    fun exist(board: Array<CharArray>, word: String): Boolean {        
        map = board
        answer = word
        map.forEachIndexed { x, row ->
            row.forEachIndexed { y, value -> 
                if (seek(setOf(x to y), x to y, 0)) return true
            }
        }
        return false
    }
    
    fun seek(visited: Set<Pair<Int, Int>>, last: Pair<Int, Int>, size: Int): Boolean {
        val (x, y) = last
        // seek dfs only meet correct word
        if (map[x][y] == answer[size]) {
            // if last word is correct, seek completed.
            if (size == answer.length-1) return true
            // traverse
            Direction.values().forEach { di ->
                val dx = x + di.x
                val dy = y + di.y
                // if isInside & not visited
                if (
                    dx in 0..map.size-1
                    && dy in 0..map[0].size-1
                    && !visited.contains(dx to dy)
                ) {
                    if (seek(visited + setOf(dx to dy), dx to dy, size + 1)) return true
                }
            }
        }
        return false
    }
}
```

---


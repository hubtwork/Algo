## LeetCode Problems



#### 1345. Jump Game IV

- **link**  [1345. Jump Game IV](https://leetcode.com/problems/jump-game-iv/)

- **lang**  `kotlin` 
- **tags**  `Array` `BFS` `Hash Table`

```kotlin
class Solution {
    fun minJumps(arr: IntArray): Int {
        if (arr.size <= 1) return 0
        var result = 0
        val size = arr.size
        // build (value : indexes) map for O(1) access
        val indexMap = mutableMapOf<Int, MutableList<Int>>()
        arr.forEachIndexed { idx, lev -> 
            if (!indexMap.contains(lev)) indexMap[lev] = mutableListOf(idx)
            else indexMap[lev]?.add(idx)
        }
        // create visit-checker to prevent revisit-problem
        val visited = BooleanArray(size).apply { set(0, true) }
        // iterate BFS
        val queue: Queue<Int> = LinkedList<Int>().apply { add(0) } 
        while(queue.isNotEmpty()) {
            for (i in 0 until queue.size) {
                val idx = queue.poll()
                // get possible next step idx
                val next: MutableList<Int> = indexMap[arr[idx]] ?: mutableListOf()
                if (idx < size) next.add(idx + 1)
                if (idx > 0) next.add(idx - 1)
                // check
                next.forEach { possibleNext ->
                    // if visit-possible,
                    if (!visited[possibleNext]) {
                        if (possibleNext == size - 1) return result + 1
                        // mark and add for next visitation
                        visited[possibleNext] = true
                        queue.add(possibleNext)
                    }
                }
                // remove index map to prevent infinite loop
                indexMap[arr[idx]]?.clear()
            }
            result ++
        }
        return 0
    }
}
```

---


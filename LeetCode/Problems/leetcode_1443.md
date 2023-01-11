## LeetCode Problems



#### 1443. Minimum Time to Collect All Apples in a Tree

- **link**  [1443. Minimum Time to Collect All Apples in a Tree](https://leetcode.com/problems/minimum-time-to-collect-all-apples-in-a-tree/description/)

- **lang**  `kotlin` 
- **tags**  `Tree` `DFS` `Hash Table`

```kotlin
class Solution {
    fun minTime(n: Int, edges: Array<IntArray>, hasApple: List<Boolean>): Int {
        // construct graph
        val graph = mutableMapOf<Int, MutableList<Int>>()
        for (i in 0 until n) graph[i] = mutableListOf()
        edges.forEach { edge ->
            graph[edge[0]]!!.add(edge[1])
            graph[edge[1]]!!.add(edge[0])
        }
        return dfs(graph, 0, hasApple, BooleanArray(n))
    }
    
    fun dfs(graph: Map<Int, List<Int>>, current: Int, hasApple: List<Boolean>, visited: BooleanArray): Int {
        var time = 0
        visited[current] = true
        graph[current]!!.forEach { next ->
            // if non-visited connected node exists, first-search to get time.
            if (!visited[next]) time += dfs(graph, next, hasApple, visited)
        }
        // if child-path is has-apple-path (time > 0) or current has apple,
        // add round-trip-time ( +2 )
        if (current != 0 && (hasApple[current] || time > 0)) time += 2
        return time
    }
}
```

---


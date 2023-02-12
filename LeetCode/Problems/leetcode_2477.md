## LeetCode Problems



#### 2477. Minimum Fuel Cost to Report to the Capital

- **link**  [2477. Minimum Fuel Cost to Report to the Capital](https://leetcode.com/problems/minimum-fuel-cost-to-report-to-the-capital/description/)

- **lang**  `kotlin` 
- **tags**  `Tree` `DFS` `Graph`

```kotlin
class Solution {
    var fuelCounts = 0L
    fun minimumFuelCost(roads: Array<IntArray>, seats: Int): Long {
        // roads.size == n - 1
        val size = roads.size
        // build Graph
        val graph = mutableMapOf<Int, MutableList<Int>>()
        for (i in 0 until size) graph[i] = mutableListOf()
        roads.forEach { road -> 
            graph[road[0]]?.add(road[1])
            graph[road[1]]?.add(road[0])
        }
        // with visit-check, visit all node with people counting.
        val visited = mutableSetOf<Int>()
        dfs(0, visited, graph, seats)
        return fuelCounts
    }
    // dfs implementations
    fun dfs(node: Int, visited: MutableSet<Int>, graph: Map<Int, List<Int>>, seats: Int): Int {
        visited.add(node)
        // start with current node's 1 people count
        var people = 1
        graph[node]?.forEach { next ->
            // grab all child's people count
            if (!visited.contains(next)) people += dfs(next, visited, graph, seats)
        }
        // add fuel cost to answer for each step.
        if (node != 0) fuelCounts += (people + seats - 1) / seats
        // push people count bottom-up
        return people
    }
}
```

---


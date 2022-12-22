## LeetCode Problems



#### 886. Possible Bipartition

- **link**  [886.Possible Bipartition](https://leetcode.com/problems/possible-bipartition/)

- **lang**  `kotlin` 
- **tags**  `DFS` `Graph`

```kotlin
class Solution {
    private lateinit var graph: Array<IntArray>
    private lateinit var group: IntArray
    fun possibleBipartition(n: Int, dislikes: Array<IntArray>): Boolean {
        // initialize graph and group for dislikes grouping
        graph = Array<IntArray>(n, { IntArray(n) })
        group = IntArray(n)
        // 1 / -1 = grouping
        dislikes.forEach { dis ->
            graph[dis[0]-1][dis[1]-1] = 1
            graph[dis[1]-1][dis[0]-1] = 1
        }
        // traverse
        for(i in 0..n-1) {
            if (group[i] == 0 && !dfs(i, 1)) return false
        }
        return true
    }
    /*
        if group[i] == 0, it's new one.
        if group[i] == 1 or -1 , it's grouped in that number.
     */
    fun dfs(idx: Int, gId: Int): Boolean {
        group[idx] = gId
        for (i in 0..graph.size-1) {
            if (graph[idx][i] != 1) continue
            if (group[i] == gId) return false
            if (group[i] == 0 && !dfs(i, -gId)) return false 
        }
        return true
    }

}
```

---

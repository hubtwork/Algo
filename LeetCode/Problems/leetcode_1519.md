## LeetCode Problems



#### 1519. Number of Nodes in the Sub-Tree With the Same Label

- **link**  [1519. Number of Nodes in the Sub-Tree With the Same Label](https://leetcode.com/problems/number-of-nodes-in-the-sub-tree-with-the-same-label/description/)

- **lang**  `kotlin` 
- **tags**  `Tree` `DFS` `Hash Table`

```kotlin
class Solution {
    private lateinit var result: IntArray
    fun countSubTrees(n: Int, edges: Array<IntArray>, labels: String): IntArray {
        result = IntArray(n)
        val graph: MutableMap<Int, MutableList<Int>> = mutableMapOf()
        for (i in 0 until n) graph[i] = mutableListOf()
        edges.forEach { edge -> 
            graph[edge[0]]!!.add(edge[1])
            graph[edge[1]]!!.add(edge[0])
        }
        dfs(0, graph, BooleanArray(n), labels)
        return result
    }
    fun dfs(current: Int, graph: Map<Int, List<Int>>, visited: BooleanArray, labels: String): IntArray {
        // mark this node as visited.
        visited[current] = true
        // initialize child-label-counter.
        val chars = IntArray(26)
        // iterate childs.
        graph[current]!!.forEach { child ->
            if (!visited[child]) {
                // if not visited, get child's accumulated label-count
                val count = dfs(child, graph, visited, labels)
                for (i in 0 until 26) chars[i] += count[i]
            }
        }
        // add current word to label-counter and backtrack
        result[current] = ++chars[labels[current] - 'a']
        return chars
    }
}
```

---


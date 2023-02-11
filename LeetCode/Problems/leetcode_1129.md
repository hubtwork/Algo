## LeetCode Problems



#### 1129. Shortest Path with Alternating Colors

- **link**  [1129. Shortest Path with Alternating Colors](https://leetcode.com/problems/shortest-path-with-alternating-colors/description/)

- **lang**  `kotlin` 
- **tags**  `Graph` `BFS`

```java
import kotlin.math.min
class Solution {
    // color values : RED = 0, BLUE = 1
    data class Instruction(val node: Int, val color: Int)
    // path-graph builder with internal color division
    class PathGraph(n: Int) {
        private val redGraph = Array<MutableSet<Int>>(n, { mutableSetOf() })
        private val blueGraph = Array<MutableSet<Int>>(n, { mutableSetOf() })
        // build graph with separate edges.
        fun buildGraph(redEdges: Array<IntArray>, blueEdges: Array<IntArray>) {
            redEdges.forEach { edge -> redGraph[edge[0]].add(edge[1]) }
            blueEdges.forEach { edge -> blueGraph[edge[0]].add(edge[1]) }
        }
        // return next visitable-nodes from current instruction.
        fun getNextPaths(inst: Instruction): Set<Int> {
            return if (inst.color == 0) blueGraph[inst.node] else redGraph[inst.node]
        }
    }

    fun shortestAlternatingPaths(n: Int, redEdges: Array<IntArray>, blueEdges: Array<IntArray>): IntArray {
        // build graph
        val graph = PathGraph(n)
        graph.buildGraph(redEdges, blueEdges)
        // build result table (first index means color)
        // all initial value is 2 * n ( maximum visit-path-length is 2n - 1 )
        val dist = Array<IntArray>(2, { IntArray(n) })
        for (i in 1 until n) {
            dist[0][i] = 2 * n
            dist[1][i] = 2 * n
        }
        // BFS starts with node 0 ( 2 separated colors )
        val queue: Queue<Instruction> = LinkedList()
        queue.add(Instruction(0, 0))
        queue.add(Instruction(0, 1))
        // iterate
        while (queue.isNotEmpty()) {
            val current = queue.poll()
            val nextColorPath = 1 - current.color
            // traverse possible-next-nodes
            graph.getNextPaths(current).forEach { next ->
                // if not yet visited, mark shortest-path ( BFS characteristics )
                if (dist[nextColorPath][next] == 2 * n) {
                    dist[nextColorPath][next] = dist[current.color][current.node] + 1
                    queue.add(Instruction(next, nextColorPath))
                }
            }
        }
        // return result of short-path. but if minimum-value is 2n, it means impossible to visit ( -1 ).
        return IntArray(n, { idx -> 
            val mini = min(dist[0][idx], dist[1][idx]) 
            if (mini == 2 * n) -1 else mini
        })
    }
}
```

---


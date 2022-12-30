## LeetCode Problems



#### 797. All Paths From Source to Target

- **link**  [797. All Paths From Source to Target](https://leetcode.com/problems/all-paths-from-source-to-target/)

- **lang**  `kotlin` 
- **tags**  `BFS` `Graph`

```kotlin
class Solution {
    fun allPathsSourceTarget(graph: Array<IntArray>): List<List<Int>> {
        val destination = graph.size-1
        // do BFS by using Queue and start with 0.
        val queue: Queue<List<Int>> = LinkedList<List<Int>>()
        queue.add(listOf(0))
        // if reached to destination, add to result
        val result = mutableListOf<List<Int>>()
        // traverse
        while (queue.isNotEmpty()) {
            for (i in 0..queue.size-1) {
                val current = queue.poll()
                // if next-edge is destination, add to result.
                // if not, add to queue for next-step.
                graph[current.last()].forEach {
                    if (it == destination) result.add(current + listOf(destination))
                    else queue.add(current + listOf(it))
                }
            }
        }
        return result
    }
}
```

---


## LeetCode Problems



#### 2359. Find Closest Node to Given Two Nodes

- **link**  [2359. Find Closest Node to Given Two Nodes](https://leetcode.com/problems/find-closest-node-to-given-two-nodes/description/)

- **lang**  `kotlin` 
- **tags**  `DFS` `Graph`

```kotlin
class Solution {
    fun closestMeetingNode(edges: IntArray, node1: Int, node2: Int): Int {
        if (node1 == node2) return node1
        val graph = Array<MutableList<Int>>(edges.size, { mutableListOf() })
        for (i in 0 until edges.size) {
            if (edges[i] != -1) graph[i].add(edges[i])
        }
        // variate node1's path and node2's path with visited, to-visit-queue
        val visit1 = BooleanArray(edges.size)
        val visit2 = BooleanArray(edges.size)
        val queue1: Queue<Int> = LinkedList<Int>()
        val queue2: Queue<Int> = LinkedList<Int>()
        queue1.add(node1)
        queue2.add(node2)
        // it can be more than one node in answer, need to return minimum index.
        val answer = mutableListOf<Int>()
        // iterate
        while (queue1.isNotEmpty() || queue2.isNotEmpty()) {
            // step by step each node.
            // node1 's step.
            for (i in 0 until queue1.size) {
                // mark visited node and enqueue to-visit-nodes.
                val n1 = queue1.poll()
                // if it's visited from node's before-step, it's answer-candidate.
                if (visit2[n1]) answer.add(n1)
                visit1[n1] = true
                graph[n1].forEach { edge ->
                    if (!visit1[edge]) queue1.add(edge)
                }
            }
            // node2 's step.
            for (i in 0 until queue2.size) {
                val n2 = queue2.poll()
                if (visit1[n2]) answer.add(n2)
                visit2[n2] = true
                graph[n2].forEach { edge ->
                    if (!visit2[edge]) queue2.add(edge)
                }
            }
            // get minimum index from candidates
            if (answer.isNotEmpty()) return answer.sorted().get(0)
        }
        return -1
    }
}
```

---


## LeetCode Problems



#### 2421. Number of Good Paths

- **link**  [2421. Number of Good Paths](https://leetcode.com/problems/number-of-good-paths/)

- **lang**  `kotlin` 
- **tags**  `Array` `Tree` `Union Find` `Graph`

```kotlin
class Solution {
    class UnionFind(size: Int) {
        private val parent: IntArray = IntArray(size, { it })
        private val rank: IntArray = IntArray(size)
        
        fun find(n: Int): Int {
            if (parent[n] != n) {
                parent[n] = find(parent[n])
            }
            return parent[n]
        }
        fun union(n1: Int, n2: Int) {
            val p1 = find(n1)
            val p2 = find(n2)
            if (p1 == p2) return
            when {
                rank[p1] > rank[p2] -> parent[p2] = p1
                rank[p1] < rank[p2] -> parent[p1] = p2
                else -> {
                    parent[p2] = p1
                    rank[p1]++
                 }
            }
        }
        
    }


    fun numberOfGoodPaths(vals: IntArray, edges: Array<IntArray>): Int {
        val size = vals.size
        val unionFind = UnionFind(size)
        val graph = Array<MutableList<Int>>(vals.size, { mutableListOf() })
        val valueMap = mutableMapOf<Int, MutableList<Int>>()
        for (i in 0 until size) {
            if (!valueMap.containsKey(vals[i])) valueMap[vals[i]] = mutableListOf()
            valueMap[vals[i]]!!.add(i)
        }
        edges.forEach { edge ->
            val a = edge[0]
            val b = edge[1]
            if (vals[a] >= vals[b]) graph[a].add(b)
            if (vals[a] <= vals[b]) graph[b].add(a)
        }

        var result = 0
        valueMap.keys.sorted().forEach { key ->
            val valNode = valueMap[key]!!
            // iterate nodes with current value
            // build disjoint-set with each neighbors
            valNode.forEach { node ->
                graph[node].forEach { neighbor ->
                    unionFind.union(node, neighbor)
                }
            }
            // get nodes' possible-group size. 
            val groupSize = mutableMapOf<Int, Int>()
            valNode.forEach { node ->
                val groupId = unionFind.find(node)
                if (!groupSize.containsKey(groupId)) groupSize[groupId] = 0
                groupSize[groupId] = groupSize[groupId]!! + 1
            }
            // result is each groupSize's nC2
            groupSize.forEach { _, size -> 
                result += size * (size + 1) / 2 
            }
        }
        return result
    }
}
```

---


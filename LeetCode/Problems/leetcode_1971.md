## LeetCode Problems



#### 1971. Find if Path Exists in Graph

- **link**  [1971. Find if Path Exists in Graph](https://leetcode.com/problems/find-if-path-exists-in-graph/description/)

- **lang**  `kotlin` 
- **tags**  `Graph` `UnionFind`

```kotlin
class UnionFind(
    size: Int
) {
    // initiate parent container
    private val parent: IntArray = IntArray(size)
    init {
        for(i in 0..size-1) { parent[i] = i }
    }
    // find method to get parent.
    fun find(n: Int): Int {
        var cursor = n
        // up to one's parent and assign as it's new parent
        while (cursor != parent[cursor]) cursor = parent[cursor]
        parent[n] = cursor
        return cursor
    }
    // union method to union each edge.
    fun union(a: Int, b: Int) {
        if (a != b) {
            // get edge's final-parent
            val ap = find(a)
            val bp = find(b)
            // connect by add one to one's child.
            parent[ap] = bp
        }
    }
    // if parent is same, is connected.
    fun areConnected(a: Int, b: Int): Boolean = find(a) == find(b)
}

class Solution {
    fun validPath(n: Int, edges: Array<IntArray>, source: Int, destination: Int): Boolean {
        val uf = UnionFind(n)
        edges.forEach { edge -> 
            uf.union(edge[0], edge[1])
        }
        return uf.areConnected(source, destination)
    }
}
```

---


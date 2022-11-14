## LeetCode Problems



#### 947. Most Stones Removed with Same Row or Column

- **link**  [947. Most Stones Removed with Same Row or Column](https://leetcode.com/problems/most-stones-removed-with-same-row-or-column/)

- **lang**  `kotlin` 
- **tags** `DFS` `Graph` `Union Find`

```kotlin
class Solution {
    inner class UnionFinder {
        private val parents = mutableMapOf<Int, Int>()
        private var _groupCount = 0
        val groupCount: Int get() = _groupCount
        // function for find parent
        private fun find(x: Int): Int {
            parents[x]?.let { parent ->
                // if parent is oneself, it's root of group
                return if (parent == x) parent
                else {
                    // if parent is not null, seek root of group
                    val rootParent = find(parent)
                    parents[x] = rootParent
                    rootParent
                }
            } ?:run {
                // if parent is null, it isn't associated.
                // assign oneself as root node.
                parents[x] = x
                _groupCount++
                return x
            }
        }
        // function for grouping
        fun union(x: Int, y: Int) {
            val rootX = find(x)
            val rootY = find(y)
            // it's connector node
            if (rootX == rootY) return
            // it's branch node
            // connect to existing group, so decrease groupCount
            parents[rootY] = rootX
            _groupCount--
        }
    }
    
    
    fun removeStones(stones: Array<IntArray>): Int {
        return stones.size - UnionFinder().apply {
            stones.forEach { stone -> union(stone[0], stone[1] + 10001) }
        }.groupCount
    }
}
```

---


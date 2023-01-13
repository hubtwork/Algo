## LeetCode Problems



#### 2246. Longest Path With Different Adjacent Characters

- **link**  [2246. Longest Path With Different Adjacent Characters](https://leetcode.com/problems/longest-path-with-different-adjacent-characters/description/)

- **lang**  `kotlin` 
- **tags**  `Array` `String` `Tree` `DFS` `Graph`

```kotlin
import kotlin.math.max
class Solution {
    private lateinit var graph: MutableMap<Int, MutableList<Int>>
    private var answer = 1
    fun longestPath(parent: IntArray, s: String): Int {
        // construct graph with each node's child group.
        graph = mutableMapOf<Int, MutableList<Int>>()
        for (i in 0 until parent.size) graph[i] = mutableListOf<Int>()
        for (i in 1 until parent.size) graph[parent[i]]!!.add(i)
        // iterate
        dfs(0, s)
        return answer
    }
    fun dfs(current: Int, s: String): Int {
        // if it's leaf node, return 1-count.
        if (graph[current]!!.isEmpty()) return 1
        // longest path can be made with 2 child-path.
        var longest_1 = 0
        var longest_2 = 0
        // iterate childs.
        graph[current]!!.forEach { next ->
            // get current child-path's longest_length
            val tmp = dfs(next, s)
            answer = max(answer, tmp)
            // if current child-path can be concatenated
            if (s[next] != s[current]) {
                // renew 2 longest child-path
                if (tmp > longest_1) {
                    longest_2 = longest_1
                    longest_1 = tmp
                } else if (tmp >= longest_2) longest_2 = tmp
            }
        }
        // renew max-longest path.
        // if pass-up to parent, longest path + 1 (current node) is longest path
        answer = max(answer, 1 + longest_1 + longest_2)
        return 1 + longest_1
    }
}
```

---


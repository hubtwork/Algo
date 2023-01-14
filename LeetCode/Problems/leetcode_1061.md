## LeetCode Problems



#### 1061. Lexicographically Smallest Equivalent String

- **link**  [1061. Lexicographically Smallest Equivalent String](https://leetcode.com/problems/lexicographically-smallest-equivalent-string/)

- **lang**  `kotlin` 
- **tags**  `String`, `Union Find`

```java
class Solution {
    class UnionFind {
        private val parent = IntArray(26, { idx -> idx })
        fun find(c: Char): Int {
            // find root-parent by loop.
            var cursor = c - 'a'
            while (cursor != parent[cursor]) cursor = parent[cursor]
            return cursor
        }
        fun union(c1: Char, c2: Char) {
            // find each param's root-parent
            val p1 = find(c1)
            val p2 = find(c2)
            // allocate lexicographical parent between two root-parents.
            when {
                p1 > p2 -> parent[p1] = p2
                p1 < p2 -> parent[p2] = p1
                else -> return
            }
        }
    }
    fun smallestEquivalentString(s1: String, s2: String, baseStr: String): String {
        // construct UnionFind
        val uf = UnionFind()
        for (idx in 0 until s1.length) uf.union(s1[idx], s2[idx])
        // find each lexicographical-parent of given string
        return baseStr.map { 'a' + uf.find(it) }.joinToString("")
    }
}
```

---


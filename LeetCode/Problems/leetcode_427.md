## LeetCode Problems



#### 427. Construct Quad Tree

- **link**  [427. Construct Quad Tree](https://leetcode.com/problems/construct-quad-tree/)

- **lang**  `kotlin` 
- **tags** `Array` `Divide and Conquer` `Tree` `Matrix`

```kotlin
/**
 * Definition for a QuadTree node.
 * class Node(var `val`: Boolean, var isLeaf: Boolean) {
 *     var topLeft: Node? = null
 *     var topRight: Node? = null
 *     var bottomLeft: Node? = null
 *     var bottomRight: Node? = null
 * }
 */

class Solution {
    fun construct(grid: Array<IntArray>): Node? {
        if (grid.isEmpty()) return null
        return constructNode(grid, 0, 0, grid.size)
    }
    // node divide and conquer method
    private fun constructNode(grid: Array<IntArray>, x: Int, y: Int, size: Int): Node {
        val node = Node(false, false)
        node.isLeaf = isLeafNode(grid, x, y, size)
        // if node is leaf, return this with no child.
        if (node.isLeaf) {
            node.`val` = (grid[x][y] == 1)
            return node
        }
        // if need to separate childs, create child conquer.
        val nextSize = size / 2
        node.`val` = true
        node.topLeft = constructNode(grid, x, y, nextSize)
        node.topRight = constructNode(grid, x, y + nextSize, nextSize)
        node.bottomLeft = constructNode(grid, x + nextSize, y, nextSize)
        node.bottomRight = constructNode(grid, x + nextSize, y + nextSize, nextSize)
        return node
    }

    private fun isLeafNode(grid: Array<IntArray>, x: Int, y: Int, size: Int): Boolean {
        if (size == 1) return true
        val value = grid[x][y]
        for (i in x until x + size) {
            for (j in y until y + size) {
                if (value != grid[i][j]) return false
            }
        }
        return true
    }
}
```

---


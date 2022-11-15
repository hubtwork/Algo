## LeetCode Problems



#### 222. Count Complete Tree Nodes

- **link**  [222. Count Complete Tree Nodes](https://leetcode.com/problems/count-complete-tree-nodes/)

- **lang**  `kotlin` 
- **tags**  `Array` `DP` `DFS` `Matrix` `Simulation`

```kotlin
/**
 * Example:
 * var ti = TreeNode(5)
 * var v = ti.`val`
 * Definition for a binary tree node.
 * class TreeNode(var `val`: Int) {
 *     var left: TreeNode? = null
 *     var right: TreeNode? = null
 * }
 */
class Solution {
    fun countNodes(root: TreeNode?): Int {
        return traverse(root)
    }
    /*
        recursive function (DFS)
        1. current = null : 0
        2. traverse left
        3. traverse right
    */
    fun traverse(node: TreeNode?): Int {
        node ?: return 0
        return 1 + traverse(node.left) + traverse(node.right)
    }
}
```

---


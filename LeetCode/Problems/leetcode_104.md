## LeetCode Problems



#### 104. Maximum Depth of Binary Tree

- **link**  [104. Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/)

- **lang**  `kotlin` 
- **tags**  `Tree` `DFS` `Binary Tree`

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
    fun maxDepth(root: TreeNode?, depth: Int = 0): Int {
      	// null type-checker
        if (root == null) return depth
      	// get left & right dfs-depth
        val left = maxDepth(root?.left, depth + 1)
        val right = maxDepth(root?.right, depth + 1)
      	// return max depth
        return if (left > right) left else right
    }
}
```

---


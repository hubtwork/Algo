## LeetCode Problems



#### 872. Leaf-Similar Trees

- **link**  [872. Leaf-Similar Trees](https://leetcode.com/problems/leaf-similar-trees/description/)

- **lang**  `kotlin` 
- **tags** `Tree` `DFS` `Binary Tree`

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
    fun leafSimilar(root1: TreeNode?, root2: TreeNode?): Boolean {
        return getLeftSequence(root1) == getLeftSequence(root2)
    }
    fun getLeftSequence(root: TreeNode?): List<Int> {
        val start = root ?: return listOf()
        val result = mutableListOf<Int>()
        // recursive traverse for find - left sequence of leaf nodes.
        fun dfs(node: TreeNode) {
            // if it's leaft node, add to result.
            if (node.left == null && node.right == null) {
                result.add(node.`val`)
                return
            }
            // for get left sequence, call left node's dfs first.
            node.left ?.let { dfs(it) }
            node.right ?.let { dfs(it) }
        }
        dfs(root)
        return result
    }
}
```

---


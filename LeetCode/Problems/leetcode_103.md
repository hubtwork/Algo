## LeetCode Problems



#### 103. Binary Tree Zigzag Level Order Traversal

- **link**  [103. Binary Tree Zigzag Level Order Traversal](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/description/)

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
    private val answerSheet = mutableListOf<MutableList<Int>>()
    private fun traverse(node: TreeNode?, level: Int) {
        node ?: return
        // add initial level-idx-list
        if (answerSheet.size <= level) answerSheet.add(mutableListOf())
        // if level is even number, it's ltr level.
        if (level % 2 == 0) answerSheet[level].add(node.`val`) else answerSheet[level].add(0, node.`val`)
        // traverse childs recursive.
        traverse(node.left, level + 1)
        traverse(node.right, level + 1)
    }
    fun zigzagLevelOrder(root: TreeNode?): List<List<Int>> {
        traverse(root, 0)
        return answerSheet
    }
}
```

---


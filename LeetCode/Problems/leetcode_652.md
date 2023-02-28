## LeetCode Problems



#### 652. Find Duplicate Subtrees

- **link**  [652. Find Duplicate Subtrees](https://leetcode.com/problems/find-duplicate-subtrees/description/)

- **lang**  `kotlin` 
- **tags**  `Hash Table` `Tree` `DFS` `Binary Tree`

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
    // map is for counter
    private val map = mutableMapOf<String, Int>()
    private val answer = mutableListOf<TreeNode>()

    fun findDuplicateSubtrees(root: TreeNode?): List<TreeNode?> {
        traverse(root)
        return answer
    }
    // traverse dfs-inorder
    fun traverse(node: TreeNode?): String {
        node ?: return ""
        val left = traverse(node.left)
        val right = traverse(node.right)
        val current = "${node.`val`}.$left.$right"
        // if it is already registered, add to answer.
        map[current] = (map[current] ?: 0).executeConditionally { answer.add(node) }
        return current
    }
    // execute and increment current number if it's duplicate node.
    private fun Int.executeConditionally(ifDuplicate: () -> Unit): Int {
        if (this == 1) ifDuplicate()
        return this + 1
    }
}
```

---


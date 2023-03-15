## LeetCode Problems



#### 958. Check Completeness of a Binary Tree

- **link**  [958. Check Completeness of a Binary Tree](https://leetcode.com/problems/check-completeness-of-a-binary-tree/)

- **lang**  `kotlin` 
- **tags** `Tree` `BFS` `Binary Tree`

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
    fun isCompleteTree(root: TreeNode?): Boolean {
        // answer must be sequential node with no null -between
        val queue: Queue<TreeNode?> = LinkedList<TreeNode?>()
        queue.add(root)
        // add child to queue by BFS until reached to null
        while (queue.peek() != null) {
            val node = queue.poll()
            queue.add(node?.left)
            queue.add(node?.right)
        }
        // if null captured, not null node must not be found.
        while (queue.isNotEmpty()) {
            if (queue.poll() != null) return false
        }
        return true
    }
}
```

---


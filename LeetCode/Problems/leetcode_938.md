## LeetCode Problems



#### 938. Range Sum of BST

- **link**  [938. Range Sum of BST](https://leetcode.com/problems/range-sum-of-bst/description/)

- **lang**  `kotlin` 
- **tags** `Tree` `DFS` `BFS` `Binary Tree`

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
    fun rangeSumBST(root: TreeNode?, low: Int, high: Int): Int {
        // DFS solution ( recursive )
        // if current is null, stop recursive calls.
        if (root == null) return 0
        // if `val` in range, return itself or if not, 0.
        // + accumulate add each traverse branches's return value
        return (if (root.`val` in low..high) root.`val` else 0) + 
            rangeSumBST(root.left, low, high) + rangeSumBST(root.right, low, high)
    }
    // + BFS solution
    fun bfs(root: TreeNode?, low: Int, high: Int): Int {
        if (root == null) return 0
        // init queue.
        var result = 0
        val queue: Queue<TreeNode> = LinkedList<TreeNode>()
        queue.add(root)
        // traverse
        while (queue.isNotEmpty()) {
            // traverse each level ( depth )
            for (i in 0..queue.size-1) {
                val node = queue.poll()
                // if `val` in range, add to result
                // add branches to queue for next level
                if (node.`val` in low..high) result += node.`val`
                if (node.left != null) queue.add(node.left)
                if (node.right != null) queue.add(node.right)
            }
        }
        return result
    }
}
```

---


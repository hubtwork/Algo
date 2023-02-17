## LeetCode Problems



#### 739. Minimum Distance Between BST Nodes

- **link**  [739. Minimum Distance Between BST Nodes](https://leetcode.com/problems/minimum-distance-between-bst-nodes/)

- **lang**  `kotlin` 
- **tags** `Tree` `DFS` `Binary Search Tree`

```kotlin
import kotlin.math.min
import kotlin.math.abs
class Solution {
    var result = 1000
    var prev: Int? = null
    // left cursor is always smaller than current
    fun minDiffInBST(root: TreeNode?): Int {
        dfs(root)
        return result
    }
    // post-order recursive search
    fun dfs(node: TreeNode?) {
        if (node == null) return
        dfs(node.left)
        // if prev is not null, check is (current - left) minimum ?
        if (prev != null) result = min(result, node.`val` - prev!!)
        // register current as prev for next iteration
        prev = node.`val`
        dfs(node.right)
    }
}
```

---


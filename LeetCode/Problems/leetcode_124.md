## LeetCode Problems



#### 124. Binary Tree Maximum Path Sum

- **link**  [124. Binary Tree Maximum Path Sum](https://leetcode.com/problems/binary-tree-maximum-path-sum/)

- **lang**  `kotlin` 
- **tags**  `Tree` `DFS` `Binary Tree`

```kotlin
import kotlin.math.max
class Solution {
    fun maxPathSum(root: TreeNode?): Int {
        var maxSum = Integer.MIN_VALUE
        fun dfs(node: TreeNode?): Int {
            if (node == null) return 0
            // get max summation of each side childs.
            // if max is when don't count the child, treat as 0 
            val lPath = max(0, dfs(node.left))
            val rPath = max(0, dfs(node.right))
            // calculate current node's connected max summation
            maxSum = max(maxSum, node.`val` + lPath + rPath)
            // return current node + max side-path
            return node.`val` + max(lPath, rPath)
        }
        dfs(root)
        return maxSum
    }
}
```

---


## LeetCode Problems



#### 129. Sum Root to Leaf Numbers

- **link**  [129. Sum Root to Leaf Numbers](https://leetcode.com/problems/sum-root-to-leaf-numbers/)

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
    private var answer = 0
    fun sumNumbers(root: TreeNode?): Int {
        dfs(root, 0)
        return answer
    }
    fun dfs(_node: TreeNode?, sum: Int) {
        val node = _node ?: return
        val curr = sum * 10 + node.`val`
        // add accumulated number to answer if it's leaf node 
        if (node.left == null && node.right == null) answer += curr
        else {
            // else dig more to child node.
            dfs(node.left, curr)
            dfs(node.right, curr)
        }
    }
}
```

---


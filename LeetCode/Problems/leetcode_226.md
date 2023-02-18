## LeetCode Problems



#### 226. Invert Binary Tree

- **link**  [226. Invert Binary Tree](https://leetcode.com/problems/invert-binary-tree/description/)

- **lang**  `kotlin` 
- **tags**  `Tree` `DFS` `Binary Tree` 

```kotlin
class Solution {
    fun invertTree(root: TreeNode?): TreeNode? {
        dfs(root)
        return root
    }
    fun dfs(node: TreeNode?): TreeNode? {
        // if reached to leaf, return null
        if (node == null) return null
        // get left node group and right node group.
        // swap it with each other for current node.
        val left = dfs(node?.left)
        node.left = dfs(node?.right)
        node.right = left
        return node
    }
}
```

---


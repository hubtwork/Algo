## LeetCode Problems



#### 144. Binary Tree Preorder Traversal

- **link**  [144. Binary Tree Preorder Traversal](https://leetcode.com/problems/binary-tree-preorder-traversal/description/)

- **lang**  `kotlin` 
- **tags**  `Tree` `DFS` `Binary Tree`

```kotlin
class Solution {
    fun preorderTraversal(root: TreeNode?): List<Int> {
        val result = mutableListOf<Int>()
        optimizedDFS(root, result)
        return result
    }
    /*
        For memory efficient, use one MutableList to contain each node's `val`.
        List-initialization like `listOf()` on each steps is memory-unefficient like below straight-forward solution.
        fun dfs(root: TreeNode?): List<Int> {
            return listOf(root.`val` ?: return) + dfs(root.left) + dfs(root.right)
        }
     */
    fun optimizedDFS(root: TreeNode?, list: MutableList<Int>) {
        root ?: return
        list.add(root.`val`)
        // preorder traversal, iterate all left -> right bottom-up 
        optimizedDFS(root.left, list)
        optimizedDFS(root.right, list)
    }
}
```

---


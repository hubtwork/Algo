## LeetCode Problems



#### 100. Same Tree

- **link**  [100. Same Tree](https://leetcode.com/problems/same-tree/)

- **lang**  `kotlin` 
- **tags**  `Tree` `DFS` `Binary Tree`

```kotlin
class Solution {
    fun isSameTree(p: TreeNode?, q: TreeNode?): Boolean {
        // case : p == q == null || p.`val` == q.`val`
        if (p == q) return true
        // case : only one is null || p.`val` != q.`val`
        if ((p == null || q == null) || (p.`val` != q.`val`)) return false
        return isSameTree(p.left, q.left) && isSameTree(p.right, q.right)
    }
}
```

---


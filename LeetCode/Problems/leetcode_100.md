## LeetCode Problems



#### 100. Same Tree

- **link**  [100. Same Tree](https://leetcode.com/problems/same-tree/)

- **lang**  `kotlin` 
- **tags**  `Tree` `DFS` `Binary Tree`

```kotlin
class Solution {
    fun isSameTree(p: TreeNode?, q: TreeNode?): Boolean {
        // check floor to avoid endless-loop
        if (p == null && q == null) return true
        // if p / q 's val ( nullable ) has same value, check each branches.
        if (p?.`val` == q?.`val`) return isSameTree(p?.left, q?.left) && isSameTree(p?.right, q?.right)
        else return false
    }
}
```

---


## LeetCode Problems



#### 1339. Maximum Product of Splitted Binary Tree

- **link**  [1339. Maximum Product of Splitted Binary Tree](https://leetcode.com/problems/maximum-product-of-splitted-binary-tree/description/)

- **lang**  `kotlin` 
- **tags**  `Tree` `DFS` `Binary Tree`

```kotlin
import kotlin.math.max
class Solution {
    fun maxProduct(root: TreeNode?): Int {
        val sums = mutableListOf<Long>()
        // traverse to memorize each sums and get total sum
        fun dfs(node: TreeNode?): Long {
            node ?: return 0
            // get each node's traversal sum 
            val leftSum = dfs(node.left)
            val rightSum = dfs(node.right)
            // add each sums all child nodes.
            val sum = leftSum + rightSum + node!!.`val`
            sums.add(sum)
            return sum
        }
        var maxProduct: Long = 0L
        val totalSum: Long = dfs(root)
        /*
            upon process, we know all sums of each node's all childs.
            if n-th node's child sum is k, 
            product of current divided subtree is ( k * (total - k) )
         */
        sums.forEach { sum ->
            val product = sum * (totalSum - sum)
            maxProduct = max(maxProduct, product)
        }
        return (maxProduct % 1000000007).toInt()
    }
}
```

---


## LeetCode DataStructure StudyPlan

<img src="../../assets/leetcode_ds_lv1_day11.png" alt="leetcode_data_structure_level1_day11" style="zoom:50%;" />

### Day 11

- [102. Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/?envType=study-plan&id=data-structure-i)
- [104. Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/?envType=study-plan&id=data-structure-i)
- [101. Symmetric Tree](https://leetcode.com/problems/symmetric-tree/?envType=study-plan&id=data-structure-i)

---

#### 102. Binary Tree Level Order Traversal

- **lang**  `kotlin` 
- **tags**  `Tree` `BFS`  `Binary Tree`

```kotlin
class Solution {
    fun levelOrder(root: TreeNode?): List<List<Int>> {
        // run BFS with queue
        val queue: Queue<TreeNode> = LinkedList<TreeNode>()
        queue.add(root ?: return listOf())
        val result = mutableListOf<List<Int>>()
        // traverse
        while (queue.isNotEmpty()) {
            // initialize each level's container before loop
            val container = mutableListOf<Int>()
            for (i in 0..queue.size-1) {
                // get node from queue and add to container, childs to queue
                val node = queue.poll()
                container.add(node.`val`)
                node.left ?.let { queue.add(it) }
                node.right ?.let { queue.add(it) }
            }
            result.add(container)
        }
        return result
    }
}
```

---


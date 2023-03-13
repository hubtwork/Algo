## LeetCode Problems



#### 101. Symmetric Tree

- **link**  [101. Symmetric Tree](https://leetcode.com/problems/symmetric-tree/)

- **lang**  `kotlin` 
- **tags**  `Tree` `BFS` `Binary Tree`

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
    /*
        main logic:
        symmetric means "divided half and same with reverse order of counter side."
        so, check each level's left and right node groups and check symmetry.
        // check same of `val`, treat null as OutOfIndexValue.
        (1) ex) if not same : not symmetric
        (2) ex) if same, but null : don't need to check that leaves.
        (3) ex) if same, not null : insert queue to check next level.
     */
    fun isSymmetric(root: TreeNode): Boolean {
        // calculate for root.
        val queue: Queue<TreeNode> = LinkedList<TreeNode>()
        if (isNotSameNode(root.left, root.right)) return false
        if (root.left == null) return true
        queue.add(root.left!!)
        queue.add(root.right!!)
        // traverse
        while(queue.isNotEmpty()) {
            // check each level ( depth )
            for (i in 0 until queue.size/2) {
                // poll two counterside nodes and compare
                val first = queue.poll()
                val second = queue.poll()
                // check left-side's left child and right-side's right child 
                if (isNotSameNode(first.left, second.right)) return false
                else if (first.left != null) {
                    queue.add(first.left!!)
                    queue.add(second.right!!)
                }
                // check left-side's right child and right-side's left child
                if (isNotSameNode(first.right, second.left)) return false
                else if (first.right != null) {
                    queue.add(first.right!!)
                    queue.add(second.left!!)
                }
            }
        }
        return true
    }
    /** Calculate function if given node is not same with null handling */
    fun isNotSameNode(n1: TreeNode?, n2: TreeNode?): Boolean {
        return if ((n1?.`val`?: -101) != (n2?.`val`?: -101)) true else false
    }
}
```

---


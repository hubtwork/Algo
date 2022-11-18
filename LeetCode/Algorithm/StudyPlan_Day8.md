## LeetCode Algorithm StudyPlan

<img src="/Users/alenheo/Desktop/repo/algo/assets/leetcode_study_day8.png" alt="leetcode_study_day8" style="zoom:50%;" />

### Day 8

- [617. Merge Two Binary Trees](https://leetcode.com/problems/merge-two-binary-trees/?envType=study-plan&id=algorithm-i)
- [116. Populating Next Right Pointers in Each Node](https://leetcode.com/problems/populating-next-right-pointers-in-each-node/?envType=study-plan&id=algorithm-i)

---

#### 617. Merge Two Binary Trees

- **lang**  `kotlin` 
- **tags**  `Tree` `DFS` `BFS` `Binary Tree` 

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
    fun mergeTrees(root1: TreeNode?, root2: TreeNode?): TreeNode? {
        if (root1 == null) return root2
        if (root2 == null) return root1
        // merge root node first.
        var head1 = root1
        var head2 = root2
        head1.`val` += head2.`val`
        traverse(head1, head2)
        return root1
    }
    // perform dfs
    // merge node2 to node1.
    fun traverse(node1: TreeNode, node2: TreeNode) {
        // traverse left
        if (node2.left != null) {
            /*
                node2.left == null : current node's left is just node1.left, so stop traverse
                node1.left == null : merge node2.left to current node's left
                node1.left != null : sum node1.left, node2.left and traverse downward
            */
            if (node1.left == null) node1.left = node2.left
            else {
                node1.left.`val` += node2.left.`val`
                traverse(node1.left, node2.left)
            }
        }
        // traverse right
        // same as left
        if (node2.right != null) {
            if (node1.right == null) node1.right = node2.right
            else {
                node1.right.`val`+= node2.right.`val`
                traverse(node1.right, node2.right)
            }
        }
    }
}
```

---


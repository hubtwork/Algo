## LeetCode DataStructure StudyPlan

<img src="../../assets/leetcode_ds_lv1_day10.png" alt="leetcode_data_structure_level1_day10" style="zoom:50%;" />

### Day 10

- [144. Binary Tree Preorder Traversal](https://leetcode.com/problems/binary-tree-preorder-traversal/?envType=study-plan&id=data-structure-i)
- [94. Binary Tree Inorder Traversal](https://leetcode.com/problems/binary-tree-inorder-traversal/?envType=study-plan&id=data-structure-i)
- [145. Binary Tree Postorder Traversal](https://leetcode.com/problems/binary-tree-postorder-traversal/?envType=study-plan&id=data-structure-i)

---

#### 144. Binary Tree Preorder Traversal

- **lang**  `kotlin` 
- **tags**  `Stack` `DFS` `Tree` `Binary Tree`

```kotlin
class Solution {
    fun preorderTraversal(root: TreeNode?): List<Int> {
        // return recursiveDfs(root)
        return iterativeDfs(root)
    }
    /* 
        DFS : Recursive.
        get all left-first traversed list and right traversed list
     */
    fun recursiveDfs(root: TreeNode?): List<Int> {
        root ?: return listOf()
        return listOf(root.`val`) + preorderTraversal(root.left) + preorderTraversal(root.right)
    }
    /*
        DFS : Iterative.
        contrary to BFS with 'Queue', DFS have to use 'Stack'.
     */
    fun iterativeDfs(root: TreeNode?): List<Int> {
        root ?: return listOf()
        val result = mutableListOf<Int>()
        val stack = Stack<TreeNode>()
        stack.add(root)
        // traverse
        while (stack.isNotEmpty()) {
            val node = stack.pop()
            result.add(node.`val`)
            // to traverse first on left, add right first.
            node.right?.let { stack.push(it) }
            node.left?.let { stack.push(it) }
        }
        return result
    }
}
```

---

#### 94. Binary Tree Inorder Traversal

- **lang**  `kotlin` 
- **tags**  `Stack` `DFS` `Tree` `Binary Tree`

```kotlin
class Solution {
    fun inorderTraversal(root: TreeNode?): List<Int> {
        // return recursiveDfs(root)
        return iterativeDfs(root)
    }
    fun recursiveDfs(root: TreeNode?): List<Int> {
        root ?: return listOf()
        return recursiveDfs(root.left) + listOf(root.`val`) + recursiveDfs(root.right)
    }
    fun iterativeDfs(root: TreeNode?): List<Int> {
        val result = mutableListOf<Int>()
        var cursor = root
        val stack = Stack<TreeNode>()
        // traverse until non-empty-stack & cursor exists
        while (stack.isNotEmpty() || cursor != null) {
            /*
                for iterative inorder traversal
                # if possible to go down to left, enroll each node to stack.
                # from left bottom, up to top cursor with traverse each's right nodes.
             */
            if (cursor != null) {
                stack.push(cursor)
                cursor = cursor.left
            } else {
                cursor = stack.pop()
                cursor?.let { result.add(it.`val`) }
                cursor = cursor.right
            }
        }
        return result
    }
}
```

---

#### 145. Binary Tree Postorder Traversal

- **lang**  `kotlin` 
- **tags**  `Stack` `DFS` `Tree` `Binary Tree`

```kotlin
class Solution {
    fun postorderTraversal(root: TreeNode?): List<Int> {
        // return recursiveDfs(root)
        return iterativeDfs(root)
    }
    fun recursiveDfs(root: TreeNode?): List<Int> {
        root ?: return listOf()
        return recursiveDfs(root.left) + recursiveDfs(root.right) + listOf(root.`val`)
    }
    fun iterativeDfs(root: TreeNode?): List<Int> {
        val result = mutableListOf<Int>()
        var cursor: TreeNode? = root
        var prev: TreeNode? = null
        val stack = Stack<TreeNode>()
        while (stack.isNotEmpty() || cursor != null) {
            /*
                for iterative inorder traversal
                # if possible to go down to left, enroll each node to stack.
                # traverse
                    1) from last saved node, move down to last right node.
                    2) save already read cursor to prev and traverse reverse order.
             */
            if (cursor != null) {
                stack.push(cursor)
                cursor = cursor.left
            } else {
                cursor = stack.peek()
                if (cursor.right == null || cursor.right == prev) {
                    result.add(cursor.`val`)
                    stack.pop()
                    prev = cursor
                    cursor = null
                } else cursor = cursor.right
            }
        }
        return result
    }
}
```

---


## LeetCode ProgrammingSkills StudyPlan

<img src="../../assets/leetcode_program_lv1_day10.png" alt="leetcode_programming_skills_level1_day10" style="zoom:50%;" />

### Day 10

- [1290. Convert Binary Number in a Linked List to Integer](https://leetcode.com/problems/convert-binary-number-in-a-linked-list-to-integer/?envType=study-plan&id=programming-skills-i)
- [876. Middle of the Linked List](https://leetcode.com/problems/middle-of-the-linked-list/?envType=study-plan&id=programming-skills-i)
- [104. Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/?envType=study-plan&id=programming-skills-i)
- [404. Sum of Left Leaves](https://leetcode.com/problems/sum-of-left-leaves/?envType=study-plan&id=programming-skills-i)

---

#### 1290. Convert Binary Number in a Linked List to Integer

- **lang**  `kotlin` 
- **tags**  `LinkedList` `Math`

```kotlin
/**
 * Example:
 * var li = ListNode(5)
 * var v = li.`val`
 * Definition for singly-linked list.
 * class ListNode(var `val`: Int) {
 *     var next: ListNode? = null
 * }
 */
class Solution {
    fun getDecimalValue(head: ListNode?): Int {
        var result = 0
        var node = head
        // add `val` from each node and shift left to make result
        while(node != null) {
            result = result.shl(1) + node.`val`
            node = node.next
        }
        return result
    }
}
```

---

#### 876. Middle of the Linked List

- **lang**  `kotlin` 
- **tags**  `LinkedList` `Two Pointers`

```kotlin
/**
 * Example:
 * var li = ListNode(5)
 * var v = li.`val`
 * Definition for singly-linked list.
 * class ListNode(var `val`: Int) {
 *     var next: ListNode? = null
 * }
 */
class Solution {
    fun middleNode(head: ListNode?): ListNode? {
        var front = head
        var back = head
        // move 2step on front node
        // move 1step on back node, it will stop at middle node. ( 2 : 1 ) =
        while (front?.next != null) {
            front = front?.next?.next
            back = back?.next
        }
        return back
    }
}
```

---

#### 404. Sum of Left Leaves

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
    fun maxDepth(root: TreeNode?): Int {
        val queue: Queue<TreeNode> = LinkedList<TreeNode>().apply {
            // if root is null, depth is 0
            add(root ?: return 0)
        }
        var depth = 0
        while (queue.isNotEmpty()) {
            // consume all elements in queue
            for (i in 0..queue.size-1) {
                // add each exist childs to queue
                val node = queue.poll()
                node.left ?.let { queue.add(it) }
                node.right ?.let { queue.add(it) }
            }
            depth ++
        }
        return depth
    }
}
```

---

#### 104. Maximum Depth of Binary Tree

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
    fun sumOfLeftLeaves(root: TreeNode?): Int {
        var result = 0
        fun dfs(node: TreeNode) {
            // check left
            node.left ?.let { left ->
                // if left has no childs, it's left leaf
                if (left.left == null && left.right == null) result += left.`val`
                else dfs(left)
            }
            // check right
            node.right ?.let { right -> dfs(right) }
        }
        dfs(root ?: return 0)
        return result
    }
}
```

---


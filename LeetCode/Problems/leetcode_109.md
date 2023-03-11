## LeetCode Problems



#### 109. Convert Sorted List to Binary Search Tree

- **link**  [109. Convert Sorted List to Binary Search Tree](https://leetcode.com/problems/convert-sorted-list-to-binary-search-tree/)

- **lang**  `kotlin` 
- **tags**  `Linked List` `Divide and Conquer` `Binary Search Tree`

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
    fun sortedListToBST(head: ListNode?): TreeNode? {
        return helper(head, null)
    }
    fun helper(head: ListNode?, tail: ListNode?): TreeNode? {
        // if head == tail, there' no needs for building treenode.
        if (head == tail) return null
        var slow: ListNode? = head
        var fast: ListNode? = head
        // move slow and fast ( x2 ) until fast is reached to tail.
        while(fast != tail && fast?.next != tail) {
            slow = slow?.next
            fast = fast?.next?.next
        }
        // build treeNode and recursive build each childs
        val node = TreeNode(slow!!.`val`)
        node.left = helper(head, slow)
        node.right = helper(slow.next, tail)
        return node
    }
}
```

---


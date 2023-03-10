## LeetCode Problems



#### 142. Linked List Cycle II

- **link**  [142. Linked List Cycle II](https://leetcode.com/problems/linked-list-cycle-ii/description/)

- **lang**  `kotlin` 
- **tags**  `Hash Table` `DFS` `Binary Tree`

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
    fun detectCycle(head: ListNode?): ListNode? {
        var cursor: ListNode? = head ?: return null
        var normal: ListNode? = cursor
        var fast: ListNode? = cursor
        // use fast forward node comparison
        while (fast?.next != null && fast?.next?.next != null) {
            normal = normal?.next
            fast = fast?.next?.next
            // if fast forward node catch normal node, it means has cycle.
            if (normal == fast) {
                // move cursor and fast node until meet together by cycle
                while (cursor != fast) {
                    cursor = cursor?.next
                    fast = fast?.next
                }
                return cursor
            }
        }
        return null
    }
}
```

---


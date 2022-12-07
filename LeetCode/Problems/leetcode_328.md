## LeetCode Problems



#### 328. Odd Even Linked List

- **link**  [328. Odd Even Linked List](https://leetcode.com/problems/odd-even-linked-list/description/)

- **lang**  `kotlin` 
- **tags**  `Linked List`

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
    fun oddEvenList(head: ListNode?): ListNode? {
        // init dummy node for track
        val oddHead = ListNode(0)
        val evenHead = ListNode(0)
        var oddCursor: ListNode? = oddHead
        var evenCursor: ListNode? = evenHead
        var mainCursor = head
        // traverse
        while (mainCursor != null) {
            // attach each nodes
            oddCursor?.next = mainCursor
            evenCursor?.next = mainCursor?.next
            oddCursor = oddCursor?.next
            evenCursor = evenCursor?.next
            // move cursor every 2 steps
            mainCursor = mainCursor.next?.next
        }
        // attach even nodes to end of odd nodes
        oddCursor?.next = evenHead.next
        return oddHead.next
    }
}
```

---


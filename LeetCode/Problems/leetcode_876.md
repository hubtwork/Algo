## LeetCode Problems



#### 876. Middle of the Linked List

- **link**  [876. Middle of the Linked List](https://leetcode.com/problems/middle-of-the-linked-list/)

- **lang**  `kotlin` 
- **tags** `Linked List` `Two Pointers`

```kotlin
class Solution {
    fun middleNode(head: ListNode?): ListNode? {
        var front = head
        var back = head
        // move 2step on front node
        // move 1step on back node, it will stop at middle node. ( 2 : 1 )
        while (front?.next != null) {
            front = front?.next?.next
            back = back?.next
        }
        return back
    }
}
```

---


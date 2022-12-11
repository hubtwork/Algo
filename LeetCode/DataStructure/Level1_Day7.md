## LeetCode DataStructure StudyPlan

<img src="../../assets/leetcode_ds_lv1_day7.png" alt="leetcode_data_structure_level1_day7" style="zoom:50%;" />

### Day 7

- [141. Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/?envType=study-plan&id=data-structure-i)
- [21. Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/?envType=study-plan&id=data-structure-i)
- [203. Remove Linked List Elements](https://leetcode.com/problems/remove-linked-list-elements/?envType=study-plan&id=data-structure-i)

---

#### 141. Linked List Cycle

- **lang**  `kotlin` 
- **tags**  `Hash Table` `Linked List` `Two Pointers`

```kotlin
class Solution {
    fun hasCycle(head: ListNode?): Boolean {
        // like two pointers, two node cursor used.
        var fast = head
        var slow = head
        // if fast-forward cursor is pointing same node with following cursor,
        // it means cycle exists in linked list.
        while (fast != null && fast?.next != null) {
            fast = fast?.next?.next
            slow = slow?.next
            if (fast == slow) return true
        }
        return false
    }
}
```

---


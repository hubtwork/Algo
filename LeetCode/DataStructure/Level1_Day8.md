## LeetCode DataStructure StudyPlan

<img src="../../assets/leetcode_ds_lv1_day8.png" alt="leetcode_data_structure_level1_day8" style="zoom:50%;" />

### Day 8

- [206. Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/?envType=study-plan&id=data-structure-i)
- [83. Remove Duplicates from Sorted List](https://leetcode.com/problems/remove-duplicates-from-sorted-list/?envType=study-plan&id=data-structure-i)

---

#### 206. Reverse Linked List

- **lang**  `kotlin` 
- **tags** `Linked List` `Recursion`

```kotlin
class Solution {
    fun reverseList(head: ListNode?): ListNode? {
        var root: ListNode? = null
        var reader = head
        // traverse
        while (reader != null) {
            // construct one-by-one backward.
            val cursor = ListNode(reader.`val`)
            cursor.next = root
            // move root cursor to current cursor
            // -> add operation like stack
            root = cursor
            reader = reader.next
        }
        return root
    }
}
```

---


## LeetCode Problems



#### 382. Linked List Random Node

- **link**  [382. Linked List Random Node](https://leetcode.com/problems/linked-list-random-node/)

- **lang**  `kotlin` 
- **tags**  `Resorvoir Sampling`  `Math` `Random`

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
class Solution(private val head: ListNode) {
    // use Reservoir Sampling to extract random element from anonymous collection.
    private fun Int.reservoirHelper(): Boolean = Math.random() < (1.0 / this)
    
    fun getRandom(): Int {
        var node: ListNode? = head.next
        var result = head.`val`
        var count = 1
        while (node != null) {
            // if current value is randomly picked, replace result with it
            if ((++count).reservoirHelper()) result = node.`val`
            node = node.next
        }
        return result
    }
}

/**
 * Your Solution object will be instantiated and called as such:
 * var obj = Solution(head)
 * var param_1 = obj.getRandom()
 */
```

---


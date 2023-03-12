## LeetCode Problems



#### 23. Merge k Sorted Lists

- **link**  [23. Merge k Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/)

- **lang**  `kotlin` 
- **tags**  `LinkedList` `Divide and Conquer` `Heap (Priority Queue)` `Merge Sort`

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
    fun mergeKLists(lists: Array<ListNode?>): ListNode? {
        // return withMapAndList(lists)
      	return withPQ(lists)
    }
    fun withMapAndList(lists: Array<ListNode?>): ListNode? {
        // Step 1. record counts of each `val` in all ListNodes.
        val countMap = mutableMapOf<Int, Int>()
        lists.forEach { node ->
            var cursor = node
            while(cursor != null) {
                countMap[cursor.`val`] = countMap.getOrDefault(cursor.`val`, 0) + 1
                cursor = cursor.next
            }   
        }
        // Step 2. get sorted `val` line-up
        val members = countMap.keys.sorted()
        val first = members.getOrNull(0)
        if (first == null) return null
        val rootNode: ListNode = ListNode(first)
        var temp: ListNode = rootNode
        countMap[first] = countMap[first]!! - 1
        // Step 3. traverse each `val`s, create and connect new ListNode based on counts.
        for (n in 0..members.size-1) {
            val mem = members[n]
            for (i in 0..countMap[mem]!!-1) {
                temp.next = ListNode(mem)
                temp = temp.next!!
            }
        }
        return rootNode
    }
    fun withPQ(lists: Array<ListNode?>): ListNode? {
        // use PriorityQueue to get sorted merged lists.
        val pq = PriorityQueue<Pair<Int, ListNode>> { x, y -> x.first - y.first}
        // iterate and build merged lists.
        for (el in lists) {
            var node = el
            while (node != null) {
                pq.add(node.`val` to ListNode(node.`val`))
                node = node.next
            }
        }
        // pick one by one from pq and build.
        // use empty head to calculate easy.
        val head = ListNode(0)
        var node = head ?: return null
        while (pq.isNotEmpty()) {
            node.next = pq.poll().second
            node = node.next
        }
        return head.next
    }
}
```

---


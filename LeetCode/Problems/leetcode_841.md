## LeetCode Problems



#### 841. Keys and Rooms

- **link**  [841. Keys and Rooms](https://leetcode.com/problems/keys-and-rooms/description/)

- **lang**  `kotlin` 
- **tags**  `BFS` `Graph`

```kotlin
class Solution {
    fun canVisitAllRooms(rooms: List<List<Int>>): Boolean {
        // check each room is opened, and keys
        var opened = BooleanArray(rooms.size, { false })
        val queue: Queue<Int> = LinkedList<Int>()
        queue.add(0)
        // traverse ( BFS )
        while (queue.isNotEmpty()) {
            // get key from pocket and open the room
            val key = queue.poll()
            opened[key] = true
            // get keys from opened room.
            rooms[key].forEach { k -> if (!opened[k]) queue.add(k) }
        }
        // if closed room exist, return false
        opened.forEach { if (!it) return false }
        return true
    }
}
```

---


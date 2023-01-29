## LeetCode Problems



#### 460. LFU Cache

- **link**  [460. LFU Cache](https://leetcode.com/problems/lfu-cache/)

- **lang**  `kotlin` 
- **tags** `Hash Table` `Linked List` `Design`

```kotlin
class LFUCache(private val capacity: Int) {
    // cache data model
    data class Data(val key: Int, val value: Int, val time: Int, val hits: Int)
    // ordered box key order = (1) value (2) hits (3) time (4) key
    private val map = mutableMapOf<Int, Data>()
    private val orderedData = TreeSet<Data>(compareBy({it.hits}, {it.time}))
    private var time = 0

    fun get(key: Int): Int? {
        // if data is not in internal box, return -1
        val data = map[key] ?: return -1
        // if key-data is not in orderedData, return null
        if(!orderedData.remove(data)) return null
        // add new Data
        val newData = Data(key, data.value, time, data.hits + 1)
        orderedData.add(newData)
        map[key] = newData
        time++
        return newData.value
    }

    fun put(key: Int, value: Int) {
        // if capacity is 0, return
        if (capacity == 0) return
        val data = map[key]
        // if data is in internal box, remove it
        // if internal box is full and new data is not in box, poll
        if (data != null) orderedData.remove(data)
        else if (map.size == capacity && data == null) {
            val lfu = orderedData.pollFirst()
            if (map.remove(lfu.key) == null) return
        }
        // add new Data
        val newItem = Data(key, value, time, (data?.hits ?: 0) + 1)
        orderedData.add(newItem)
        map[key] = newItem
        time++
    }

}

/**
 * Your LFUCache object will be instantiated and called as such:
 * var obj = LFUCache(capacity)
 * var param_1 = obj.get(key)
 * obj.put(key,value)
 */
```

---


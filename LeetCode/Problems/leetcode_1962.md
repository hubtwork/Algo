## LeetCode Problems



#### 1962. Remove Stones to Minimize the Total

- **link**  [1962. Remove Stones to Minimize the Total](https://leetcode.com/problems/remove-stones-to-minimize-the-total/)

- **lang**  `kotlin` 
- **tags**  `Array` `Heap(PQ)` 

```kotlin
import kotlin.math.ceil
class Solution {
    fun minStoneSum(piles: IntArray, k: Int): Int {
        // construct Max-Heap and add piles.
        val maxHeap = PriorityQueue<Int>(piles.size) { o1, o2 -> o2.compareTo(o1) }
        piles.forEach { maxHeap.add(it) }
        // iterate in range(k)
        for (i in 0..k-1) {
            // if calc-result > 0 : add again.
            maxHeap.add(ceil(maxHeap.poll().toFloat() / 2).toInt())
        }
        return maxHeap.sum()
    }
}
```

---


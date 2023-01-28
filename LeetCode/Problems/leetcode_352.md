## LeetCode Problems



#### 352. Data Stream as Disjoint Intervals

- **link**  [352. Data Stream as Disjoint Intervals](https://leetcode.com/problems/data-stream-as-disjoint-intervals/description/)

- **lang**  `kotlin` 
- **tags**  `Binary Search`  `Design` `Order and Set`

```kotlin
class SummaryRanges() {
    // use treeMap for sorted map
    private val treeMap = TreeMap<Int, IntArray>()
    
    fun addNum(value: Int) {
        // get interval below of given value 
        var rangeBelow: IntArray? = treeMap.floorEntry(value)?.value
        // get interval above of given value
        val rangeAbove: IntArray? = treeMap.remove(value + 1)
        // if above-range exists, composite interval
        val end = if (rangeAbove == null) value else rangeAbove[1]
        // if below-range is null or below-range's end can't concat with current value
        if (rangeBelow == null || rangeBelow[1] < value - 1) {
            // add new range to map
            treeMap[value] = intArrayOf(value, end)
        } else if (rangeBelow[1] == value - 1) {
            // if below-range is concatable with current given value, concat to origin
            rangeBelow[1] = end
        }
    }
    fun getIntervals(): Array<IntArray> {
        return treeMap.values.toTypedArray()
    }

}

/**
 * Your SummaryRanges object will be instantiated and called as such:
 * var obj = SummaryRanges()
 * obj.addNum(value)
 * var param_2 = obj.getIntervals()
 */
```

---


## LeetCode Problems



#### 451. Sort Characters By Frequency

- **link**  [451. Sort Characters By Frequency](https://leetcode.com/problems/sort-characters-by-frequency/)

- **lang**  `kotlin` 
- **tags**  `Hash Table` `String` `Sorting` `Heap` `Counting`

```kotlin
class Solution {
    fun frequencySort(s: String): String {
        var result = mutableListOf<Char>()
        // to sort map
        LinkedList(
            // create map
            mutableMapOf<Char, Int>().apply {
                // count each character's occurance
                s.forEach { c -> 
                    this[c] ?.let { this[c] = this[c]!! + 1 } ?: run { this[c] = 1 }
                }
            }.entries
        )
            .sortedByDescending { it.value }    // sort map.entries by count's decreasing order
            .forEach { (k, v) ->
                // add each character with repeat by count
                for (i in 1..v) result.add(k)
            }
        return result.joinToString("")
    }
}
```

---


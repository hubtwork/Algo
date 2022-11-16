## LeetCode Problems



#### 187. Repeated DNA Sequences

- **link**  [187. Repeated DNA Sequences](https://leetcode.com/problems/repeated-dna-sequences/)

- **lang**  `kotlin` 
- **tags**  `Hash Table`  `String` `Sliding Window` 

```kotlin
class Solution {
    fun findRepeatedDnaSequences(s: String): List<String> {
        // each dna require length 10
        if (s.length < 10) return listOf()
        val dnaMap = mutableMapOf<String, Int>()
        val result = mutableListOf<String>()
        // traverse all dna
        // if dna count is 1 = add on
        for (i in 0..s.length-10) {
            val currentDna = s.substring(i, i+10)
            if (dnaMap[currentDna] == null) dnaMap[currentDna] = 1
            else {
                if (dnaMap[currentDna] == 1) result.add(currentDna)
                dnaMap[currentDna] = dnaMap[currentDna]!! + 1
            }
        }
        return result
    }
}
```

---


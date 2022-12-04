## LeetCode Problems



#### 1657. Determine if Two Strings Are Close

- **link**  [1657. Determine if Two Strings Are Close](https://leetcode.com/problems/determine-if-two-strings-are-close/)

- **lang**  `kotlin` 
- **tags**  `Hash Table` `String` `Sorting`

```kotlin
class Solution {
    fun closeStrings(word1: String, word2: String): Boolean {
        /*
            [rule]
            1) same length
            2) same characters' occurrence
            3) same count elements ( unconstrained to alphabet )
        */
        if (word1.length != word2.length) return false
        // occurrence DS
        val occur1 = mutableSetOf<Char>()
        val occur2 = mutableSetOf<Char>()
        // count DS
        val count1 = IntArray(26)
        val count2 = IntArray(26)
        // traverse
        for (i in 0..word1.length-1) {
            // register occurrence
            occur1.add(word1[i])
            occur2.add(word2[i])
            // register count
            count1[word1[i] - 'a'] ++
            count2[word2[i] - 'a'] ++
        }
        // sort each count for compare
        count1.sort()
        count2.sort()
        return if (occur1 == occur2 && count1 contentEquals count2) true else false
    }
}
```

---


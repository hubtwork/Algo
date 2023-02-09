## LeetCode Problems



#### 2306. Naming a Company

- **link**  [2306. Naming a Company](https://leetcode.com/problems/naming-a-company/)

- **lang**  `kotlin` 
- **tags**  `Array` `Hash Table` `String` `Enumeration`

```kotlin
class Solution {
    fun distinctNames(ideas: Array<String>): Long {
        val wordSet = mutableSetOf<String>()
        ideas.forEach { word -> wordSet.add(word) }

        val counter = Array<LongArray>(26, { LongArray(26) })
        // register possible transformed-ideas to counter
        ideas.forEach { _idea ->
            val idea = _idea.toCharArray()
            val origin = idea[0]
            // count possible transformed-word of each word
            // counter[origin][transformed] means number of possible new idea
            for (initial in 0 until 26) {
                if ('a' + initial != origin) {
                    idea[0] = 'a' + initial 
                    if (!wordSet.contains(String(idea))) counter[origin - 'a'][initial] ++
                }
            }
        }
        // count each possible-pair.
        var answer: Long = 0L
        for (origin in 0 until 26) {
            for (partner in 0 until 26) {
                // possible pair is counter[origin][partner] count * counter [parter][origin] count
                answer += counter[origin][partner] * counter[partner][origin]
            }
        }
        return answer
    }
}
```

---


## LeetCode Problems



#### 211. Design Add and Search Words Data Structure

- **link**  [211. Design Add and Search Words Data Structure](https://leetcode.com/problems/design-add-and-search-words-data-structure/)

- **lang**  `kotlin` 
- **tags**  `Design` `String` `Trie`

```kotlin
class WordDictionary() {

    data class Trie(
        val map: MutableMap<Char, Trie> = mutableMapOf<Char, Trie>()
    ) {
        operator fun plus(c: Char): Trie {
            if (!map.containsKey(c)) map[c] = Trie()
            return map[c]!!
        }
        fun markEnd() { map['*'] = Trie() }
        fun next(c: Char): Trie? = map[c]
        // search helper method
        fun searchWord(word: String, idx: Int = 0): Boolean {
            // if it's last character, return it's end of word in dictionary.
            if (idx == word.length) return map['*'] != null
            // if meet dot(.), iterate all searching for current childs.
            if (word[idx] == '.') {
                for (child in map.values) {
                    if (child.searchWord(word, idx + 1)) return true
                }
            }
            // else, return its child's validation
            return map[word[idx]]?.searchWord(word, idx + 1) ?: false
        }
    }

    private val root = Trie()

    fun addWord(word: String) {
        var node = root
        word.forEach { c ->
            node += c
        }
        node.markEnd()
    }

    fun search(word: String): Boolean {
        return root.searchWord(word)
    }

}

/**
 * Your WordDictionary object will be instantiated and called as such:
 * var obj = WordDictionary()
 * obj.addWord(word)
 * var param_2 = obj.search(word)
 */
```

---


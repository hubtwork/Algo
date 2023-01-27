## LeetCode Problems



#### 472. Concatenated Words

- **link**  [472. Concatenated Words](https://leetcode.com/problems/concatenated-words/)

- **lang**  `kotlin` 
- **tags** `Array` `DP` `Trie`

```kotlin
class Solution {
    data class Trie(
        val next: MutableMap<Char, Trie> = mutableMapOf<Char, Trie>()
    ) {
        private var _isTerminal: Boolean = false
        val isTerminal: Boolean get() = _isTerminal
        fun markTerminal() { _isTerminal = true }
    }
    
    fun findAllConcatenatedWordsInADict(words: Array<String>): List<String> {
        val answer = mutableSetOf<String>()
        val node = Trie()
        // build Trie
        words.forEach { addTrie(node, it, 0) }
        // check is it concatnated-string
        words.forEach { if (isConcatenated(it, 0, node, false)) answer.add(it) }
        return answer.toList()
    }
    // BUILD TRIE NODE SET.
    fun addTrie(node: Trie, word: String, idx: Int) {
        if (!node.next.contains(word[idx])) node.next[word[idx]] = Trie()
        val next = node.next[word[idx]]!!
        // if it's end of given word, mark it as one's terminal character.
        if (idx == word.length-1) next.markTerminal()
        else addTrie(next, word, idx + 1)
    }
    // CHECK IS IT CONCATENATED.
    fun isConcatenated(word: String, idx: Int, node: Trie, isAfterFirst: Boolean): Boolean {
        var current = node
        var cursor = idx
        // traverse
        while (cursor < word.length) {
            // if no one, it's not concatenated.
            if (!current.next.contains(word[cursor])) return false
            current = current.next[word[cursor]]!!
            // if it's combined by trie-sub-node, return true
            if (current.isTerminal && isConcatenated(word, cursor + 1, node, true)) return true
            cursor++
        }
        return isAfterFirst && current.isTerminal
    }
}
```

---


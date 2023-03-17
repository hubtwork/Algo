## LeetCode Problems



#### 208. Implement Trie (Prefix Tree)

- **link**  [208. Implement Trie (Prefix Tree)](https://leetcode.com/problems/implement-trie-prefix-tree/)

- **lang**  `kotlin` 
- **tags**  `Design` `String` `Trie` 

```kotlin
class Trie() {
    data class Node(
        val map: MutableMap<Char, Node> = mutableMapOf<Char, Node>()
    ) {
        // override plus opertor to construct next node function
        operator fun plus(ch: Char): Node {
            return map.get(ch) ?: run {
                map[ch] = Node()
                map[ch]!!
            }
        }
        // move to next node
        infix fun moveTo(ch: Char): Node? = map[ch]
        // mark as end with Asterisk.
        fun markEnd() { if (map['*'] == null) map['*'] = Node() }
        // check is it end by Asterisk holding T/F
        fun isEnd(): Boolean = map['*'] != null
    }

    private val root = Node()

    fun insert(word: String) {
        var node = root
        word.forEach { ch -> 
            node += ch
        }
        node.markEnd()
    }

    fun search(word: String): Boolean {
        var node = root
        for (ch in word) {
            node = (node moveTo ch) ?: return false
        }
        return node.isEnd()
    }

    fun startsWith(prefix: String): Boolean {
        var node = root
        for (ch in prefix) {            
            node = (node moveTo ch) ?: return false
        }
        return true
    }

}

/**
 * Your Trie object will be instantiated and called as such:
 * var obj = Trie()
 * obj.insert(word)
 * var param_2 = obj.search(word)
 * var param_3 = obj.startsWith(prefix)
 */
```

---


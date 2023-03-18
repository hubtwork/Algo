## LeetCode Problems



#### 1472. Design Browser History

- **link**  [1472. Design Browser History](https://leetcode.com/problems/design-browser-history/)

- **lang**  `kotlin` 
- **tags**  `Design` `Double Linked-List`

```kotlin
class BrowserHistory(homepage: String) {
    // use double linked-list
    data class Page(
        val url: String
    ) {
        var prev: Page? = null
        var next: Page? = null
    }

    private var cursor = Page(homepage)

    fun visit(url: String) {
        val page = Page(url)
        page.prev = cursor
        cursor.next = page
        cursor = cursor.next!!
    }

    fun back(steps: Int): String {
        for(i in 0 until steps) {
            if (cursor.prev == null) break
            cursor = cursor.prev!!
        }
        return cursor.url
    }

    fun forward(steps: Int): String {
        for (i in 0 until steps) {
            if (cursor.next == null) break
            cursor = cursor.next!!
        }
        return cursor.url
    }
}

/**
 * Your BrowserHistory object will be instantiated and called as such:
 * var obj = BrowserHistory(homepage)
 * obj.visit(url)
 * var param_2 = obj.back(steps)
 * var param_3 = obj.forward(steps)
 */
```

---


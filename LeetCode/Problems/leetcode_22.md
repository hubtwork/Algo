## LeetCode Problems



#### 22. Generate Parentheses

- **link**  [22. Generate Parentheses](https://leetcode.com/problems/generate-parentheses/)

- **lang**  `kotlin` 
- **tags**  `String` `DP` `BackTracking`

```kotlin
class Solution {
    private val parentheses = mutableListOf<String>()
    fun generateParenthesis(n: Int): List<String> {
        backTracking(n, "", 0, 0)
        return parentheses
    }
    fun backTracking(n: Int, current: String, _open: Int, _close: Int) {
        // if catch answer
        if (current.length == n*2) {
            parentheses.add(current)   
            return
        }
        /*
            rules.
            - each time, open count must bigger than close count
            1) if open is lower than n, can go
            2) if close is lower than n, conditionally can go
                (close count must be lower than open count)
        */
        if (_open < n) backTracking(n, current + "(", _open+1, _close)
        if (_close < n && _open > _close) backTracking(n, current + ")", _open, _close+1)
        
    }
}
```

---


## LeetCode Problems



#### 125. Valid Palindrome

- **link**  [125. Valid Palindrome](https://leetcode.com/problems/valid-palindrome/description/)

- **lang**  `kotlin` 
- **tags**  `Two Pointers` `String` 

```kotlin
class Solution {
    fun isPalindrome(s: String): Boolean {
        // replace given string with regex following rule.
        val ss = s.replace("[^a-zA-Z0-9]".toRegex(), "").toLowerCase()
        // two-pointer check
        var left = 0
        var right = ss.length - 1
        while (left <= right) {
            if (ss[left++] != ss[right--]) return false
        }
        return true
    }
}
```

---


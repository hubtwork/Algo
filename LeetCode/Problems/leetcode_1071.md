## LeetCode Problems



#### 1071. Greatest Common Divisor of Strings

- **link**  [1071. Greatest Common Divisor of Strings](https://leetcode.com/problems/greatest-common-divisor-of-strings/)

- **lang**  `kotlin` 
- **tags**  `Math` `String`

```java
class Solution {
    fun gcdOfStrings(str1: String, str2: String): String {
        // make sure that str2 is shorter than str1
        if (str1.length < str2.length) return gcdOfStrings(str2, str1)
        // if short-string is empty, return 
        if (str2.isEmpty()) return str1
        // if long-string's prefix same length with str2 is not same with str2, return empty.
        if (str1.substring(0, str2.length) != str2) return ""
        // if correct, consume more if possible for get gcd
        return gcdOfStrings(str1.substring(str2.length), str2)
    }
}
```

---


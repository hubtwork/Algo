## LeetCode Problems



#### 263. Ugly Number

- **link**  [263. Ugly Number](https://leetcode.com/problems/ugly-number/)

- **lang**  `kotlin` 
- **tags**  `Math` 

```kotlin
class Solution {
    fun isUgly(n: Int): Boolean {
        var k = n
      	// real ugly problem... not a math.. :(
        while (k%5 == 0 && k > 0) k /= 5
        while (k%3 == 0 && k > 0) k /= 3
        while (k%2 == 0 && k > 0) k /= 2
        return k == 1
    }
}
```

---


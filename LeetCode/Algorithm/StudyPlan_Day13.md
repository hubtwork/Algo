## LeetCode Algorithm StudyPlan

<img src="../../assets/leetcode_study_day13.png" alt="leetcode_study_day13" style="zoom:50%;" />

### Day 12

- [231. Power of Two](https://leetcode.com/problems/power-of-two/?envType=study-plan&id=algorithm-i)
- [191. Number of 1 Bits](https://leetcode.com/problems/number-of-1-bits/?envType=study-plan&id=algorithm-i)

---

#### 231. Power of Two

- **lang**  `kotlin` 
- **tags**  `Math` `for loop` `BitManipulation` `Recursion` 

```kotlin
class Solution {
    fun isPowerOfTwo(n: Int): Boolean {
        // return loop(n)
        // return recursion(n)
        return bitwise(n)
    }
    // loop solution
    fun loop(n: Int): Boolean {
        if (n == 0) return false
        var k = n
        while (k % 2 == 0) k = k/2
        return if (k == 1) true else false
    }
    // recursion solution
    fun recursion(n: Int): Boolean {
        if (n == 0) return false
        if (n == 1) return true
        return if (n % 2 == 0) recursion(n/2) else return false
    }
    /*
        bitwise
        16: 10000
        15: 01111
        & : 00000
        so if n == 2^k, n and n - 1 == 0
    */
    fun bitwise(n: Int): Boolean {
        if (n == 0) return false
        return n > 0 && n.and(n-1) == 0
    }
}
```

---


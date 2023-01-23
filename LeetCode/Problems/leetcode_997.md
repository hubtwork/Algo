## LeetCode Problems



#### 997. Find the Town Judge

- **link**  [997. Find the Town Judge](https://leetcode.com/problems/find-the-town-judge/)

- **lang**  `kotlin` 
- **tags** `Array` `Hash Table` `Graph`

```kotlin
class Solution {
    fun findJudge(n: Int, trust: Array<IntArray>): Int {
        val trustedCount = IntArray(n)
        // iterate
        trust.forEach { tr -> 
            // to find trusted by all, but not trust anyone, just use in/decremental calculation
            trustedCount[tr[0] - 1] --
            trustedCount[tr[1] - 1] ++
        }
        // check is there person whom trusted by all, but not trust anyone.
        for (idx in 0 until trustedCount.size) {
            if (trustedCount[idx] == n-1) return idx + 1
        }
        return -1
    }
}
```

---


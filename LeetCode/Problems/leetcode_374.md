## LeetCode Problems



#### 374. Guess Number Higher or Lower

- **link**  [374. Guess Number Higher or Lower](https://leetcode.com/problems/guess-number-higher-or-lower/)

- **lang**  `kotlin` 
- **tags**  `Binary Search`  `Interactive`

```kotlin
/** 
 * The API guess is defined in the parent class.
 * @param  num   your guess
 * @return 	     -1 if num is higher than the picked number
 *			      1 if num is lower than the picked number
 *               otherwise return 0
 * fun guess(num:Int):Int {}
 */

class Solution:GuessGame() {
    override fun guessNumber(n:Int):Int {
        var min = 1
        var max = n
        // until find answer do binary search
        while (true) {
            val mid = min + (max-min)/2
            val result = guess(mid)
            if (result == 0) return mid
            else if (result == 1) min = mid + 1
            else if (result == -1) max = mid
        }
    }
}
```

---


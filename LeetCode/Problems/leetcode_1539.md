## LeetCode Problems



#### 1539. Kth Missing Positive Number

- **link**  [1539. Kth Missing Positive Number](https://leetcode.com/problems/kth-missing-positive-number/description/)

- **lang**  `kotlin` 
- **tags**  `Array` `Binary Search` 

```kotlin
class Solution {
    fun findKthPositive(arr: IntArray, k: Int): Int {
        var lowBound = 0
        var highBound = arr.size
        // binary search
        while (lowBound < highBound) {
            val mid = lowBound + (highBound - lowBound) / 2
            // we have to find num in phrase below
            // arr[mid] - (mid + 1) : passed missing-number count in current cursor
            if (arr[mid] - (mid + 1) < k) lowBound = mid + 1
            else highBound = mid
        }
        return lowBound + k
    }
}
```

---


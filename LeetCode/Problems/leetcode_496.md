## LeetCode Problems



#### 496. Next Greater Element I

- **link**  [496. Next Greater Element I](https://leetcode.com/problems/next-greater-element-i/description/)

- **lang**  `kotlin` 
- **tags** `Array` `Stack` `Monotonic Stack` `Hash Table`

```kotlin
class Solution {
    fun nextGreaterElement(nums1: IntArray, nums2: IntArray): IntArray {
        // hash map for O(1) find
        val map = mutableMapOf<Int, Int>()
        // use Monotonic Stack to find each element's first upper.
        val result = IntArray(nums1.size)
        val stack = Stack<Int>()
        stack.add(nums2.size-1)
        // iterate reverse-order
        for (i in nums2.size-2 downTo 0) {
            // pop all lower or sames in monotonic stack.
            // (to find first upper of current)
            while (stack.isNotEmpty() && nums2[stack.peek()] <= nums2[i]) stack.pop()
            // if stack is not empty, stack's peek is first greater position
            if (stack.isNotEmpty()) map[nums2[i]] = nums2[stack.peek()]
            stack.add(i)
        }
        // if hash map has key "num", result is value or -1 ( no next upper )
        nums1.forEachIndexed { idx, num -> result[idx] = map[num] ?: -1 }
        return result
    }
}
```

---


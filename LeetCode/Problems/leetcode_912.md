## LeetCode Problems



#### 912. Sort an Array

- **link**  [912. Sort an Array](https://leetcode.com/problems/sort-an-array/)

- **lang**  `kotlin` 
- **tags** `Array` `Quick Sort` `Divide and Conquer`

```kotlin
class Solution {
    fun sortArray(nums: IntArray): IntArray {
        if (nums.size == 1) return nums
        quickSort(nums, 0, nums.size - 1)
        return nums
    }
    fun quickSort(nums: IntArray, _start: Int, _end: Int) {
        if (_start >= _end) return
        // set mid pivot for quickSort
        var start = _start
        var end = _end
        var pivot = nums[start + (end - start) / 2]
        // iterate
        while (start <= end) {
            // find first elements which is incorrect index compare to pivot
            while (start <= end && nums[start] < pivot) start ++ 
            while (start <= end && nums[end] > pivot) end --
            // replace each element have to moved counterpart
            if (start <= end) {
                val temp = nums[end]
                nums[end --] = nums[start]
                nums[start ++] = temp
            }
        }
        // reduce each range, divide and conquer
        quickSort(nums, start, _end)
        quickSort(nums, _start, end)
    }
}
```

---


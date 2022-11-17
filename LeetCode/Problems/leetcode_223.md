## LeetCode Problems



#### 223. Rectangle Area

- **link**  [223. Rectangle Area](https://leetcode.com/problems/rectangle-area/)

- **lang**  `kotlin` 
- **tags**  `Math` `Geometry` 

```kotlin
class Solution {
    fun computeArea(ax1: Int, ay1: Int, ax2: Int, ay2: Int, bx1: Int, by1: Int, bx2: Int, by2: Int): Int {
        return (ay2-ay1) * (ax2-ax1) +
        (by2-by1) * (bx2-bx1) - 
        getOverlappedWidth(ax1, ay1, ax2, ay2, bx1, by1, bx2, by2)
    }
    /*
        think about overlapped width
        ax1 ----------- ax2
             bx1 ---- bx2
        overlap  ----
        -> min(ax2, bx2) - max(ax1, bx1)
        * but if no overlap, it'll be under 0. so return 0
    */
    fun getOverlappedWidth(ax1: Int, ay1: Int, ax2: Int, ay2: Int, bx1: Int, by1: Int, bx2: Int, by2: Int): Int {
        return Math.max(Math.min(ax2, bx2) - Math.max(ax1, bx1), 0) * Math.max(Math.min(ay2, by2) - Math.max(ay1, by1), 0)
    }
}
```

---


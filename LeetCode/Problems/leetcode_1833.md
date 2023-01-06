## LeetCode Problems



#### 1833. Maximum Ice Cream Bars

- **link**  [1833. Maximum Ice Cream Bars](https://leetcode.com/problems/maximum-ice-cream-bars/description/)

- **lang**  `kotlin` 
- **tags**  `Array` `Greedy` `Sorting`

```kotlin
class Solution {
    fun maxIceCream(costs: IntArray, coins: Int): Int {
        // total cost for each buy-process
        var totalCost = 0
        // sort and iterate with index
        costs.sort()
        costs.forEachIndexed { count, cost ->
            // buy-process and check total-purchase-amount.
            totalCost += cost
            // if over, can't buy this. or same, can buy this.
            if (totalCost > coins) return count
            if (totalCost == coins) return count + 1
        }
        // if not paused in iteration, can buy all.
        return costs.size
    }
}
```

---


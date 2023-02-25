## LeetCode Problems



#### 121. Best Time to Buy and Sell Stock

- **link**  [121. Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/)

- **lang**  `kotlin` 
- **tags**  `Array` `DP` 

```kotlin
import kotlin.math.max
class Solution {
    fun maxProfit(prices: IntArray): Int {
        /*
            Analysis.
            track from last to start.
            calculate best profit by checking max-selling-point and max-buying-point.
         */
        var maxi = prices.last()
        var maxProfit = 0
        // iterate
        for (i in prices.size - 2 downTo 0) {
            // record best selling point
            maxi = max(maxi, prices[i])
            // record best real-profit ( best selling - cheapest buying )
            maxProfit = max(maxProfit, maxi - prices[i])
        }
        return maxProfit
    }
}
```

---


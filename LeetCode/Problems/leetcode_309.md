## LeetCode Problems



#### 309. Best Time to Buy and Sell Stock with Cooldown

- **link**  [309. Best Time to Buy and Sell Stock with Cooldown](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/description/)

- **lang**  `kotlin` 
- **tags**  `Array` `DP`

```kotlin
import kotlin.math.max
class Solution {
    fun maxProfit(prices: IntArray): Int {
        // check max value of sell and cooldown
        var sell = 0
        var buy = -prices[0]
        var cooldown = 0
        var minBuy = buy
        var tmp = sell
        // iterate
        for (i in 1..prices.size-1) {
            // get each sell-buy pair and cooldowns for max profit.
            sell = minBuy + prices[i]
            buy = cooldown - prices[i]
            cooldown = max(cooldown, tmp)
            tmp = sell
            minBuy = max(minBuy, buy)
        }
        return max(sell, cooldown)
    }
}
```

---


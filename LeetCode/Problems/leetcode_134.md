## LeetCode Problems



#### 134. Gas Station

- **link**  [134. Gas Station](https://leetcode.com/problems/gas-station/description/)

- **lang**  `kotlin` 
- **tags**  `Array` `Greedy`

```kotlin
class Solution {
    /*
        Calculation Logic
        #1. Traverse from n-index clockWise to n-index.
        - calc: sum of all (gas_i - cost_i)
        #2. If "calc" positive, can traverse.
        #3. Start-point is must be first-all-positive-calc
     */
    fun canCompleteCircuit(gas: IntArray, cost: IntArray): Int {
        var startPoint = 0
        var calc = 0
        var tempCalc = 0
        for (i in 0 until gas.size) {
            val diff = gas[i] - cost[i]
            calc += diff
            tempCalc += diff
            // if running-diff is negative,
            // assign next index as start-point and reset running-diff.
            if (tempCalc < 0) {
                startPoint = i + 1
                tempCalc = 0
            }
        }
        return if (calc < 0) -1 else startPoint
    }
}
```

---


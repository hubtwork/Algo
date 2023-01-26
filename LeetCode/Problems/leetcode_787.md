## LeetCode Problems



#### 787. Cheapest Flights Within K Stops

- **link**  [787. Cheapest Flights Within K Stops](https://leetcode.com/problems/cheapest-flights-within-k-stops/)

- **lang**  `kotlin` 
- **tags** `DP` `DFS` `Dijkstra`

```kotlin
import kotlin.math.min
class Solution {
    data class Ticket(val destination: Int, val cost: Int)
    fun findCheapestPrice(n: Int, flights: Array<IntArray>, src: Int, dst: Int, k: Int): Int {
      	// build graph && dijkstra container
        val map = Array<MutableList<Ticket>>(n, { mutableListOf() })
        flights.forEach { (src, dst, cost) -> map[src].add(Ticket(dst, cost)) }
        val dp = IntArray(n, { Integer.MAX_VALUE })
        dp[src] = 0
        // bfs with queue
        val queue: Queue<Pair<Int, Int>> = LinkedList<Pair<Int, Int>>()
        queue.add(Pair(src, 0))
        var stops = 0
      	// traverse
        while (stops <= k && queue.isNotEmpty()) {
            for (i in 0 until queue.size) {
                val cursor = queue.poll()
                val city = cursor.first
                val cost = cursor.second
              	// mark one's best cost
                map[city].forEach { ticket ->
                    // if current is best-cost, continue traverse
                    if (cost + ticket.cost < dp[ticket.destination]) {
                        dp[ticket.destination] = cost + ticket.cost
                        queue.add(Pair(ticket.destination, dp[ticket.destination]))
                    }
                }
            }
            stops++
        }
        return if (dp[dst] == Integer.MAX_VALUE) -1 else dp[dst]
    }
}
```

---


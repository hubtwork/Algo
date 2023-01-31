## LeetCode Problems



#### 1626. Best Team With No Conflicts

- **link**  [1626. Best Team With No Conflicts](https://leetcode.com/problems/best-team-with-no-conflicts/)

- **lang**  `kotlin` 
- **tags**  `Array` `DP` `Sorting`

```kotlin
import kotlin.math.max
class Solution {
    data class Player(val age: Int, val score: Int): Comparable<Player> {
        // compare method for sorted with descending ( age -> score )
        override fun compareTo(other: Player): Int = 
            compareValuesBy(this, other, { - it.age }, { - it.score })
    }

    fun bestTeamScore(scores: IntArray, ages: IntArray): Int {
        val size = scores.size
        // build player list and sort.
        val players = mutableListOf<Player>()
        for (i in 0 until size) players.add(Player(ages[i], scores[i]))
        players.sort()
        // calculate dp
        var answer = 0
        val dp = IntArray(size)
        // iterate
        for (current in 0 until size) {
            val score = players[current].score
            dp[current] = score
            // consume candidates who has more score-possibilities
            for (before in 0 until current) {
                if (players[before].score >= score) {
                    dp[current] = max(dp[current], dp[before] + score)
                }
            }
            answer = max(answer, dp[current])
        }
        return answer
    }
}
```

---


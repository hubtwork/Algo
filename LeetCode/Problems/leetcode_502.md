## LeetCode Problems



#### 502. IPO

- **link**  [502. IPO](https://leetcode.com/problems/ipo/description/)

- **lang**  `kotlin` 
- **tags** `Array` `Greedy` `Sorting` `Heap ( Priority Queue )`

```kotlin
class Solution {
    data class Task(val profit: Int, val capital: Int) {
        companion object {
            val minCapitalComparator = Comparator<Task> { me, other -> me.capital - other.capital }
            val maxProfitComparator = Comparator<Task> { me, other -> other.profit - me.profit }
        }
    }

    fun findMaximizedCapital(k: Int, w: Int, profits: IntArray, capital: IntArray): Int {
        // minimum-capital-first PQ
        val capitalPQ = PriorityQueue<Task> (Task.minCapitalComparator)
        // maximum-profit-first PQ
        val profitPQ = PriorityQueue<Task> (Task.maxProfitComparator)
        // enroll capital-profit pairs
        for (i in 0 until profits.size) { capitalPQ.add(Task(profits[i], capital[i])) }
        // trace budgets.
        var budget = w
        for (i in 0 until k) {
            // move tasks possibly in budget.
            while (capitalPQ.isNotEmpty() && capitalPQ.peek().capital <= budget) profitPQ.add(capitalPQ.poll())
            // if no possible task, escape iteration.
            if (profitPQ.isEmpty()) break
            // add profit to budget with best task
            budget += profitPQ.poll().profit
        }
        return budget
    }
}
```

---


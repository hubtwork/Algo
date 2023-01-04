## LeetCode Problems



#### 2244. Minimum Rounds to Complete All Tasks

- **link**  [2244. Minimum Rounds to Complete All Tasks](https://leetcode.com/problems/minimum-rounds-to-complete-all-tasks/description/)

- **lang**  `kotlin` 
- **tags** `Array` `Hash Table` `Greedy` `Counting` 

```kotlin
class Solution {
    fun minimumRounds(tasks: IntArray): Int {
        tasks.sort()
        var count = 0
        var pointer = 0
        while (pointer < tasks.size) {
            // read all levels
            val level = tasks[pointer]
            var levelCount = 0
            // get task-count for current level
            while (pointer < tasks.size && tasks[pointer] == level) { 
                pointer++
                levelCount++
            }
            /*
                if count == 1, it's fail to execute.
                if count % 3 == 0, (count / 3) steps with 3 tasks.
                if count % 3 == 1, (count / 3 - 1) steps with 3 tasks + 2 steps with 2 tasks
                if count % 3 == 2, (count / 3 - 1) steps with 3 tasks + 1 step with 2 tasks
                ex -> 7 = 3 + 2 + 2, 8 = 3 + 3 + 2
             */
            if (levelCount == 1) return -1
            if (levelCount % 3 == 0) count += levelCount / 3
            else count += levelCount / 3 + 1
        }
        return count
    }
}
```

---


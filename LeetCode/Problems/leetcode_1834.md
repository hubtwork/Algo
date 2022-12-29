## LeetCode Problems



#### 1834. Single-Threaded CPU

- **link**  [1834. Single-Threaded CPU](https://leetcode.com/problems/single-threaded-cpu/)

- **lang**  `kotlin` 
- **tags**  `Array` `Sorting` `Heap(PQ)`

```kotlin
class Solution {
    data class Task(
        val id: Int,
        val enqueueTime: Int,
        val processingTime: Int
    )

    fun getOrder(tasks: Array<IntArray>): IntArray {
        // initialize variables
        var timer = Int.MAX_VALUE
        var orderCounter = 0
        val result = IntArray(tasks.size)
        // ALL TASK QUEUE has three conditions.
        // (1) enqueTime-fast, (2) processingTime-fast, (3) task-id
        val allTask = PriorityQueue<Task>(tasks.size, compareBy({ it.enqueueTime }, { it.processingTime }, { it.id } ))
        // AVAILABLE TASK QUEUE has two conditions.
        // (1) emit short-processingTime (2) emit lower id ( if equals processingTime )
        val availableTask = PriorityQueue<Task>(tasks.size, compareBy({ it.processingTime }, { it.id }))
        // enqueue all tasks to AVAILABLE TASK
        tasks.forEachIndexed { idx, task -> allTask.add(Task(idx, task[0], task[1])) }
        // iterate for all tasks.
        while (allTask.isNotEmpty() || availableTask.isNotEmpty()) {
            // next task will come from allTask or availableTask
            // but if no availables, timer will be fast-forwarded to enqueTime from all task.
            val nextTask = if (availableTask.isEmpty()) allTask.poll().also { timer = it.enqueueTime } else availableTask.poll()
            // mark order-result with next task's id.
            result[orderCounter++] = nextTask.id
            // FAST-FORWARD with processing task.
            timer += nextTask.processingTime
            // enqueue available tasks from ALL TASK.
            while (allTask.isNotEmpty() && allTask.peek().enqueueTime <= timer) {
                availableTask.add(allTask.poll())
            }
        }
        return result
    }
}
```

---


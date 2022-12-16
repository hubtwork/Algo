## LeetCode Problems



#### 232. Implement Queue using Stacks

- **link**  [263. Ugly Number](https://leetcode.com/problems/ugly-number/)

- **lang**  `kotlin` 
- **tags**  `Stack` `Design` `Queue` 

```kotlin
class MyQueue() {
    // implements queue using 2 stacks
    private val front = Stack<Int>()
    private val back = Stack<Int>()
    // front-forward, move all elements in back to front. and newly push.
    fun push(x: Int) {
        while (back.isNotEmpty()) front.push(back.pop())
        front.push(x)
    }
    // back-forward, move all elements in front to back. return pop() of back.
    fun pop(): Int {
        while (front.isNotEmpty()) back.push(front.pop())
        return back.pop()
    }
    // back-forward, move all elements in front to back. return peek() of back.
    fun peek(): Int {
        while (front.isNotEmpty()) back.push(front.pop())
        return back.peek()
    }
    // check are front and back stack all empty.
    fun empty(): Boolean = front.isEmpty() && back.isEmpty()
}
```

---


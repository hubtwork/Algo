## LeetCode Problems



#### 1114. Print in Order

- **link**  [1114. Print in Order](https://leetcode.com/problems/print-in-order/)

- **lang**  `java` 
- **tags**  `Concurrency`

```java
class Foo {

    // use each thread's semaphore for ensure executing order
    private Semaphore s1 = new Semaphore(1);
    private Semaphore s2 = new Semaphore(0);
    private Semaphore s3 = new Semaphore(0);
    
    public Foo() {
        
    }

    public void first(Runnable printFirst) throws InterruptedException {
        s1.acquire();
        // printFirst.run() outputs "first". Do not change or remove this line.
        printFirst.run();
        s2.release();
    }

    public void second(Runnable printSecond) throws InterruptedException {
        s2.acquire();
        // printSecond.run() outputs "second". Do not change or remove this line.
        printSecond.run();
        s3.release();
    }

    public void third(Runnable printThird) throws InterruptedException {
        s3.acquire();
        // printThird.run() outputs "third". Do not change or remove this line.
        printThird.run();
        s1.release();
    }
}
```

---


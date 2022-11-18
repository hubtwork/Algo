## LeetCode Problems



#### 433. Minimum Genetic Mutation

- **link**  [433. Minimum Genetic Mutation](https://leetcode.com/problems/minimum-genetic-mutation/)

- **lang**  `kotlin` 
- **tags** `HashTable` `String` `BFS`

```kotlin
class Solution {
    fun minMutation(startGene: String, endGene: String, bank: Array<String>): Int {
        return mutateReadable(startGene, endGene, bank)
    }
    
    fun mutateReadable(startGene: String, endGene: String, bank: Array<String>): Int {
        val geneBank: MutableSet<String> = bank.toMutableSet()
        var count = 0
        var geneList = listOf(startGene)
        // check all candidate each step count.
        while (geneList.isNotEmpty()) {
            count ++
            var tempList = mutableListOf<String>()
            // traverse rest geneBank for checking can mutate
            geneBank.toList().forEach { inBank ->
                run seek@ {
                    geneList.forEach { gene ->
                        // if current inBank gene can be mutated, remove from bank and attach candidate
                        if (gene canMutate inBank) {
                            // if endGene is found, return count
                            if (inBank == endGene) return count
                            geneBank.remove(inBank)
                            tempList.add(inBank)
                            return@seek
                        }
                    }
                }
            }
            geneList = tempList
        }
        return -1
    }
    
    // checking function is this gene can mutate
    infix fun String.canMutate(inBank: String): Boolean {
        var count = 0
        this.forEachIndexed { idx, c -> if (c != inBank[idx]) count++ }
        return count == 1
    }
    
    // less readable, but lower iteration / lower memory usage
    fun mutateIterate(startGene: String, endGene: String, bank: Array<String>): Int { 
        val genes = "ACGT"
        val geneBank: MutableSet<String> = bank.toMutableSet()
        var count = 0
        // using Queue
        var geneList: Queue<String> = LinkedList<String>().apply {
            add(startGene)
        }
        while (geneList.isNotEmpty()) {
            count++
            val len = geneList.size
            // iterate all current step's memebers
            for (currentMem in 0..len-1) {
                val target = geneList.poll().toCharArray()
                // check each character of target can be mutated
                for (i in 0..target.size-1) {
                    val gen = target.copyOf()
                    // check iterable genes
                    genes.forEach { k -> 
                        if (gen[i] != k) {
                            gen[i] = k
                            val genStr = String(gen)
                            // if simulated gene is in bank, process
                            if (geneBank.contains(genStr)) {
                                if (genStr == endGene) return count
                                geneBank.remove(genStr)
                                geneList.add(genStr)
                            }
                            
                        }
                    }
                }
            }
        }
        return -1   
    }
}
```

---


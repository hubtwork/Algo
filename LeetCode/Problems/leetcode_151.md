## LeetCode Problems

##### Memory Usage first prize

> I know there're many conditions when evaluating submission in leetcode, it's not a absolute evaluation.
>
> 100% was the first time in my life, so just attached it. XD

<img src="/Users/alenheo/Desktop/repo/algo/assets/leetcode_151_prize.png" alt="leetcode_study_day2" style="zoom:50%;" />

#### 151. Reverse Words in a String

- **link**  [151. Reverse Words in a String](https://leetcode.com/problems/reverse-words-in-a-string/)

- **lang**  `kotlin` 
- **tags**  `String` `Two Pointers` 

```kotlin
class Solution {
    fun reverseWords(s: String): String {
        var result = ""
        var cursor = s.length - 1
        // skip trailing continuous whitespace
        while (s[cursor] == ' ') cursor--
        // read string backward
        while (cursor >= 0) {
            var temp = cursor
            if (s[cursor] == ' ') {
                // if current character is whitespace
                // skip continuous whitespace
                while (temp >= 0 && s[temp] == ' ') temp--
                // add whitespace only 'in word', not leading
                if (temp != -1) result += ' '
            }
            else {
                // if current character is alphabet
                var tempStr = ""
                var count = 0
                // read word from backward
                while (temp >= 0 && s[temp] != ' ') tempStr = s[temp--] + tempStr
                result += tempStr
            }
            cursor = temp
        }
        return result
    }
}
```

---


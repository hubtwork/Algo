## LeetCode Problems



#### 175. Combine Two Tables

- **link**  [175. Combine Two Tables](https://leetcode.com/problems/combine-two-tables/)

- **lang**  `kotlin` 
- **tags**  `Database` 

```mysql
# Write your MySQL query statement below
select firstName, lastName, city, state from Person
left join Address on Person.personId = Address.personId
```

---


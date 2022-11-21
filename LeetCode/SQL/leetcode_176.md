## LeetCode Problems



#### 176. Second Highest Salary

- **link**  [176. Second Highest Salary](https://leetcode.com/problems/second-highest-salary/)

- **lang**  `mysql` 
- **tags**  `Database` 

```mysql
# Write your MySQL query statement below
# add ifnull function for show as 'null'
select ifnull((select distinct salary from Employee order by salary DESC limit 1 offset 1), null) as SecondHighestSalary
```

---


# 2884.Pandas Modify Columns - Easy

| Field | Detail |
|-------|--------|
| **Issue** | [#16 - 2884.Pandas Modify Columns - Easy](https://github.com/lance-terminal/challenges/issues/16) |
| **Author** | @lance-terminal |
| **Labels** | LeetCode |
| **Created** | 2026-02-08T04:42:26Z |
| **Closed** | 2026-02-08T15:49:04Z |

---

# [2884. Modify Columns](https://leetcode.com/problems/modify-columns/)

DataFrame `employees`
```SQL
+-------------+--------+
| Column Name | Type   |
+-------------+--------+
| name        | object |
| salary      | int    |
+-------------+--------+
```
A company intends to give its employees a pay rise.
Write a solution to modify the salary column by multiplying each salary by 2.
The result format is in the following example

Example 1:
Input:
DataFrame `employees`
```SQL
+---------+--------+
| name    | salary |
+---------+--------+
| Jack    | 19666  |
| Piper   | 74754  |
| Mia     | 62509  |
| Ulysses | 54866  |
+---------+--------+
```
Output:
```SQL
+---------+--------+
| name    | salary |
+---------+--------+
| Jack    | 39332  |
| Piper   | 149508 |
| Mia     | 125018 |
| Ulysses | 109732 |
+---------+--------+
```
Explanation:
Every salary has been doubled.




## Comments

---

**lance-terminal** — 2026-02-08T15:49:03Z

```python
import pandas as pd
def modifySalaryColumn(employees: pd.DataFrame) -> pd.DataFrame:
    employees['salary'] = employees['salary'] * 2
    return employees
```

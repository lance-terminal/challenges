# 2881.Pandas Create a New Column - Easy

| Field | Detail |
|-------|--------|
| **Issue** | [#13 - 2881.Pandas Create a New Column - Easy](https://github.com/lance-terminal/challenges/issues/13) |
| **Author** | @lance-terminal |
| **Labels** | LeetCode |
| **Created** | 2026-02-08T04:31:41Z |
| **Closed** | 2026-02-08T15:21:41Z |

---

# [2881. Create a New Column](https://leetcode.com/problems/create-a-new-column/)

DataFrame `employees`
```SQL
+-------------+--------+
| Column Name | Type.  |
+-------------+--------+
| name        | object |
| salary      | int.   |
+-------------+--------+
```
A company plans to provide its employees with a bonus.
Write a solution to create a new column name bonus that contains the doubled values of the salary column.
The result format is in the following example.

Example 1:
Input:
DataFrame employees
```SQL
+---------+--------+
| name    | salary |
+---------+--------+
| Piper   | 4548   |
| Grace   | 28150  |
| Georgia | 1103   |
| Willow  | 6593   |
| Finn    | 74576  |
| Thomas  | 24433  |
+---------+--------+
```
Output:
```SQL
+---------+--------+--------+
| name    | salary | bonus  |
+---------+--------+--------+
| Piper   | 4548   | 9096   |
| Grace   | 28150  | 56300  |
| Georgia | 1103   | 2206   |
| Willow  | 6593   | 13186  |
| Finn    | 74576  | 149152 |
| Thomas  | 24433  | 48866  |
+---------+--------+--------+
```
Explanation: 
A new column bonus is created by doubling the value in the column salary.

 


## Comments

---

**lance-terminal** — 2026-02-08T15:21:32Z

```python
import pandas as pd

def createBonusColumn(employees: pd.DataFrame) -> pd.DataFrame:
    employees['bonus'] = employees['salary'] * 2
    return employees

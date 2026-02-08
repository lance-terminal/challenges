# 2879.Pandas Display the First Three Rows - Easy

| Field | Detail |
|-------|--------|
| **Issue** | [#11 - 2879.Pandas Display the First Three Rows - Easy](https://github.com/lance-terminal/challenges/issues/11) |
| **Author** | @lance-terminal |
| **Labels** | LeetCode |
| **Created** | 2026-02-08T04:00:34Z |
| **Closed** | 2026-02-08T04:14:17Z |

---

# [2879. Display the First Three Rows](https://leetcode.com/problems/display-the-first-three-rows/)

DataFrame: `employees`
```SQL
+-------------+--------+
| Column Name | Type   |
+-------------+--------+
| employee_id | int    |
| name        | object |
| department  | object |
| salary      | int    |
+-------------+--------+
```
Write a solution to display the first 3 rows of this DataFrame.
Example 1:
Input:
DataFrame employees
```SQL
+-------------+-----------+-----------------------+--------+
| employee_id | name      | department            | salary |
+-------------+-----------+-----------------------+--------+
| 3           | Bob       | Operations            | 48675  |
| 90          | Alice     | Sales                 | 11096  |
| 9           | Tatiana   | Engineering           | 33805  |
| 60          | Annabelle | InformationTechnology | 37678  |
| 49          | Jonathan  | HumanResources        | 23793  |
| 43          | Khaled    | Administration        | 40454  |
+-------------+-----------+-----------------------+--------+
```
Output:
```SQL
+-------------+---------+-------------+--------+
| employee_id | name    | department  | salary |
+-------------+---------+-------------+--------+
| 3           | Bob     | Operations  | 48675  |
| 90          | Alice   | Sales       | 11096  |
| 9           | Tatiana | Engineering | 33805  |
+-------------+---------+-------------+--------+
```
Explanation: 
Only the first 3 rows are displayed.




## Comments

---

**lance-terminal** — 2026-02-08T04:02:19Z

```Python
import pandas as pd
def selectFirstRows(employees: pd.DataFrame) -> pd.DataFrame:
    return employees.head(3)
```
.head(10) .tail(10)

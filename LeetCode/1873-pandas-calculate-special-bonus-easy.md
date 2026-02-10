# 1873.Pandas Calculate Special Bonus - Easy

| Field | Detail |
|-------|--------|
| **Issue** | [#29 - 1873.Pandas Calculate Special Bonus - Easy](https://github.com/lance-terminal/challenges/issues/29) |
| **Author** | @lance-terminal |
| **Labels** | LeetCode |
| **Created** | 2026-02-10T02:14:59Z |
| **Closed** | 2026-02-10T02:40:57Z |

---

# [1873. Calculate Special Bonus](https://leetcode.com/problems/calculate-special-bonus/)

Table: `Employees`
```SQL
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| employee_id | int     |
| name        | varchar |
| salary      | int     |
+-------------+---------+
```
`employee_id` is the primary key (column with unique values) for this table.
Each row of this table indicates the employee ID, employee name, and salary.

Write a solution to calculate the bonus of each employee. The bonus of an employee is `100%` of their salary if the ID of the employee is an odd number and the employee's name does not start with the character `'M'`. The bonus of an employee is `0` otherwise.

Return the result table ordered by `employee_id`.
The result format is in the following example.

 

Example 1:

Input: 
Employees table:
```SQL
+-------------+---------+--------+
| employee_id | name    | salary |
+-------------+---------+--------+
| 2           | Meir    | 3000   |
| 3           | Michael | 3800   |
| 7           | Addilyn | 7400   |
| 8           | Juan    | 6100   |
| 9           | Kannon  | 7700   |
+-------------+---------+--------+
```
Output:
```SQL
+-------------+-------+
| employee_id | bonus |
+-------------+-------+
| 2           | 0     |
| 3           | 0     |
| 7           | 7400  |
| 8           | 0     |
| 9           | 7700  |
+-------------+-------+
```
Explanation: 
The employees with IDs 2 and 8 get 0 bonus because they have an even employee_id.
The employee with ID 3 gets 0 bonus because their name starts with 'M'.
The rest of the employees get a 100% bonus.




## Comments

---

**lance-terminal** — 2026-02-10T02:40:51Z

```Python
import pandas as pd

def calculate_special_bonus(employees: pd.DataFrame) -> pd.DataFrame:
    employees['bonus'] = employees.apply( # make a new column called bonus
        lambda x: x['salary'] if x['employee_id'] % 2 > 0 and not x['name'].startswith('M') # anonymous function using lambda. If emoloyee_id is odd number and names does not start with M report the salary into the new column
    else 0, # or else fill it with 0
        axis=1 # across the columns, down rows → row operations
    )

    df = employees[['employee_id', 'bonus']].sort_values('employee_id')
    return df
```

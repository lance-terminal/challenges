# 2880.Pandas Select Data - Easy

| Field | Detail |
|-------|--------|
| **Issue** | [#12 - 2880.Pandas Select Data - Easy](https://github.com/lance-terminal/challenges/issues/12) |
| **Author** | @lance-terminal |
| **Labels** | LeetCode |
| **Created** | 2026-02-08T04:09:37Z |
| **Closed** | 2026-02-08T15:19:30Z |

---

# [2880. Select Data](https://leetcode.com/problems/select-data/)

DataFrame `students`

```SQL
+-------------+--------+
| Column Name | Type   |
+-------------+--------+
| student_id  | int    |
| name        | object |
| age         | int    |
+-------------+--------+
```
Write a solution to select the name and age of the student with student_id = 101.
The result format is in the following example.

Example 1:
Input:
```SQL
+------------+---------+-----+
| student_id | name    | age |
+------------+---------+-----+
| 101        | Ulysses | 13  |
| 53         | William | 10  |
| 128        | Henry   | 6   |
| 3          | Henry   | 11  |
+------------+---------+-----+
```
Output:
```SQL
+---------+-----+
| name    | age | 
+---------+-----+
| Ulysses | 13  |
+---------+-----+
```
Explanation:
Student Ulysses has student_id = 101, we select the name and age.




## Comments

---

**lance-terminal** — 2026-02-08T15:19:22Z

```python
import pandas as pd
def selectData(students: pd.DataFrame) -> pd.DataFrame:
    return students.loc[students["student_id"] == 101, ["name", "age"]] 
```
`.loc` is an indexer
.loc[rows_condition, columns_list]
